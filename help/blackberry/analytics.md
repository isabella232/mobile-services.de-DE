---
description: Nachdem Sie die Bibliothek zu Ihrem Projekt hinzugefügt haben, können Sie beliebige Analytics-Methodenaufrufe an beliebigen Stellen in Ihrer App durchführen (stellen Sie sicher, dass Sie ADBMobile.h in Ihre Klasse importieren).
seo-description: Nachdem Sie die Bibliothek zu Ihrem Projekt hinzugefügt haben, können Sie beliebige Analytics-Methodenaufrufe an beliebigen Stellen in Ihrer App durchführen (stellen Sie sicher, dass Sie ADBMobile.h in Ihre Klasse importieren).
seo-title: Analytics
title: Analytics
uuid: de018eda-b37d-4afe-83a0-8011381d7aff
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 14%

---


# Analytics {#analytics}

Nachdem Sie die Bibliothek zu Ihrem Projekt hinzugefügt haben, können Sie beliebige Analytics-Methodenaufrufe an beliebigen Stellen in Ihrer App durchführen (stellen Sie sicher, dass Sie ADBMobile.h in Ihre Klasse importieren).

## Mobilanwendungsberichte in Analytics aktivieren {#task_3DA1354942CF4BF4B11B9CC97588A9ED}

Bevor Sie Code hinzufügen, lassen Sie Ihren Analytics-Administrator Folgendes ausführen, um die Lebenszyklusverfolgung für Mobilanwendungen zu aktivieren. Dadurch wird sichergestellt, dass Ihre Report Suite zu Beginn der Entwicklung Metriken erfassen kann.


1. Öffnen Sie **[!UICONTROL Admin Tools]** > **[!UICONTROL Report Suites]** und wählen Sie Ihre mobile(n) Report Suite(s) aus.
1. Klicken Sie auf Einstellungen **[!UICONTROL bearbeiten]** > **[!UICONTROL Mobilverwaltung]** > **[!UICONTROL Mobilanwendungs-Berichte]**.

   ![](assets/mobile-settings.png)

1. Klicken Sie auf Neueste App-Berichte **[!UICONTROL aktivieren]**.

   Optional können Sie auch auf **[!UICONTROL Verfolgung]** mobiler Standorte aktivieren und ältere Berichte und Zuordnung für Hintergrundtreffer **[!UICONTROL aktivieren]** klicken.

   ![](assets/enable-lifecycle.png)

Lebenszyklusmetriken können jetzt erfasst werden, und Mobilanwendungsberichte werden im Menü **[!UICONTROL Berichte]** in der Benutzeroberfläche der Marketing-Berichte angezeigt.

## Erfassen von Lebenszyklusmetriken {#task_25D469C62DF84573AEB5E8E950B96205}

1. Rufen Sie zum Erfassen von Lebenszyklusmetriken in Ihrer App `collectLifecycleData()` den `ApplicationUI` Konstruktor auf.

   Beispiel:

   ```java
   ApplicationUI::ApplicationUI(bb::cascades::Application *app): QObject(app) { 
   //... 
   ADBMobile::collectLifecycleData(); 
   } 
   ```

   Wenn die Anwendung in derselben Sitzung zweimal aufgerufen `collectLifecycleData()` wird, meldet sie bei jedem Aufruf nach dem ersten Absturz einen Absturz. Das SDK setzt beim Beenden der Anwendung ein Flag, das auf einen erfolgreichen Beenden hinweist. Wenn dieses Flag nicht gesetzt ist, `collectLifecyleData()` wird ein Absturz gemeldet.

## Events, Props und eVars {#concept_B885D5A71A5D45129CE7C1C3426A7D28}


Wenn Sie sich die [ADBMobile-Klassen- und Methodenreferenz](/help/blackberry/methods.md)angesehen haben, fragen Sie sich wahrscheinlich, wo Sie Ereignis, eVars, Props, Erben und Listen festlegen können. In Version 4 können Sie diese Variablentypen nicht mehr direkt in Ihrer App zuweisen. Stattdessen verwendet das SDK Kontextdaten und Verarbeitungsregeln, um Ihre App-Daten Analytics-Variablen für die Berichterstellung zuzuordnen.

Verarbeitungsregeln bieten mehrere Vorteile:

* Sie können Ihre Datenzuordnung ändern, ohne eine Aktualisierung an den Appstore zu senden.
* Sie können aussagekräftige Namen für Daten verwenden, anstatt Variablen festzulegen, die für eine Report Suite spezifisch sind.
* Das Senden zusätzlicher Daten hat geringe Auswirkungen. Diese Werte werden erst dann in Berichten angezeigt, wenn sie mithilfe von Verarbeitungsregeln zugeordnet werden.

Any values that you were assigning directly to variables should be added to the `data` HashMap instead.

## Verarbeitungsregeln {#concept_3EA4CD602AF4488A896B0EDD3BA2D969}

Verarbeitungsregeln werden verwendet, um die Daten, die Sie in Kontextdatenvariablen senden, zu Berichten in &quot;evars&quot;, &quot;props&quot;und andere Variablen zu kopieren.

[Processing Rules Training (Schulung zu den Verarbeitungsregeln)](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013

[Verarbeitungsregeln](https://docs.adobe.com/content/help/de-DE/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Autorisierung zur Verwendung der Verarbeitungsregeln erhalten](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Es wird empfohlen, Kontextdatenvariablen mithilfe von &quot;Namensräumen&quot;zu gruppieren, da dies eine logische Reihenfolge gewährleistet. Wenn Sie beispielsweise Informationen zu einem Produkt erfassen möchten, können Sie die folgenden Variablen definieren:

```js
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

Kontextdatenvariablen werden in der Benutzeroberfläche der Verarbeitungsregeln alphabetisch sortiert, sodass Namensraum schnell Variablen im selben Namensraum anzeigen können.

Außerdem haben wir gehört, dass einige von Ihnen Kontextdatenschlüssel mit der eVar- oder prop-Nummer benennen:

```js
"eVar1":"jimbo"
```

This might make it *slightly* easier when you perform the one time mapping in processing rules, but you lose readability during debugging and future code updates can be more difficult. Stattdessen empfehlen wir dringend, aussagekräftige Namen für Schlüssel und Werte zu verwenden:

```js
"username":"jimbo"
```

Kontextvariablen, die Zählervariablen definieren, können denselben Schlüssel und Wert haben:

```js
"logon":"logon"
```

Kontextdatenvariablen, die Inkrementor-Ereignis definieren, können das Ereignis als Schlüssel und den Inkrementierungswert als Wert haben:

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe behält sich den Namespace `a.` vor. Neben dieser kleinen Einschränkung müssen Kontextdatenvariablen in Ihrer Firma eindeutig sein, um Kollisionen zu vermeiden.

## Offline-Verfolgung aktivieren {#concept_402F4ECE240B4CA1B779322A7BFCB8DE}

Um Treffer zu speichern, wenn das Gerät offline ist, können Sie optional die Offline-Verfolgung in der `ADBMobileConfig.json` Datei aktivieren.

Achten Sie vor der Aktivierung der Offline-Verfolgung sehr genau auf die Zeitstempelanforderungen, die in der Konfigurationsdatei-Referenz beschrieben sind.

## Analytics-Methoden

Eine Liste der für BlackBerry verfügbaren Analytics-Methoden finden Sie unter *Analytics-Methoden* in der [Adobe Mobile Class and Method Reference](/help/blackberry/methods.md).