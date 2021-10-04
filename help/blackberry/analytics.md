---
description: Nachdem Sie die Bibliothek zu Ihrem Projekt hinzugefügt haben, können Sie beliebige Analytics-Methodenaufrufe an einer beliebigen Stelle in Ihrer App durchführen (stellen Sie sicher, dass Sie ADBMobile.h in Ihre Klasse importieren).
title: Analysen
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
exl-id: 4cd27e1a-e806-4dbb-84f5-63902ca2003f
source-git-commit: 1fa6111d6bf1c2d36f15d2f037718646a035435a
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 12%

---

# Analysen {#analytics}

Nachdem Sie die Bibliothek zu Ihrem Projekt hinzugefügt haben, können Sie beliebige Analytics-Methodenaufrufe an einer beliebigen Stelle in Ihrer App durchführen (stellen Sie sicher, dass Sie ADBMobile.h in Ihre Klasse importieren).

## Mobile-App-Berichte in Analytics aktivieren {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

Bevor Sie Code hinzufügen, bitten Sie Ihren Analytics-Administrator, Folgendes auszuführen, um das Lebenszyklus-Tracking für mobile Apps zu aktivieren. Diese Aktionen stellen sicher, dass Ihre Report Suite bereit ist, Metriken zu Beginn der Entwicklung zu erfassen.

1. Öffnen Sie **[!UICONTROL Admin Tools]** > **[!UICONTROL Report Suites]** und wählen Sie Ihre mobilen Report Suites aus.
1. Klicken Sie auf **[!UICONTROL Einstellungen bearbeiten]** > **[!UICONTROL Mobile Management]** > **[!UICONTROL Mobilanwendungs-Berichterstellung]**.

   ![Mobile Einstellungen](assets/mobile-settings.png)

1. Klicken Sie auf **[!UICONTROL Aktuelle App-Berichte aktivieren]**.

   Optional können Sie auch auf **[!UICONTROL Mobilstandortverfolgung aktivieren]** und **[!UICONTROL Ältere Berichterstellung und Zuordnung für Hintergrundtreffer aktivieren]** klicken.

   ![Lebenszyklus aktivieren](assets/enable-lifecycle.png)

Lebenszyklusmetriken können jetzt erfasst werden und Mobilanwendungsberichte werden im Menü **[!UICONTROL Berichte]** in der Benutzeroberfläche der Marketing-Berichte angezeigt.

## Lebenszyklusmetriken erfassen {#task_25D469C62DF84573AEB5E8E950B96205}

1. Rufen Sie `collectLifecycleData()` im Konstruktor `ApplicationUI` auf, um Lebenszyklusmetriken in Ihrer App zu erfassen.

   Beispiel:

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   Wenn `collectLifecycleData()` in derselben Sitzung zweimal aufgerufen wird, meldet Ihre Anwendung bei jedem Aufruf nach dem ersten einen Absturz. Das SDK legt eine Markierung fest, wenn die Anwendung heruntergefahren wird, die auf einen erfolgreichen Beenden hinweist. Wenn diese Markierung nicht gesetzt ist, meldet `collectLifecyleData()` einen Absturz.

## Events, Props und eVars {#concept_B885D5A71A5D45129CE7C1C3426A7D28}

Wenn Sie sich die [ADBMobile-Klassen- und Methodenreferenz](/help/blackberry/methods.md) angesehen haben, fragen Sie sich wahrscheinlich, wo Sie Ereignisse, eVars, Props, Erben und Listen festlegen können. In Version 4 können Sie diese Variablentypen nicht mehr direkt in Ihrer App zuweisen. Stattdessen verwendet das SDK Kontextdaten und Verarbeitungsregeln, um Ihre App-Daten Analytics-Variablen für die Berichterstellung zuzuordnen.

Verarbeitungsregeln bieten Ihnen verschiedene Vorteile:

* Sie können Ihre Datenzuordnung ändern, ohne eine Aktualisierung an den Appstore zu senden.
* Sie können aussagekräftige Namen für Daten verwenden, anstatt Variablen festzulegen, die für eine Report Suite spezifisch sind.
* Das Senden zusätzlicher Daten hat geringe Auswirkungen. Diese Werte werden erst dann in Berichten angezeigt, wenn sie mithilfe von Verarbeitungsregeln zugeordnet werden.

Alle Werte, die Sie Variablen direkt zugewiesen haben, sollten stattdessen der HashMap `data` hinzugefügt werden.

## Verarbeitungsregeln {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Props und andere Variablen für die Berichterstellung zu kopieren.

[Verarbeitungsregeln](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html)

Adobe empfiehlt die Gruppierung Ihrer Kontextdatenvariablen mithilfe von &quot;Namespaces&quot;, da dies Ihnen hilft, die logische Reihenfolge zu wahren. Wenn Sie beispielsweise Informationen zu einem Produkt erfassen möchten, können Sie die folgenden Variablen definieren:

```js
"product.type":"hat";
"product.team":"mariners";
"product.color":"blue";
```

Kontextdatenvariablen werden in der Benutzeroberfläche der Verarbeitungsregeln alphabetisch sortiert, sodass Sie mit Namespaces schnell Variablen sehen können, die sich im selben Namespace befinden.

Wir haben auch gehört, dass einige von Ihnen Kontextdatenschlüssel mithilfe der eVar- oder Prop-Nummer benennen:

```js
"eVar1":"jimbo";
```

Dies könnte *etwas* vereinfachen, wenn Sie die einmalige Zuordnung in Verarbeitungsregeln durchführen. Sie verlieren jedoch Lesbarkeit während des Debuggens und künftiger Code-Aktualisierungen. Stattdessen empfehlen wir dringend die Verwendung beschreibender Namen für Schlüssel und Werte:

```js
"username":"jimbo";
```

Kontextvariablen, die Zählerereignisse definieren, können denselben Schlüssel und denselben Wert haben:

```js
"logon":"logon";
```

Kontextdatenvariablen, die Inkrementierungsereignisse definieren, können das Ereignis als Schlüssel und den zu inkrementierenden Betrag als Wert haben:

```js
"levels completed":"6";
```

>[!TIP]
>
>Adobe behält sich den Namespace `a.` vor. Abgesehen von dieser kleinen Einschränkung müssen Kontextdatenvariablen nur in Ihrem Anmeldeunternehmen eindeutig sein, um Konflikte zu vermeiden.

## Offline-Tracking aktivieren {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

Um Treffer zu speichern, wenn das Gerät offline ist, können Sie optional die Offline-Verfolgung in der Datei `ADBMobileConfig.json` aktivieren.

Achten Sie besonders auf die Zeitstempelanforderungen, die in der Referenz zur Konfigurationsdatei beschrieben sind, bevor Sie die Offline-Verfolgung aktivieren.

## Analytics-Methoden

Eine Liste der für BlackBerry verfügbaren Analytics-Methoden finden Sie unter *Analytics-Methoden* in [Adobe Mobile Class and Method Reference](/help/blackberry/methods.md).
