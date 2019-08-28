---
description: 'null'
seo-description: 'null'
seo-title: Analytics
solution: Marketing Cloud, Analytics
title: Analytics
topic: Entwickler und Implementierung
uuid: c 2 cef 3 d 3-77 a 7-4 a 8 e-bbe 4-3 db 10 a 77996 a
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics {#analytics}

Nachdem Sie die Bibliothek zum Projekt hinzugefügt haben, können Sie beliebige Analytics-Methodenaufrufe an beliebigen Stellen in Ihrer App vornehmen.

>[!TIP]
>
>Stellen Sie sicher, dass Sie in `ADBMobile.h` Ihre Klasse importiert werden.

## Enable mobile application reports in Analytics {#section_F2F9234009184F20BA36B5CDE872B424}

Bevor Sie Code hinzufügen, bitten Sie Ihren Analytics-Administrator, folgende Schritte auszuführen, um Mobile App-Lebenszyklus-Tracking zu ermöglichen. Dadurch wird sichergestellt, dass Ihre Report Suite zur Erfassung von Metriken bereit ist, wenn Sie die Entwicklung beginnen.

1. Open **[!UICONTROL Admin Tools]** &gt; **[!UICONTROL Report Suites]** and select your mobile report suite(s).

1. Click **[!UICONTROL Edit Settings]** &gt; **[!UICONTROL Mobile Management]** &gt; **[!UICONTROL Mobile Application Reporting]**.

   ![](assets/mobile-settings.png)

1. Klicken Sie auf **[!UICONTROL Neueste Anwendungsberichte aktivieren]**.

   Optionally, you can also click **[!UICONTROL Enable Mobile Location Tracking]** or **[!UICONTROL Enable Legacy Reporting and Attribution for background hits]**.

   ![](assets/enable-lifecycle.png)

Die Lebenszyklusmetriken können jetzt erfasst werden und im Menü Berichte in der Oberfläche für Marketingberichte werden **Mobilanwendungsberichte** angezeigt.

### Neue Versionen

Regelmäßig werden neue Versionen der Mobilanwendungs-Berichterstellung veröffentlicht. Neue Versionen werden nicht automatisch auf Ihre Report Suite angewendet. Sie müssen diese Schritte wiederholen, um die Aktualisierung durchzuführen. Jedes Mal, wenn Sie Ihrer Anwendung eine neue Experience Cloud-Funktion hinzufügen, wird empfohlen, diese Schritte zu wiederholen, um sicherzustellen, dass Sie über die neueste Konfiguration verfügen.

## Lifecycle metrics {#section_532702562A7A43809407C9A2CBA80E1E}

Um Lebenszyklusmetriken in Ihrer Anwendung zu erfassen, fügen Sie Aufrufe bei Aktivierung der Anwendung hinzu, wie in den folgenden Beispielen gezeigt.

### Winjs in default. js

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

### C # in App. xaml. cs

```js
public App() 
{ 
    this.InitializeComponent(); 
    this.Resuming += OnResuming; 
    this.Suspending += OnSuspending; 
} 
protected override void OnLaunched(LaunchActivatedEventArgs e) 
{   ... 
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

### C++/CX in App.xaml.cpp

```js
App::App() 
{ 
 InitializeComponent(); 
 Resuming += ref new EventHandler<Object ^>(this, &App::OnResuming); 
 Suspending += ref new SuspendingEventHandler(this, &App::OnSuspending); 
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

If `CollectLifecycleData()` is called twice in the same session, your application reports a crash on every call after the first. Das SDK setzt eine Markierung, wenn die Anwendung heruntergefahren wird, um eine erfolgreiche Beendigung anzugeben. If this flag is not set, `CollectLifecyleData()` reports a crash.

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

If you've looked at [SDK methods](/help/universal-windows/c-configuration/methods.md), you are probably wondering where to set events, eVars, props, heirs, and lists. In Version 4 können Sie diese Variablentypen nicht mehr direkt in Ihrer Anwendung zuweisen. Stattdessen nutzt das SDK Kontextdaten und Verarbeitungsregeln, um Ihre App-Daten zwecks Reporting Analytics-Variablen zuzuordnen.

Verarbeitungsregeln bieten mehrere Vorteile:

* Sie können Ihre Datenzuweisung ändern, ohne ein Update im App Store einzureichen.
* Sie können relevante Namen für Ihre Daten verwenden, anstatt Variablen festzulegen, die spezifisch für eine Report Suite sind.
* Es ist kaum Aufwand nötig, um zusätzliche Daten zu senden. Diese Werte werden erst dann in Berichten angezeigt, wenn sie mithilfe von Verarbeitungsregeln zugeordnet werden.

Alle Werte, die Sie Variablen direkt zugewiesen haben, müssen stattdessen Kontextdaten hinzugefügt werden.

## Verarbeitungsregeln {#section_66EE762EEA5E4728864166201617DEBF}

Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Eigenschaften und andere Variablen für Berichte zu kopieren.

[Training zu Verarbeitungsregeln](https://tv.adobe.com/embed/1181/16506/) beim Summit 2013

[Hilfe zu Verarbeitungsregeln](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

[Autorisierung zur Verwendung der Verarbeitungsregeln erhalten](https://helpx.adobe.com/analytics/kb/processing-rules-authorization.html)

Es ist empfehlenswert, die Kontextdatenvariablen mithilfe von „Namespaces“ zu gruppieren, um eine logische Ordnung beizubehalten. Wenn Sie beispielsweise Informationen zu einem Produkt erfassen möchten, können Sie die folgenden Variablen definieren:

```javascript
"product.type":"hat" 
"product.team":"mariners" 
"product.color":"blue"
```

Kontextdatenvariablen werden auf der Verarbeitungsregeloberfläche alphabetisch sortiert. Mit Namespaces können Sie schnell nachvollziehen, welche Variablen sich im selben Namespace befinden.

Wir haben außerdem erfahren, dass einige von Ihnen Kontextdatenschlüssel mithilfe der eVar- oder prop-Nummer benennen:

```js
"eVar1":"jimbo"
```

Dadurch wird es *etwas* einfacher, wenn Sie die einmalige Zuordnung in den Verarbeitungsregeln durchführen. Sie verlieren dadurch jedoch auch die Lesbarkeit während des Debuggings und künftiger Codeaktualisierungen, was wiederum komplizierter sein kann. Es wird stattdessen dringend empfohlen, dass Sie beschreibende Namen für Schlüssel und Werte verwenden:

```js
"username":"jimbo"
```

Legen Sie für Kontextvariablen, die Zählerereignisse definieren, den Wert „1“ fest:

```js
"logon":"1"
```

Kontextdatenvariablen, die Inkrementierungsereignisse definieren, können den Wert zum Inkrementieren enthalten:

```js
"levels completed":"6"
```

>[!TIP]
>
>Adobe behält sich den Namespace `a.`vor. Abgesehen von dieser Einschränkung müssen Kontextdatenvariablen in Ihrem Anmeldeunternehmen nur eindeutig sein, um Kollisionen zu vermeiden.

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

Sie müssen eine spezielle Syntax verwenden, um *`products`* im mobilen SDK festzulegen. Weitere Informationen finden Sie unter [products-Variable](/help/universal-windows/analytics/products.md).

## (Optional) Enable offline tracking {#section_955B2A03EB854742BDFC4A0A3C287009}

To store hits when the device is offline, you can enable offline tracking in the [SDK methods](/help/universal-windows/c-configuration/methods.md) file. Achten Sie auf die Zeitstempelanforderungen, die in der Konfigurationsdatei-Referenz beschrieben werden, bevor Sie Offline-Tracking aktivieren.

## Geo-location and points of interest {#section_BAD34A8DD013454DB355121316BD7FD4}

Standort ermöglicht Ihnen, Standortdaten (Breitengrad/Längengrad) und vordefinierte Zielpunkte zu messen. Each `TrackLocation` call sends:

* Breitengrad/Längengrad und Zielpunkt (wenn dieser unter die in der Konfigurationsdatei `ADBMobileConfig.json` definierten Zielpunkte fällt).

   Diese werden an die Variablen der mobilen Lösung zum automatischen Reporting weitergegeben.

* Entfernung vom Zentrum und Präzision in Form von Kontextdaten.

   Erfassen Sie diesen Wert mithilfe einer Verarbeitungsregel.

So verfolgen Sie einen Standort:

```js
var ADB = ADBMobile; 
ADB.Analytics.trackLocation(37.75345, -122.33207, null);
```

Wenn der folgende Zielpunkt in der Konfigurationsdatei `ADBMobileConfig.json` definiert ist:

```js
"poi" : [ 
            ["San Francisco",37.757144,-122.44812,7000], 
        ]
```

When the device location is determined to be within a 7000 meter radius of the defined point, an `a.loc.poi` context data variable with the value `San Francisco` is sent in with the `TrackLocation` hit. Eine `a.loc.dist`-Kontextvariable wird gesendet, die den Abstand von den definierten Koordinaten in Metern enthält.

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

## Timed actions {#section_7FF8B6A913A0460EAA4CAE835E32D8C1}

Mit zeitgesteuerten Aktionen können Sie die in der App verbrachte Zeit und die Gesamtzeit zwischen dem Anfang und dem Ende einer Aktion messen. Das SDK berechnet die Dauer in jeder Sitzung und die (sitzungsübergreifende) Gesamtzeit, die zum Abschluss einer Aktion benötigt wird. Damit können Segmente für den Vergleich der Zeit bis zum Kauf, Durchgänge und Checkoutfluss usw. verglichen werden.

* Sitzungsübergreifende Gesamtdauer in Sekunden in der App zwischen Start und Ende
* Gesamtdauer in Sekunden zwischen Start und Ende (Ist-Zeit)

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
