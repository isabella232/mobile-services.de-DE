---
description: Sie können iOS PhoneGap-Plug-in-Methoden verwenden, um eine Reihe verschiedener Aufgaben auszuführen.
keywords: android; library; mobile; sdk
seo-description: Sie können iOS PhoneGap-Plug-in-Methoden verwenden, um eine Reihe verschiedener Aufgaben auszuführen.
seo-title: Phonegap-Plug-in-Methoden
solution: Marketing Cloud, Analytics
title: Phonegap-Plug-in-Methoden
topic: Entwickler und Implementierung
uuid: bc 3 db 9 ce -81 b 7-45 ec -88 aa -6020 c 1 db 5 d 9 c
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# PhoneGap plug-in methods{#phonegap-plug-in-methods}

Sie können PhoneGap-Plug-in-Methoden in Android zum Durchführen einer Vielzahl von Aufgaben verwenden.

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```js
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Configuration methods {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   Gibt den Datenschutzstatus für den aktuellen Benutzer zurück.

   Folgende Status stehen zur Verfügung:

   * `ADB.optedIn`: Diese Treffer werden sofort gesendet.
   * `ADB.optedOut`: Diese Treffer werden verworfen.
   * `ADB.optUnknown`: **Wenn Ihre Report Suite** zeitstempelfähig ist, werden Treffer gespeichert, bis sich der Datenschutzstatus an die Teilnahme (Treffer werden gesendet) oder das Opt-Out ändert (Treffer werden verworfen). Wenn für Ihre Report Suite **keine** Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

      Der Standardwert wird in der Datei `ADBMobileConfig.json` festgelegt.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      getPrivacyStatus(function (value) { myTempVal = value; }, function () {myTempVal = null;}); 
      ```

* **setPrivacyStatus**

   Legt für den aktuellen Benutzer den Datenschutzstatus `status` fest.

   Sie können einen der folgenden Status festlegen:

   * `ADB.optedIn`: Diese Treffer werden sofort gesendet.
   * `ADB.optedOut`: Diese Treffer werden verworfen.
   * `ADB.optUnknown`: **Wenn Ihre Report Suite** zeitstempelfähig ist, werden Treffer gespeichert, bis sich der Datenschutzstatus an die Teilnahme (Treffer werden gesendet) oder das Opt-Out ändert (Treffer werden verworfen). Wenn für Ihre Report Suite **keine** Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.setPrivacyStatus('ADB.optedIn');
      ```

* **getLifetimeValue**

   Gibt den Lebenszeitwert für den aktuellen Benutzer zurück. Der Standardwert lautet 0.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.getLifetimeValue(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

* **setDebugLogging**

   Enables (`true`) or disables (`false`) viewing debug information. Für die Variable ist standardmäßig `false` festgelegt.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   Ruft die Bibliotheksversion ab.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.getVersion(function (value) { versionNum = value }, function () { versionNum = 1.0;});
      ```

* **trackingIdentifier**

   Gibt die automatisch generierte Besucher-ID zurück.

   Diese App-spezifische, Unique Visitor-ID wird beim ersten App-Start generiert, gespeichert und dann fortlaufend weiterverwendet. Diese ID wird auch bei App-Upgrades beibehalten und nur entfernt, wenn die App deinstalliert wird.

   >[!TIP]
   >
   >Wenn Ihre App-Upgrades vom Experience Cloud 3. x auf 4. x-SDK aktualisiert werden, wird die vorherige Besucher-ID (benutzerdefiniert oder automatisch generiert) abgerufen und als benutzerdefinierte Benutzer-ID gespeichert. Weitere Informationen finden Sie unten unter `getUserIdentifier`. Diese ID bewahrt Besucherdaten bei SDK-Upgrades auf.

   Für neue Installationen für das SDK der Version 4.x lautet die Benutzer-ID `null` und die Tracking-ID wird verwendet.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.trackingIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

