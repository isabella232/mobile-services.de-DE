---
description: Sie können iOS PhoneGap-Plug-in-Methoden verwenden, um eine Reihe verschiedener Aufgaben auszuführen.
keywords: phonegap
seo-description: Sie können iOS PhoneGap-Plug-in-Methoden verwenden, um eine Reihe verschiedener Aufgaben auszuführen.
seo-title: PhoneGap-Plug-in-Methoden
solution: Experience Cloud,Analytics
title: PhoneGap-Plug-in-Methoden
topic-fix: Developer and implementation
uuid: bd830fe5-804a-4d0a-bbb6-99a6d8da6a03
exl-id: 7ffdf008-1605-471f-93fb-f9c6b38a3bcb
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '1731'
ht-degree: 100%

---

# PhoneGap-Plug-in-Methoden {#phonegap-plug-in-methods}

Sie können iOS PhoneGap-Plug-in-Methoden verwenden, um eine Reihe verschiedener Aufgaben auszuführen.

Fügen Sie in `html`-Dateien, in denen Sie die Verfolgung nutzen möchten, das Tag `<head>` ein:

```html
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Konfigurationsmethoden {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   Gibt den Datenschutzstatus für den aktuellen Benutzer zurück. Folgende Status stehen zur Verfügung:

   * `ADB.optedIn`: Treffer werden umgehend gesendet.
   * `ADB.optedOut`: Treffer werden verworfen.
   * `ADB.optUnknown`Wenn für Ihre Report Suite Zeitstempel aktiviert **sind**, werden Treffer so lange gespeichert, bis der Datenschutzstatus in „opt-in“ (Treffer werden gesendet) oder „opt-out“ (Treffer werden verworfen) geändert wird. Wenn für Ihre Report Suite **keine** Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.\
      Der Standardwert wird in der Datei `ADBMobileConfig.json` festgelegt.

      * Hier finden Sie ein Code-Beispiel für diese Methode:

         ```javascript
         getPrivacyStatus(function (value){myTempVal = value;},function(){myTempVal = null;});
         ```

* **setPrivacyStatus**

   Legt für den aktuellen Benutzer den Datenschutzstatus `status` fest. Sie können einen der folgenden Status festlegen:
   * `ADB.optedIn`: Treffer werden umgehend gesendet.
   * `ADB.optedOut`: Treffer werden verworfen.
   * `ADB.optUnknown`: Wenn für Ihre Report Suite Zeitstempel aktiviert **sind**, werden Treffer gespeichert, bis sich der Datenschutzstatus zu „optedin“ (Treffer werden gesendet) oder „optedout“ (Treffer werden verworfen) ändert.

      Wenn für Ihre Report Suite **keine** Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
        ADB.setPrivacyStatus('ADB.optedIn'); 
      ```

