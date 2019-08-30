---
description: Hier finden Sie eine Liste der TVJS-Methoden, die von der tvOS-Bibliothek bereitgestellt werden.
seo-description: Hier finden Sie eine Liste der TVJS-Methoden, die von der tvOS-Bibliothek bereitgestellt werden.
seo-title: TVJS-Methoden
solution: Marketing Cloud, Analytics
title: TVJS-Methoden
topic: Entwickler und Implementierung
uuid: a 7 bfa 85 a -0 d 6 e -4 f 51-9 a 9 e -70429 c 2 a 9806
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# TVJS-Methoden {#tvjs-methods}

Hier finden Sie eine Liste der TVJS-Methoden, die von der tvOS-Bibliothek bereitgestellt werden.

## Configuration methods {#section_5F82FD2F6A0546B3B4E80DF832E11634}

* **version**

   Gibt die aktuelle Version der Adobe Mobile-Bibliothek zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      version()
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var sdkVersion = ADBMobile.version();
      ```

   * Rückgabe: `String`

* **privacyStatus**

   Gibt die NSUInteger-Darstellung für die Datenschutzstatusaufzählung des aktuellen Benutzers zurück.

   Optionen:

   * `ADBMobilePrivacyStatusOptIn`: Treffer werden sofort gesendet.
   * `ADBMobilePrivacyStatusOptOut`: Treffer werden verworfen.
   * `ADBMobilePrivacyStatusUnknown`: Wenn die Offline-Verfolgung aktiviert ist, werden die Zugriffe gespeichert, bis der Datenschutzstatus zu „opt-in“ (Zugriffe werden dann gesendet) oder „opt-out“ (Zugriffe werden dann verworfen) geändert wird.

      Ist die Offline-Verfolgung nicht aktiviert, werden die Treffer verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird. THe default value is set in the `ADBMobileConfig.json` file.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      privacyStatus()
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var privacyStatus = ADBMobile.privacyStatus();
      ```

   * Rückgabe: `Number`

* **setPrivacyStatus**

   Legt den Datenschutzstatus für den aktuellen Benutzer auf einen der folgenden Werte fest:

   * `ADBMobilePrivacyStatusOptIn`: Treffer werden sofort gesendet.
   * `ADBMobilePrivacyStatusOptOut`: Treffer werden verworfen.
   * `ADBMobilePrivacyStatusUnknown`: Wenn die Offline-Verfolgung aktiviert ist, werden die Zugriffe gespeichert, bis sich der Datenschutzstatus ändert (Treffer werden gesendet), oder die Abmeldung (Treffer werden verworfen).
   Ist die Offline-Verfolgung nicht aktiviert, werden die Treffer verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      setPrivacyStatus(privacyStatus)
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```


* **lifetimeValue**

   Gibt den Lebenszeitwert für den aktuellen Benutzer zurück. Der Standardwert lautet `0`.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      lifetimeValue()
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var ltv = ADBMobile.lifetimeValue();
      ```

   * Rückgabe: `Number`

* **userIdentifier**

   Gibt die Benutzer-ID zurück, sofern eine benutzerdefinierte ID festgelegt wurde. Gibt „nil“ zurück, wenn keine benutzerdefinierte ID festgelegt wurde. Die Standardeinstellung lautet `nil`.

   >[!IMPORTANT]
   >
   >Wenn Ihre App-Upgrades vom Experience Cloud 3. x auf 4. x-SDK aktualisiert werden, wird die vorherige oder automatisch erzeugte Besucher-ID abgerufen und als benutzerdefinierte Benutzer-ID gespeichert. Dadurch werden Besucherdaten zwischen SDK-Upgrades beibehalten. Für neue Installationen für das SDK der Version 4.x lautet die Benutzer-ID nil, bis die Festlegung erfolgt.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      userIdentifier()
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var uid = ADBMobile.userIdentifier();
      ```

   * Rückgabe: `String`

* **setUserIdentifier**

   Legt die Benutzer-ID fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      setUserIdentifier(userId)
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.setUserIdentifier(‘myUserId’);
      ```

   * Gibt Folgendes zurück: N/A

   * Parameter:  `userID`

      * Typ: String
      * Neue ID für diesen Benutzer.