* **getUserIdentifier**

   Wenn eine Kunden-ID festgelegt wurde, wird diese ID zurückgesendet. Wenn keine ID festgelegt wurde, wird `null` zurückgesendet. Der Standardwert lautet `null`.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      getUserIdentifier(function(value) { myTempVal = value; }, function () { myTempVal = null; });
      ```

* **setUserIdentifier**

   Legt die Benutzerkennung auf `identifier` fest.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   Legt das Geräte-Token für Push-Benachrichtigungen fest.

   ```java
   getUserIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; });
   ```

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.setPushIdentifier(pushIdentifier, success, fail);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.setPushIdentifier('test_push_identifier',function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **keepLifecycleSessionAlive**

   Legt den Keepalive-Wert der Lebenszyklussitzung fest.

   >[!IMPORTANT]
   >
   >Calling `keepLifecycleSessionAlive` prevents your app from launching a new session the next time it is resumed from background. Sie sollten diese Methode nur verwenden, wenn Ihre App für Benachrichtigungen im Hintergrund registriert ist.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.keepLifecycleSessionAlive(); 
      ```

* **trackingSendQueuedHits**

   Zwingt die Bibliothek, alle Treffer in der Warteschlange unabhängig von aktuellen Batch-Optionen zu senden.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   Ruft die Anzahl der in der Offline-Warteschlange gespeicherten Verfolgungsaufrufe ab oder legt diese fest.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.trackingGetQueueSize(function (value) { myTempVal = value;}, function () { myTempVal = null;}); 
      ```

* **trackingClearQueue**

   Entfernt sämtliche in der Offline-Warteschlange gespeicherten Verfolgungsaufrufe.

   >[!WARNING]
   >
   >Gehen Sie beim manuellen Leeren der Warteschlange vorsichtig vor, da sie nicht rückgängig gemacht werden kann.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.trackingClearQueue(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

## PII methods {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   Sendet eine Anfrage zur Erfassung personenbezogener Daten.

   * Hier finden Sie die Syntax für diese Methode:

   ```javascript
   ADB.collectPII(piiData,success, fail);
   ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success') },function (value) { alert('fail') ;});
      ```


## Tracking methods {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   Verfolgt einen Adobe-Deep-Link-Clickthrough.

   >[!TIP]
   >
   >Wenn der Lebenszyklusaufruf ein Startereignis ist, werden die Adobe Link-Daten angehängt. Andernfalls wird ein zusätzlicher Aufruf gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```js
      ADB.trackAdobeDeepLink(deeplinkURL, success, fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function (value) { alert('success'); },function (value) { alert('fail') }); 
      ```

* **trackState**

   Verfolgt einen App-Status mit optionalen Kontextdaten. States are the views that are available in your app, such as such as `home dashboard`, `app settings`, `cart`, and so on. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `trackState`-Aufrufe inkrementieren die Seitenansichten.

   `cData`: JSON-Objekt mit Schlüsselwertpaaren, die in den Kontextdaten gesendet werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```js
      ADB.trackState(string stateName[,JSON cData]);
      ```

   * Hier finden Sie Codebeispiele für diese Methode:

      ```js
        ADB.trackState("login&amp;nbsp;page"); 
      ```

      ```js
        ADB.trackState("login page", {"user":"john","remember":"true"});
      ```

* **trackAction**

   Verfolgt eine Aktion in der App. Actions include `logins`, `banner taps`, `feed subscriptions`, and other metrics that occur in your app and that you want to measure.

   * Hier finden Sie die Syntax für diese Methode:

      ```js
      ADB.trackAction(string action[,JSON cData]); 
      ```

   * Hier finden Sie die Codebeispiele für diese Methode:

      ```js
        ADB.trackAction("login");
      ```

      ```js
        ADB.trackAction("login", {"user":"john","remember":"true"}); 
      ```

* **trackLocation**

   Sendet die aktuellen XY-Koordinaten. Ermittelt außerdem anhand der in der Datei `ADBMobileConfig.json` definierten Zielpunkte (POI), ob der als Parameter angegebene Standort in einem vorhandenen Zielpunkt liegt. Falls die aktuellen Koordinaten auf einen definierten POI passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem `trackLocation`-Aufruf gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.trackLocation(x, y[,JSON cData]); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.trackLocation('40.431596', '-111.893713'); 
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Erhöht den Lebenszeitwert des Benutzers um `amount`.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSON cData]); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.trackLifetimeValueIncrease('10.01'); 
      ```

