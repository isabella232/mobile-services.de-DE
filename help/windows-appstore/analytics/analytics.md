---
description: 'null'
seo-description: 'null'
seo-title: Analytics
solution: Experience Cloud,Analytics
title: Analytics
topic: Developer and implementation
uuid: fa0ef6c4-c04d-4695-9eb4-ada4e9920e6c
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 20%

---


# Analytics {#analytics}

Nachdem Sie die Bibliothek zum Projekt hinzugefügt haben, können Sie beliebige Analytics-Methodenaufrufe an beliebigen Stellen in Ihrer App durchführen.

>[!TIP]
>
>Stellen Sie sicher, dass Sie `ADBMobile.h` in Ihre Klasse importieren.

## Mobilanwendungsberichte in Analytics aktivieren {#section_F2F9234009184F20BA36B5CDE872B424}

Bevor Sie Code hinzufügen, lassen Sie Ihren Analytics-Administrator Folgendes ausführen, um die Lebenszyklusverfolgung für Mobilanwendungen zu aktivieren. Dadurch wird sichergestellt, dass Ihre Report Suite zu Beginn der Entwicklung Metriken erfassen kann.

1. Öffnen Sie **[!UICONTROL Admin Tools]** > **[!UICONTROL Report Suites]** und wählen Sie Ihre mobile(n) Report Suite(s) aus.
1. Klicken Sie auf Einstellungen **[!UICONTROL bearbeiten]** > **[!UICONTROL Mobilverwaltung]** > **[!UICONTROL Mobilanwendungs-Berichte]**.

   ![](assets/mobile-settings.png)

1. Klicken Sie auf Neueste App-Berichte **[!UICONTROL aktivieren]**.

   Optional können Sie auch auf **[!UICONTROL Verfolgung]** mobiler Standorte aktivieren und ältere Berichte und Zuordnung für Hintergrundtreffer **[!UICONTROL aktivieren]** klicken.

   ![](assets/enable-lifecycle.png)

Lebenszyklusmetriken können jetzt erfasst werden, und Mobilanwendungsberichte werden im Menü **[!UICONTROL Berichte]** in der Benutzeroberfläche der Marketing-Berichte angezeigt.


### Neue Versionen

In regelmäßigen Abständen werden neue Versionen von Mobile Application Berichte veröffentlicht. Neue Versionen werden nicht automatisch auf Ihre Report Suite angewendet. Wiederholen Sie diese Schritte, um die Aktualisierung durchzuführen. Jedes Mal, wenn Sie Ihrer App neue Experience Cloud-Funktionen hinzufügen, sollten Sie diese Schritte wiederholen, um sicherzustellen, dass Sie über die neueste Konfiguration verfügen.


## Lebenszyklusmetriken {#section_532702562A7A43809407C9A2CBA80E1E}

Um Lebenszyklusmetriken in Ihrer App zu erfassen, fügen Sie Aufrufe hinzu, wenn die Anwendung aktiviert wird, wie in den folgenden Beispielen gezeigt.


### WinJS in default.js


```js
app.onactivated = function (args) { 
  if (args.detail.kind === activation.ActivationKind.launch) { 
   ... 
   // launched and resumed stuff  
   ADBMobile.Config.collectLifecycleData(); 
  } 
}; 
app.oncheckpoint = function (args) { 
  ADBMobile.Config.pauseCollectingLifecycleData(); 
}
```

### C# in App.xaml.cs

```js
public App() 
{ 
    this.InitializeComponent(); 
    this.Resuming *= OnResuming; 
    this.Suspending *= OnSuspending; 
} 
protected override void OnLaunched(LaunchActivatedEventArgs e) 
{ 
    ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnResuming(object sender, object e) 
{ 
    ... 
    ADBMobile.Config.CollectLifecycleData(); 
    ... 
} 
private void OnSuspending(object sender, SuspendingEventArgs e) 
{ 
    ... 
    ADBMobile.Config.PauseCollectingLifecycleData(); 
    ... 
}
```