* **setAdvertisingIdentifier**

   Legt IDFA im SDK fest. Wenn es im SDK festgelegt wurde, wird IDFA im Lebenszyklus gesendet. Auf den IDFA kann auch in Signalen (Postbacks) zugegriffen werden.

   >[!IMPORTANT]
   >
   >Rufen Sie IDFA nur aus Apple apis ab, wenn Sie einen Anzeigendienst verwenden. Wenn Sie den IDFA abrufen und ihn nicht richtig verwenden, wird Ihre App ggf. abgelehnt.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      setAdvertisingIdentifier(idfa)
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.setAdvertisingIdentifier(‘myIdfa’);
      ```

   * Gibt Folgendes zurück: N/A
   * Parameter: `idfa`
      * Typ: `String`
      * Aus der Apple-API abgerufener IDFA.

* **setDebugLogging**

   Legt die Debug-Protokollierungsvoreinstellung fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      setDebugLogging(logging)
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      `ADBMobile.setDebugLogging(true);
      ```

   * Gibt Folgendes zurück: N/A
   * Parameter: `logging`
      * Typ: `Bool`
      * Der Wert gibt an, ob das Adobe-SDK Protokollierungen an der Debug-Konsole vornehmen sollte.


## Analytics methods {#section_F3DB9BE225F84F86BE5F8D15164C0379}

* **trackStateData**

   Verfolgt einen App-Status mit optionalen Kontextdaten. Status sind die in Ihrer App verfügbaren Ansichten wie Startseiten-Dashboard, App-Einstellungen, Warenkorb usw. Diese Statusangaben sind mit den Seiten einer Website vergleichbar und trackState-Aufrufe erhöhen die Seitenaufrufe.

   Wenn der Status leer ist, wird es in Berichten als app name app version (build) angezeigt. Wenn dieser Wert in einem Bericht angezeigt wird, müssen Sie den Status in jedem trackState-Aufruf festlegen.

   >[!TIP]
   >
   >Dies ist der einzige Verfolgungsaufruf, der Seitenansichten inkrementiert.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      trackStateData(stateName [, contextData])
      ```

      * Gibt Folgendes zurück: N/A
      * Parameter: `stateName`
         * Typ: `String`
         * Seitenstatusname
      * Parameter: `contextData`
         * Typ: Objekt
         * Zusätzliche Kontextdaten für diesen Treffer.
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.trackStateData(‘homepage’, {‘userid’:12345});
      ```




* **trackActionData**

   Verfolgt eine Aktion in der App. Bei Aktionen handelt es sich um die Dinge, die in Ihrer App vor sich gehen, die Sie messen möchten, beispielsweise Anmeldungen, Banner-Tippvorgänge, Feed-Abonnements und andere Metriken.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      trackActionData(actionName [, contextData])
      ```

      * Gibt Folgendes zurück: N/A
      * Parameter: `actionName`
         * Typ: String
         * Name der zu verfolgenden Aktion.
      * Parameter: `contextData`
         * Typ: Objekt
         * Zusätzliche Kontextdaten für diesen Treffer.
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.trackActionData(‘likeClicked’, {‘imageName’:’funnyKitty’});
      ```



* **trackLocationWithLatLonData**

   Sendet die aktuellen Koordinaten (Längen- und Breitengrad).

   Also uses points of interest (POI) that are defined in the `ADBMobileConfig.json` file to determine whether the location that you entered as a parameter is in any of your POIs. Falls die aktuellen Koordinaten auf einen definierten Zielpunkt passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem `trackLocation`-Aufruf gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      trackLocationWithLatLonData(lat, lon [, contextData]);
      ```

      * Gibt Folgendes zurück: N/A
      * Parameter: `lat`
         * Typ: Zahl
         * Breitengrad des Standorts.
      * Parameter: `lon`
         * Typ: Zahl
         * Längengrad des Standorts.
      * Parameter: `contextData`
         * Typ: Objekt
         * Zusätzliche Kontextdaten für diesen Treffer.
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.trackLocationWithLatLonData(43.36, -116.12, null);
      ```




* **trackLifetimeValueIncreaseJsData**

   Erhöht den Lebenszeit-Wert des Benutzers.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      trackLifetimeValueIncreaseJsData(increaseAmount)
      ```

      * Gibt Folgendes zurück: N/A
      * Parameter: `increaseAmount`
         * Typ: Zahl
         * Zum aktuellen Lebenszeitwert des Benutzers hinzuzufügender Betrag.
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.trackLifetimeValueIncreaseJsData(5);
      ```


* **trackTimedActionStartData**

   Beginnt eine zeitgesteuerte Aktion mit einer benannten Aktion. Wenn Sie diese Methode für eine bereits gestartete Methode aufrufen, wird die vorherige zeitgesteuerte Aktion überschrieben.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      trackTimedActionStartData(name [, contextData])
      ```

      * Gibt Folgendes zurück: N/A
      * Parameter: `name`
         * Typ: String
         * Name der zu startenden zeitgesteuerten Aktion.
      * Parameter: `contextData`
         * Typ: Objekt
         * Zusätzliche Kontextdaten für diesen Treffer.
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.trackTimedActionStartData(‘level1’, {‘userId’:42423});
      ```


* **trackTimedActionUpdateData**

   Übergibt Daten, mit denen die Kontextdaten für die vorliegende Aktion aktualisiert werden sollen.

   Die übergebenen Daten werden für die angegebene Aktion an die vorhandenen Daten angehängt. Wenn derselbe Schlüssel bereits für die Aktion definiert ist, werden die Daten überschrieben.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      trackTimedActionUpdateData(name [, contextData])
      ```

      * Gibt Folgendes zurück: N/A
      * Parameter: `name`
         * Typ: String
         * Name der zu aktualisierenden zeitgesteuerten Aktion.
      * Parameter: `contextData`
         * Typ: Objekt
         * Zusätzliche Kontextdaten für diesen Treffer.
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.trackTimedActionUpdateData(‘level1’);
      ```



* **trackTimedActionEndJsLogic**

   Beendet eine zeitgesteuerte Aktion.

   Wenn Sie eine Callback-Funktion bereitstellen, können Sie auf die endgültigen Zeitwerte zugreifen. Wenn kein Callback angegeben ist oder der Callback „true“ zurückgibt, sendet das Adobe-SDK automatisch einen Treffer. Wenn ein FALSE aus dem Rückruf zurückgegeben wird, wird der Treffer für die zeitgesteuerte Aktion unterdrückt.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      trackTimedActionEndJsLogic(name [, callback])
      ```

      * Gibt Folgendes zurück: N/A
      * Parameter: `name`
         * Typ: String
         * Name der zu beendenden zeitgesteuerten Aktion
      * Parameter: `callback`
         * Typ: `function(inAppDuration, totalDuration, data)`
         * Callback method that will have `inAppDuration` (number), `totalDuration` (number), and `data` (context data object) in its parameters.

            You can suppress the final hit from being sent by the SDK by returning `false` in your callback function.
      * Hier finden Sie ein Code-Beispiel für diese Methode:

         ```objective-c
         ADBMobile.trackTimedActionEndJsLogic(‘level1’, 
         function(inAppDuration, totalDuration, data) {
             // do something with final values
             return true;
             });
         ```