* **trackTimed&#x200B;ActionStart**

   Start a timed action with the name `action`.

   Wenn Sie diese Methode für eine bereits gestartete Methode aufrufen, wird die vorherige zeitgesteuerte Aktion überschrieben.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.trackTimedActionStart(action[,JSON cData]);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   Pass in `cData` to update the context data that is associated with the `action`&gt;.

   The `cData` that is passed is appended to the existing data for the action and, if the same key is already defined for `action`, overwrites the data.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.trackTimedActionUpdate(String action[,JSON cData]);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.trackTimedActionUpdate("cartToCheckout",{'SampleContextDataKey3':'SampleContextDataVal3','SampleContextDataKey4':'SampleContextDataVal4'});
      ```

* **trackTimed&#x200B;ActionEnd**

   Beendet eine zeitgesteuerte Aktion.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.trackTimedActionEnd("cartToCheckout"); 
      ```

* **trackingTimedActionExists**

   Gibt zurück, ob derzeit eine zeitgesteuerte Aktion ausgeführt wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.trackingTimedActionExists(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

## Beacon methods {#section_F9500D6BD95348E08E283C02B657019D}

* **trackBeacon**

   Verfolgt das Eintreten eines Benutzers in den Radius eines Beacons.

   * Hier finden Sie die Syntax für diese Methode:

      ```js
      ADB.trackBeacon(uuid, major, minor, proximity, cData) 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.trackBeacon('2F234454-CF6D-4A0F-ADF2-F4911BA9FFA6', 1, 2, 
      ADB.beaconUnknown, {'hp':'hp_val','hp.company':'adobe'}
      ```

* **clearCurrentBeacon**

   Löscht die Beacon-Daten, sobald der Benutzer den Radius des Beacons verlässt.

   * Hier finden Sie die Syntax für diese Methode:

      ```js
      ADB.clearCurrentBeacon(success, fail)
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.clearCurrentBeacon(); 
      ```

## Target-Methoden {#section_8670140C5A3F455E887830AFFDF91D59}

* **targetLoadRequest**

   Sendet eine Anfrage an Ihren konfigurierten `Target`-Server und gibt den Zeichenfolgenwert des Angebots zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.targetLoadRequest(success, fail, name, defaultContent, parameters);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.targetLoadRequest(function&nbsp;(value)
      {myTempVal = value }, function () { myTempVal = null;},'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   Sendet eine Anfrage an Ihren konfigurierten `Target`-Server.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.targetLoadOrderConfirmRequest(success, fail name orderId, orderTotal, productPurchaseId, parameters); 
      ```

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.targetLoadRequest(function (value) { myTempVal = value }
      , function ()
      { myTempVal = null; } 
      , 'name' 'orderId' 'total', 'purchaseId',
      {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   Löscht die `Target`-Cookies aus dem gemeinsamen Cookie-Speicher.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.targetClearCookies(); 
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Processes a `Target` service request.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(
        success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters requestLocationParameters
        ); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters  (function () { alert('success'); }, function () { alert('fail'); }, ;'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}, {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'});
      ```

* **targetLoadRequestWithName**

   Processes a `Target` service request.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.targetLoadRequestWithRequestName(success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.targetLoadRequestWithName(
      function (value){ // handle target success} ,
      function() { // handle target failure }, 
      "mboxName",
      "defaultContent",
      {"profileParameters":"profileParametervalues"}
      {"orderId" : "32FGJ4XK" , "orderTotal" : "123.33" , "purchasedProductIds":"[46,34]" }
      {"mboxParameters":"mboxParametersvalues"}
      );
      ```

* **targetSessionID**

   Ruft den Wert des Cookies `SessionID` ab, das für diesen Besucher vom Target-Server zurückgegeben wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.targetSessionID (success, fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.targetSessionID(function (value) { alert(value) },function (value){ alert('fail'); });  
      ```

* **targetPcID**

   Ruft den Wert des Cookies `PcID` ab, das für diesen Besucher vom `Target`-Server zurückgegeben wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.targetPcID (success, fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.targetPcID(function  (value) { alert(value) },function (value) { alert('fail'); });
      ```

* **targetSetThirdPartyID**

   Legt die benutzerdefinierte Besucher-ID für Target fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID, success, fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id' function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **targetThirdPartyID**

   Ruft die benutzerdefinierte Besucher-ID für Target ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.targetThirdPartyID(success, fail);
      ```

   * Hier finden Sie Codebeispiele für diese Methode:

      ```java
       ADB.targetThirdPartyID(function (value) { alert(value); },function (value) { alert('fail')__;});
      ```

## Acquisition methods {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   Sendet eine Anfrage an Ihren konfigurierten Target-Server und gibt den Zeichenfolgenwert des Angebots zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.acquisitionCampaignStartForApp(appId, data, success, fail); 
      ```

   * Hier finden Sie die Codebeispiele für diese Methode:

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’});  
      ```

## Advertising identifier {#section_194607D101B047A19C51B19E176E1500}

In the main activity that is generated by Cordova, call `Config.submitAdvertisingIdentifierTask()` in the `onResume()` method. Weitere Informationen finden Sie unter [Konfigurationsmethoden](/help/android/configuration/methods.md).

## Audience Manager methods {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   Ruft das Besucherprofil ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.audienceGetVisitorProfile(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.audienceGetVisitorProfile(function(value) { profile = value;}, function() { profile = null; }); 
      ```

* **audienceGetDpuuid**

   Gibt die DPUUID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.audienceGetDpuuid(success fail);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.audienceGetDpuuid(function(value) { dpuuid = value;}, function(){dpuuid = null; }); 
      ```

* **audienceGetDpid**

   Gibt die DPID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.audienceGetDpid(success, fail);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;}, function() {dpid =  null;}); 
      ```

* **audienceSetDpidAndDpuuid** 

   Legt die DPID und die DPUUID fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid, dpuuid, success, fail); 
      ```

   * Hier finden Sie die Codebeispiele für diese Methode:

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’, function() {…}, function(){…};
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’); 
      ```

* **audienceSignalWithData**

   Verarbeitet eine Audience Manager-Dienstanforderung.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.audienceSignalWithData(success, fail, data);
      ```

   * Hier finden Sie die Codebeispiele für diese Methode:

      ```java
       ADB.audienceSignalWithData(function() {}, function() {} {‘key1’: ’value1’ ‘key2’: ‘value2’}); 
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’: ’value1’, ‘key2’:‘value2’}); 
      ```

* **audienceReset**

   Die UUID des Audience Manager bereinigt das aktuelle Besucherprofil.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.audienceReset();
      ```

## ID Service methods {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   Gibt die Experience Cloud ID vom ID-Dienst zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.visitorGetMarketingCloudId(success, fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.visitorGetMarketingCloudId(function (value) { mcid = value;},function (){ mcid = null;});
      ```

* **visitorSyncIdentifiers**

   Synchronisiert die angegebenen Kennungen mit dem ID-Dienst.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.visitorSyncIdentifiers(identifiers, success, fail); 
      ```

   * Hier finden Sie die Codebeispiele für diese Methode:

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’: ‘value_id_1’});  
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   Synchronisiert die bereitgestellten Kennungen mit dem ID-Dienst.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState
      (identifiers, authenticationState, success, fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'}, ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **visitorSyncIdentifierWithType**

   Synchronisiert die angegebene Kennung mit dem ID-Dienst.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType, identifier authenticationState, success, fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type', 'test-identifier', ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success') },function (value) { alert('fail'); }); 
      ```

* **visitorAppendToURL**

   Hängt die Besucherkennungen an die angegebene URL an.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
       ADB.visitorAppendToURL(urlToAppend, success, fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.visitorAppendToURL('test_visitor_url', function (value) alert(value);},'');
      ```

* **visitorGetIDs**

   Returns all `visitorID`s that have been synced.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.visitorGetIDs (success, fail);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.visitorGetIDs(function (value) { alert(value); },function (value) { alert('fail') ;}); 
      ```