* **getLifetimeValue**

   Gibt den Lebenszeitwert für den aktuellen Benutzer zurück. Der Standardwert lautet 0.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.getLifetimeValue(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```

* **setDebugLogging**

   Aktiviert (`true`) oder deaktiviert (`false`) die Anzeige von Debugging-Informationen. Für die Variable ist standardmäßig `false` festgelegt.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   Ruft die Bibliotheksversion ab.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.getVersion(function(value){versionNum = value;},function(){versionNum=1.0;}); 
      ```

* **trackingIdentifier**

   Gibt die automatisch generierte Besucher-ID zurück. Hierbei handelt es sich um eine App-spezifische Unique-Visitor-ID, die beim ersten Start der App generiert und ab diesem Zeitpunkt gespeichert und verwendet wird. Diese ID bleibt zwischen App-Upgrades erhalten und wird entfernt, wenn die App deinstalliert wird.

   >[!TIP]
   >
   >Wenn für Ihre App ein Upgrade vom Experience Cloud-SDK 3.x auf 4.x vorgenommen wird, wird die vorherige (benutzerdefinierte oder automatisch generierte) Besucher-ID abgerufen und als benutzerdefinierte Benutzer-ID (siehe `getUserIdentifier` unten) gespeichert. So werden Besucherdaten auch bei Upgrades des SDK beibehalten. Für neue Installationen für das SDK der Version 4.x lautet die Benutzer-ID `null` und die Tracking-ID wird verwendet.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
       ADB.trackingIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **getUserIdentifier**

   Gibt die benutzerdefinierte Benutzer-ID zurück, wenn eine festgelegt wurde. Andernfalls gibt die Methode `null` zurück. Der Standardwert lautet `null`.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      getUserIdentifier(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **setUserIdentifier**

   Legt die Benutzerkennung auf `identifier` fest.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   Legt das Geräte-Token für Push-Benachrichtigungen fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```javascript
      ADB.setPushIdentifier(pushIdentifier,success,fail);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.setPushIdentifier('test_push_identifier',function(value){alert('success');},function(value){alert('fail');
      ```

* **keepLifecycleSessionAlive**

   Legt den Keepalive-Wert der Lebenszyklussitzung fest.

   >[!IMPORTANT]
   >
   >Der Aufruf von `keepLifecycleSessionAlive` verhindert, dass Ihre App eine neue Sitzung startet, wenn sie aus dem Hintergrund fortgesetzt wird. Sie sollten diese Methode nur verwenden, wenn Ihre App für Benachrichtigungen im Hintergrund registriert ist.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **trackingSendQueuedHits**

   Zwingt die Bibliothek, alle Treffer in der Warteschlange unabhängig von aktuellen Batch-Optionen zu senden.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   Ruft die Anzahl der in der Offline-Warteschlange gespeicherten Verfolgungsaufrufe ab oder legt diese fest.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.trackingGetQueueSize(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **trackingClearQueue**

   Entfernt sämtliche in der Offline-Warteschlange gespeicherten Verfolgungsaufrufe.

   >[!CAUTION]
   >
   >Gehen Sie beim manuellen Leeren der Warteschlange vorsichtig vor. Dieser Vorgang kann nicht rückgängig gemacht werden.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.trackingClearQueue(function(value){myTempVal = value;},function(){myTempVal = null;}); 
      ```

* **keepLifecycleSessionAlive**

   Gibt dem SDK gegenüber an, dass beim nächsten Fortsetzen aus der Ausführung im Hintergrund keine neue Sitzung gestartet werden soll, unabhängig vom Wert für den Lebenszyklussitzungs-Timeout in der Konfigurationsdatei.

   >[!IMPORTANT]
   >
   >Wichtig: Diese Methode ist für Apps vorgesehen, die sich für Benachrichtigungen während der Ausführung im Hintergrund registrieren und die nur aus dem Code heraus aufgerufen werden sollen, der aktiv ist, wenn die App im Hintergrund ausgeführt wird.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.keepLifecycleSessionAlive();
      ```

* **collectLifecycleData**

   Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Nutzung aller Lösungen im SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/ios/metrics.md).

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.collectLifecycleData(); 
      ```


## PII-Methoden {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   Sendet eine Anfrage zur Erfassung personenbezogener Daten.

   * Hier finden Sie die Syntax für diese Methode:

      ```javascript
      ADB.collectPII(piiData,success,fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success'); },function (value) { alert('fail'); });
      ```

## Tracking-Methoden {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   Verfolgt einen Adobe-Deep-Link-Clickthrough.

   >[!TIP]
   >
   >Wenn es sich bei dem Lebenszyklusaufruf um ein Startereignis handelt, werden die Adobe-Linkdaten automatisch angehängt. Andernfalls wird ein zusätzlicher Aufruf gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```javascript
      ADB.trackAdobeDeepLink(deeplinkURL,success,fail);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackPushMessageClickthrough**

   Verfolgt die Clickthrough-Rate bei Push-Nachrichten.

   * Hier finden Sie die Syntax für diese Methode:

      ```javascrpt
      ADB.trackPushMessageClickthrough(userInfo,success,fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.trackPushMessageClickthrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackLocalNotificationClickThrough**

   Verfolgt einen lokalen Benachrichtigungs-Clickthrough-Vorgang.

   * Hier finden Sie die Syntax für diese Methode:

      ```javascript
      ADB.trackLocalNotificationClickThrough(userInfo,success,fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.trackLocalNotificationClickThrough({'k1':'v1','k2':'v2','k3':'v3'},function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **trackState**

   Verfolgt einen App-Status mit optionalen Kontextdaten. Die Statusangaben entsprechen den verfügbaren Ansichten in der App, z. B. `home dashboard`, `app settings` und `cart`. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `trackState`-Aufrufe inkrementieren die Seitenansichten. cData ist ein JSON-Objekt mit Schlüssel-Wert-Paaren, die in den Kontextdaten gesendet werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```javascript
      ADB.trackState(stringstateName[,JSONcData]); 
      ```

   * Hier finden Sie Code-Beispiele für diese Methode:

      ```javascript
      ADB.trackState("loginpage");
      ```

      ```javascript
        ADB.trackState("loginpage",{"user":"john","remember":"true"});
      ```

* **trackAction**

   Verfolgt eine Aktion in der App. Bei Aktionen handelt es sich um die Dinge, die in Ihrer App vor sich gehen, die Sie messen möchten, einschließlich `logins`, `banner taps`, `feed subscriptions` und anderer Metriken.

   * Hier finden Sie die Syntax für diese Methode:

      ```javascript
      ADB.trackAction(stringaction[,JSONcData]);
      ```

   * Hier finden Sie Code-Beispiele für diese Methode:

      ```javascript
      ADB.trackAction("login");
      ```

      ```javascript
      ADB.trackAction("login",{"user":"john","remember":"true"})
      ```

* **trackActionFromBackground**

   Verfolgt eine Aktion, die im Hintergrund aufgetreten ist. Dadurch wird das Auslösen von Lebenszyklusereignissen in bestimmten Szenarien unterbunden.

   * Hier finden Sie die Syntax für diese Methode:

      ```javascript
      ADB.trackActionFromBackground(stringaction[,JSONcData]); 
      ```

   * Hier finden Sie Code-Beispiele für diese Methode:

      ```javascript
      ADB.trackActionFromBackground("login");
      ```

      ```javascript
      ADB.trackActionFromBackground("login",{"user":"john","remember":"true"});
      ```

* **trackLocation**

   Sendet die aktuellen X- und Y-Koordinaten. Ermittelt außerdem anhand der in der Datei `ADBMobileConfig.json` definierten Zielpunkte (POIs), ob der als Parameter angegebene Standort in einem vorhandenen Zielpunkt liegt. Falls die aktuellen Koordinaten auf einen definierten POI passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem `trackLocation`-Aufruf gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```javascript
       ADB.trackLocation(x,y[,JSONcData]);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      ADB.trackLocation('40.431596','-111.893713');
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Erhöht den Lebenszeitwert des Benutzers um `amount`.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSONcData]);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.trackLifetimeValueIncrease('10.01');
      ```

* **trackTimed&#x200B;ActionStart**

   Startet eine zeitgesteuerte Aktion mit dem Namen `action`. Wenn Sie diese Methode für eine bereits gestartete Methode aufrufen, wird die vorherige zeitgesteuerte Aktion überschrieben.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.trackTimedActionStart(action[,JSONcData]);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   Übergibt `cData`, mit denen die Kontextdaten für die vorliegende `action` aktualisiert werden sollen. Die übergebenen `cData` werden an die vorhandenen Daten für die Aktion angehängt. Falls bereits ein Schlüssel für die `action` definiert ist, werden die vorhandenen Daten dieses Schlüssels überschrieben.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.trackTimedActionUpdate(Stringaction[,JSONcData]);
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

   Gibt an, ob derzeit eine zeitgesteuerte Aktion ausgeführt wird oder nicht.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.trackingTimedActionExists(function(value){myTempVal = value;},function(){myTempVal = null;});
      ```


## Target-Methoden {#section_C45D2FE54AE04EB5BD24D3508F8A3212}

* **targetLoadRequest**

   Sendet eine Anfrage an den konfigurierten `Target`-Server und gibt die Zeichenfolge des Angebots zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.targetLoadRequest(success,fail,name,defaultContent,parameters); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.targetLoadRequest(function (value)
      {myTempVal = value;},function() {myTempVal = null;},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   Sendet eine Anfrage an Ihren konfigurierten Target-Server.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.targetLoadOrderConfirmRequest(success,fail,name,orderId,orderTotal,productPurchaseId,parameters); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.targetLoadRequest(function(value){myTempVal=value;}
      ,function()
      {myTempVal = null; }
      ,'name','orderId','total','purchaseId'
      ,{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   Löscht die Target-Cookies aus dem gemeinsamen Cookie-Speicher.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.targetClearCookies();
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Verarbeitet eine Target-Serviceanfrage.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(success,fail,name,defaultContent,profileParameters,orderParameters,mboxParameters,requestLocationParameters
      ); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(function(){alert('success');},function(){alert('fail');},'bannerOffer','none',{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe','hp.val2':'hp_val2'}); 
      ```

* **targetLoadRequestWithName**

   Verarbeitet eine Target-Serviceanfrage.

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
      ADB.targetSessionID(success,fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
        ADB.targetSessionID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

* **targetPcID**

   Ruft den Wert des Cookies `PcID` ab, das für diesen Besucher vom Target-Server zurückgegeben wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.targetPcID(success,fail);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.targetPcID(function(value){alert(value);},function(value){alert('fail');});
      ```

* **targetSetThirdPartyID**

   Legt die benutzerdefinierte Besucher-ID für Target fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID,success,fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Gruppe:

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id',function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **targetThirdPartyID**

   Ruft die benutzerdefinierte Besucher-ID für Target ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.targetThirdPartyID(success,fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.targetThirdPartyID(function(value){alert(value);},function(value){alert('fail');}); 
      ```

## Akquisemethoden {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   Ermöglicht es Entwicklern, eine App-Akquisekampagne so zu starten, als hätte der Benutzer einen Link aufgerufen. Dies ist hilfreich beim Erstellen von manuellen Akquise-Links und beim manuellen Verarbeiten der Umleitung zum App-Store, beispielsweise mit einer `SKStoreView`.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.acquisitionCampaignStartForApp(appId,data,success,fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.acquisitionCampaignStartForApp('0652024f-adcd-49f9-9bd7-2552a4564d2f',{'extraDataKey':'extraDataValue'},success,fail); 
      ```


## Advertising-ID {#section_194607D101B047A19C51B19E176E1500}

Rufen Sie im von Cordova generierten `AppDelegate` `[ADBMobile setAdvertisingIdentifier:]` in der „delegate“-Methode `application:didFinishLaunchingWithOptions:` auf. Weitere Informationen finden Sie unter [Konfigurationsmethoden](/help/ios/configuration/sdk-methods.md).

## Audience Manager-Methoden {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   Ruft das Besucherprofil ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.audienceGetVisitorProfile();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.audienceGetVisitorProfile(function(value){profile = value;},function(){profile = null;}); 
      ```

* **audienceGetDpuuid**

   Gibt die DPUUID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.audienceGetDpuuid(success,fail);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
       ADB.audienceGetDpuuid(function(value){dpuuid=value;},function(){dpuuid=null;}); 
      ```

* **audienceGetDpid**

   Gibt die DPID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
       ADB.audienceGetDpid(success,fail);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;},function(){dpid = null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   Legt die DPID und die DPUUID fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid,dpuuid,success,fail);
      ```

   * Hier finden Sie Code-Beispiele für diese Methode:

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’,function(){…},function(){…});
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’,‘dpuuid’);
      ```

* **audienceSignalWithData**

   Verarbeitet eine Audience Manager-Dienstanforderung.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.audienceSignalWithData(success,fail,data);
      ```

   * Hier finden Sie Code-Beispiele für diese Methode:

      ```java
      ADB.audienceSignalWithData(function(){},function(){},{‘key1’:’value1’,‘key2’:‘value2’});
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’:’value1’,‘key2’:‘value2’}); 
      ```

* **audienceReset**

   Setzt die UUID des Zielgruppen-Managers zurück und löscht das aktuelle Besucherprofil.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.audienceReset(); 
      ```

## ID-Dienst-Methoden {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   Gibt die Experience Cloud ID vom ID-Service zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.visitorGetMarketingCloudId(success,fail);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.visitorGetMarketingCloudId(function(value){mcid=value;},function(){mcid=null;}); 
      ```

* **visitorSyncIdentifiers**

   Synchronisiert die bereitgestellten IDs mit dem ID-Service.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.visitorSyncIdentifiers(identifiers,success,fail);
      ```

   * Hier finden Sie Code-Beispiele für diese Methode:

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’},function(){…},function(){…})) 
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:‘value_id_1’});
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   Synchronisiert die bereitgestellten IDs mit dem Besucher-ID-Dienst.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState(identifiers,authenticationState,success,fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'},ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');});
      ```

* **visitorSyncIdentifierWithType**

   Synchronisiert die bereitgestellte ID mit dem Besucher-ID-Dienst.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType,identifier,authenticationState,success,fail); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type','test-identifier',ADB.mobileVisitorAuthenticationStateAuthenticated,function(value){alert('success');},function(value){alert('fail');}); 
      ```

* **visitorAppendToURL**

   Hängt die Besucherkennungen an die angegebene URL an.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.visitorAppendToURL(urlToAppend,success,fail);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.visitorAppendToURL('test_visitor_url',function(value){alert(value);},'');
      ```

* **visitorGetIDs**

   Gibt alle `visitorIDs` zurück, die synchronisiert wurden.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      ADB.visitorGetIDs(success,fail)
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADB.visitorGetIDs(function(value){alert(value);},function(value){alert('fail');}); 
      ```