### C/CX in App.xaml.cpp

```js
App::App() 
{ 
 InitializeComponent(); 
 Resuming *= ref new EventHandler<Object ^>(this, &App::OnResuming); 
 Suspending *= ref new SuspendingEventHandler(this, &App::OnSuspending); 
} 
void App::OnResuming(Object ^sender, Object ^args) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
} 
void App::OnSuspending(Object^ sender, SuspendingEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::PauseCollectingLifecycleData(); 
 ... 
} 
void App::OnLaunched(Windows::ApplicationModel::Activation::LaunchActivatedEventArgs^ e) 
{ 
 ... 
 ADBMobile::Config::CollectLifecycleData(); 
 ... 
}
```

Wenn die Anwendung in derselben Sitzung zweimal aufgerufen `CollectLifecycleData()` wird, meldet sie bei jedem Aufruf nach dem ersten Absturz einen Absturz. Das SDK setzt beim Beenden der Anwendung ein Flag, das auf einen erfolgreichen Beenden hinweist. Wenn dieses Flag nicht gesetzt ist, `CollectLifecyleData()` wird ein Absturz gemeldet.


## Events, Props und eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}


Wenn Sie sich die [ADBMobile-Klassen- und Methodenreferenz](/help/windows-appstore/c-configuration/methods.md)angesehen haben, fragen Sie sich wahrscheinlich, wo Sie Ereignis, eVars, Props, Erben und Listen festlegen können. In Version 4 können Sie diese Variablentypen nicht mehr direkt in Ihrer App zuweisen. Stattdessen verwendet das SDK Kontextdaten und Verarbeitungsregeln, um Ihre App-Daten Analytics-Variablen für die Berichterstellung zuzuordnen.

Verarbeitungsregeln bieten mehrere Vorteile:

* Sie können Ihre Datenzuordnung ändern, ohne eine Aktualisierung an den Appstore zu senden.
* Sie können aussagekräftige Namen für Daten verwenden, anstatt Variablen festzulegen, die für eine Report Suite spezifisch sind.
* Das Senden zusätzlicher Daten hat geringe Auswirkungen. Diese Werte werden erst dann in Berichten angezeigt, wenn sie mithilfe von Verarbeitungsregeln zugeordnet werden.

Alle Werte, die Sie direkt Variablen zuweisen, sollten stattdessen den Kontextdaten hinzugefügt werden.


## Verarbeitungsregeln {#section_66EE762EEA5E4728864166201617DEBF}

Verarbeitungsregeln werden verwendet, um die Daten, die Sie in Kontextdatenvariablen senden, zu Berichten in &quot;evars&quot;, &quot;props&quot;und andere Variablen zu kopieren.