* **trackingTimedActionExistsJs**

   Gibt zurück, ob derzeit eine zeitgesteuerte Aktion ausgeführt wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      trackingTimedActionExistsJs(name)
      ```

      * Gibt Folgendes zurück: Bool
      * Parameter: `name`
         * Typ: `String`
         * Name der zeitgesteuerten Aktion, die Sie prüfen müssen.
   * Hier finden Sie ein Code-Beispiel für diese Methode:


      ```objective-c
      var actionExists = ADBMobile.trackTimedActionExistsJs(‘level1’);
      ```


* **trackingIdentifier**

   Gibt die automatisch generierte Besucher-ID zurück.

   Hierbei handelt es sich um eine App-spezifische Unique Visitor-ID, die von den Adobe-Servern generiert wird. Wenn die Adobe-Server zum Zeitpunkt der Generierung nicht erreicht werden können, wird die ID mithilfe der CFUUID von Apple generiert. Der Wert wird beim ersten Start generiert, dann gespeichert und von diesem Zeitpunkt an verwendet. Diese ID wird zwischen App-Upgrades beibehalten. Sie wird gespeichert, während des Standardanwendungs-Backup-Vorgangs wiederhergestellt und bei der Deinstallation der App entfernt.

   >[!TIP]
   >
   >Wenn Ihre App-Upgrades vom Experience Cloud 3. x auf 4. x-SDK aktualisiert werden, wird die vorherige oder automatisch erzeugte Besucher-ID abgerufen und als benutzerdefinierte Benutzer-ID gespeichert. Dadurch werden Besucherdaten zwischen SDK-Upgrades beibehalten. Für neue Installationen für das SDK der Version 4.x lautet die Benutzer-ID `nil` und die Tracking-ID wird verwendet. Weitere Informationen finden Sie unten in der Zeile userIdentifier.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      trackingIdentifier()
      ```

      * Rückgabe: `String`
      * Parameter: Ohne
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var trackingId = ADBMobile.trackingIdentifier();
      ```


* **trackingSendQueuedHits**

   Erzwingt in der Bibliothek das Senden aller Zugriffe aus der Offline-Warteschlange, unabhängig von der Anzahl der Zugriffe.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      trackingSendQueuedHits()
      ```

      * Gibt Folgendes zurück: N/A
      * Parameter: Ohne
   * Hier finden Sie ein Code-Beispiel für diese Methode:


      ```objective-c
      ADBMobile.trackingSendQueuedHits();
      ```


* **trackingClearQueue**

   Löscht alle Zugriffe aus der Offline-Warteschlange.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      trackingClearQueue()
      ```

      * Gibt Folgendes zurück: N/A
      * Parameter: Ohne
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.trackingClearQueue();
      ```


* **trackingGetQueueSize**

   Ruft die Anzahl der Zugriffe ab, die sich derzeit in der Offline-Warteschlange befinden.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      trackingGetQueueSize()
      ```

      * Gibt Folgendes zurück: Zahl
      * Parameter: Ohne
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var queueSize = ADBMobile.trackingGetQueueSize();
      ```


## Audience Manager methods {#section_0155C4DF04644EDAAF6159C420A158DE}

* **audienceVisitorProfile**

   Gibt das zuletzt erfasste Besucherprofil zurück.

   Gibt null zurück, falls noch kein Signal übertragen wurde. Das Besucherprofil wird in `NSUserDefaults` gespeichert und steht so bei jedem Start der App zur Verfügung.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      audienceVisitorProfile()
      ```

      * Gibt Folgendes zurück: Objekt
      * Parameter: Ohne
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var profile = ADBMobile.audienceVisitorProfile();
      ```


* **audienceDpid** 

   Gibt die aktuelle DPID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      audienceDpid()
      ```

      * Returns: String
      * Parameter: Ohne
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var dpid = ADBMobile.audienceDpid();
      ```


* **audienceDpuuid**

   Gibt die aktuelle DPUUID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      audienceDpuuid()
      ```

      * Rückgabe: `String`
      * Parameter: Ohne
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var dpuuid = ADBMobile.audienceDpuuid();
      ```


* **audienceSetDpidDpuuid**

   Legt die dpid und dpuuid fest und wenn sie festgelegt wurden, werden Sie bei jedem Signal gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      audienceSetDpidDpuuid(dpid, dpuuid)
      ```

      * Gibt Folgendes zurück: N/A
      * Parameter: `dpid`
         * Typ: `String`
         * Datenanbieter-ID für Audience Manager.
      * Parameter: `dpuuid`
         * Typ: `String`
         * ID für die Kombination aus Benutzer und Datenanbieter.
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.audienceSetDpidDpuuid(‘myDpid’, ‘userDpuuid’);
      ```


* **audienceSignalWithDataJsCallback**

   Sendet Audience Manager ein Signal mit Eigenschaften und ruft die passenden Segmente ab, die in einer Callback-Funktion zurückgegeben werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      audienceSignalWithDataJsCallback(traits [, callback])
      ```

      * Parameter: `traits`
         * Typ: Objekt
         * Eigenschaftenwörterbuch für diesen Benutzer.
      * Parameter: `callback`
         * Typ: function(profile)
         * Das von Audience Manager im Parameter für die Callback-Funktion zurückgegebene Profil.
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.audienceSignalWithDataJsCallback({‘trait’:’something’}, 
      function(profile) {
          //do something with the user’s segments found in profile
           });
      ```



* **audienceReset**

   Setzt die Audience Manager-UUID zurück und löscht das aktuelle Besucherprofil.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      audienceReset()
      ```

      * Gibt Folgendes zurück: N/A
      * Parameter: Keine
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.audienceReset();
      ```


## ID Service methods {#section_BEB6DA612EA4423FB354B65ECC941335}

* **visitorMarketingCloudID**

   Ruft die Experience Cloud ID vom ID-Service ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      visitorMarketingCloudID()
      ```

      * Returns: String
      * Parameter: Ohne
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var mcid = ADBMobile.visitorMarketingCloudID();
      ```