[Processing Rules Training (Schulung zu den Verarbeitungsregeln)](https://tv.adobe.com/embed/1181/16506/) @ Summit 2013

[Übersicht über Verarbeitungsregeln](https://docs.adobe.com/content/help/de-DE/analytics/admin/admin-tools/processing-rules/processing-rules.html)

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

Setzen Sie Kontextvariablen, die Zähler-Ereignis definieren, auf den Wert &quot;1&quot;:

```js
"logon":"1"
```

Kontextdatenvariablen, die inkrementierende Ereignis definieren, können den zu inkrementierenden Wert aufweisen:

```js
"levels completed":"6"
```

>[!NOTE]
>
>Adobe behält sich den Namespace `a.` vor. Neben dieser kleinen Einschränkung müssen Kontextdatenvariablen in Ihrer Firma eindeutig sein, um Kollisionen zu vermeiden.

## Variable „products“ {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Um *`products`* das mobile SDK festzulegen, müssen Sie eine spezielle Syntax verwenden. Siehe [Produktvariable](/help/windows-appstore/analytics/products/products.md).

## (Optional) Offline-Verfolgung aktivieren {#section_955B2A03EB854742BDFC4A0A3C287009}

Um Treffer zu speichern, wenn das Gerät offline ist, können Sie die Offline-Verfolgung in der [ADBMobileConfig.json-Konfiguration](/help/windows-appstore/c-configuration/methods.md)aktivieren. Bevor Sie die Offline-Verfolgung aktivieren, beachten Sie die Zeitstempelanforderungen, die in der Konfigurationsdatei-Referenz beschrieben sind.

## Geostandort und Zielpunkte {#section_BAD34A8DD013454DB355121316BD7FD4}

Mithilfe der geografischen Position können Sie Standortdaten (Breiten-/Längengrad) und vordefinierte Zielpunkte messen. Jeder `TrackLocation` Aufruf sendet:

* Breitengrad/Längengrad und POI (wenn innerhalb eines in der `ADBMobileConfig.json` Konfigurationsdatei definierten POI). Diese werden für den automatischen Berichte an mobile Lösungsvariablen übergeben.
* Entfernung von Zentrum und Genauigkeit als Kontextdaten weitergegeben. Erfassen Sie mithilfe einer Verarbeitungsregel.

So verfolgen Sie einen Ort:

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

Wenn der folgende POI in der `ADBMobileConfig.json` Konfigurationsdatei definiert ist:

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

Wenn die Geräteposition innerhalb eines Umkreises von 7000 Metern vom definierten Punkt bestimmt wird, wird eine `a.loc.poi` Kontextdatenvariable mit dem Wert &quot;San Francisco&quot;mit dem `TrackLocation` Treffer gesendet. An `a.loc.dist` context variable is sent with the distance in meters from the defined coordinates.

## Lifetime value {#section_D2C6971545BA4D639FBE07F13EF08895}

Mit dem Lebenszeitwert können Sie für jeden Benutzer einen Lebenszeitwert messen und vorgeben. Sobald Sie einen Wert mit `TrackLifetimeValueIncrease` senden, wird der Wert zum vorhandenen Wert hinzugefügt. Der Lebenszeitwert wird auf dem Gerät gespeichert und kann jederzeit mithilfe von `GetLifetimeValue` abgerufen werden. Dies kann verwendet werden, um Lebenszeiteinkäufe, Banneranzeigen, abgeschlossene Videos, Informationen zur Freigabe in sozialen Netzwerken, Fotouploads usw. zu speichern.

```js
// Lifetime Value Example 
var ADB = ADBMobile; 
var purchasePrice = 39.95; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ItemPurchaseEvent"] = "ItemPurchaseEvent"; 
cdata["PurchaseItem"] = "Item453"; 
cdata["PurchasePrice"] = purchasePrice; 
ADB.Analytics.trackLifetimeValueIncrease(purchasePrice, cdata);
```

## Zeitgesteuerte Aktionen {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

Mit zeitgesteuerten Aktionen können Sie die In-App-Zeit und die Gesamtzeit zwischen dem Beginn und dem Ende einer Aktion messen. Das SDK berechnet die Dauer der Sitzung und die Gesamtzeit (sitzungsübergreifend), die zum Abschluss der Aktion erforderlich ist. Auf diese Weise können Segmente definiert werden, die zeitlich mit dem Kauf verglichen werden sollen, Übermittlungsstufe, Kassengang usw.

* Gesamtanzahl der Sekunden in der App zwischen Start und Ende – sitzungsübergreifend
* Gesamtanzahl der Sekunden zwischen Start und Ende (Uhrzeit)

```js
// Timed Action Start Example 
var ADB = ADBMobile; 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["ExperienceName"] = experience; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
```

```js
// Timed Action Update Example 
var ADB = ADBMobile; 
var cdataUpdate = new Windows.Foundation.Collections.PropertySet(); 
cdataUpdate["ImageLiked"] = imageName; 
ADB.Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
```

```js
// Timed Action End Example 
var ADB = ADBMobile; 
ADB.Analytics.trackTimedActionEnd("TimeUntilPurchase");
```