* **visitorSyncIdentifiers**

   Zusätzlich zur Experience Cloud ID können Sie festlegen, dass zusätzliche Kunden-IDs zu jedem Besucher zugeordnet werden. Die Besucher-API akzeptiert mehrere Kunden-IDs für denselben Besucher sowie eine Kundentypkennung, die den Umfang der einzelnen Kunden-IDs abgrenzt. Diese Methode entspricht setCustomerIDs in der JavaScript-Bibliothek.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      visitorSyncIdentifiers(identifiers)
      ```

      * Gibt Folgendes zurück: N/A
      * Parameter: `identifiers`

         * Typ: `Object`
         * IDs zum Synchronisieren des ID-Services für diesen Benutzer.
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.visitorSyncIdentifiers({‘idType’:’idValue’});
      ```


* **visitorSyncIdentifiersAuthenticationState**

   Synchronisiert die bereitgestellten IDs mit dem ID-Service.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      visitorSyncIdentifiersAuthenticationState(identifiers, authState)
      ```

      * Gibt Folgendes zurück: N/A
      * Parameter: `identifiers`
         * Typ: `Object`
         * IDs zum Synchronisieren des ID-Services für diesen Benutzer.
      * Parameter: `authState`
         * Typ: ADBMobileVisitorAuthenticationState
         * Der Authentifizierungsstatus des Benutzers und mögliche Werte umfassen:
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.visitorSyncIdentifiersAuthenticationState({'myIdType':'valueForUser'}, ADBMobileVisitorAuthenticationStateLoggedOut)
      ```



* **visitorSyncIdentifierWithTypeIdentifierAuthenticationState**

   Synchronisiert den bereitgestellten ID-Typ und -Wert mit dem ID-Service.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      visitorSyncIdentifierWithTypeIdentifierAuthenticationState(idType, identifier, authState)
      ```

      * Rückgabe: N/A
      * Parameter: `idType`
         * Typ: `String`
         * Typ der ID, die Sie synchronisieren.
      * Parameter: `identifier`
         * Typ: `String`
         * Wert der ID, die Sie synchronisieren.
      * Parameter: `authState`
         * Typ: Adbmobilevisitorauthenticationstate-Authentifizierungsstatus
des Benutzers. Mögliche Werte:
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.visitorSyncIdentifierWithTypeIdentifierAuthenticationState('myIdType', 'valueForUser', 
      ADBMobileVisitorAuthenticationStateAuthenticated);
      ```


* **visitorGetIDsJs**

   Ruft ein Array schreibgeschützter ADBVisitorID-Objekte ab. Der folgende Code ist ein Beispiel eines „VisitorID“-Objekts:

   ```js
   {
       idType: "abc",
       authenticationState: 1, 
       identifier: "123"
   }
   ```

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      visitorGetIDsJs()
      ```

      * Rückgabe: `Array [Object]`

      * Parameter: Ohne
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var myVisitorIds = ADBMobile.visitorGetIDsJs();
      ```


## Target-Methoden {#section_F9F7EC2B9B7C41AFBCA2458F9F138634}

* **targetThirdPartyID**

   Gibt die Drittanbieter-ID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      targetThirdPartyID()
      ```

      * Rückgabe: `String`
      * Parameter: Ohne
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var thirdPartyID = ADBMobile.targetThirdPartyID();
      ```


* **targetSetThirdPartyID**

   Legt die Drittanbieter-ID fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      targetSetThirdPartyID(thirdPartyID)
      ```

      * Gibt Folgendes zurück: N/A
      * Parameter: `thirdPartyID`
         * Typ: `String`
         * Für Target-Anforderungen zu verwendende Drittanbieter-ID.
   * Hier finden Sie ein Code-Beispiel für diese Methode:

   ```objective-c
   ADBMobile.targetSetThirdPartyID(‘thirdPartyID’);
   ```

* **targetPcID**

   Gibt die PcID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      targetPcID()
      ```

      * Rückgabe: `String`
      * Parameter: Ohne
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var pcID = ADBMobile.targetPcID();
      ```


* **targetSessionID**

   Gibt die Sitzungs-ID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      targetSessionID()
      ```

      * Rückgabe: `String`
      * Parameter: Ohne
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var sessionID = ADBMobile.targetSessionID();
      ```
