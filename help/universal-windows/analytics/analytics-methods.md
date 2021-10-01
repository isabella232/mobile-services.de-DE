---
description: Informationen, die Sie bei der Verwendung des universellen Windows-Plattform-SDK mit Adobe Analytics unterstützen.
solution: Experience Cloud,Analytics
title: Analytics-Methoden
topic-fix: Developer and implementation
uuid: cc299bb5-ec61-49bf-869a-f3c3bc83359f
exl-id: 3ceaedfa-274f-4dc7-9e4c-15233d09f935
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 58%

---

# Analytics-Methoden {#analytics-methods}

Informationen, die Sie bei der Verwendung des universellen Windows-Plattform-SDK mit Adobe Analytics unterstützen.

Das SDK unterstützt derzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target und Audience Manager. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Analytics-Methoden wird &quot;Analytics&quot;vorangestellt.

Jede dieser Methoden wird zum Senden von Daten in Ihre Adobe Analytics Report Suite verwendet.

>[!TIP]
>
>Wenn Sie `winmd`-Methoden aus winJS (JavaScript) verwenden, wird für alle Methoden automatisch der erste Buchstabe kleingeschrieben.

* **TrackState (winJS: trackState)**

   Verfolgt einen App-Status mit optionalen Kontextdaten. Status sind die Ansichten, die in Ihrer App verfügbar sind, z. B. &quot;Startseiten-Dashboard&quot;, &quot;App-Einstellungen&quot;, &quot;Warenkorb&quot;usw. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `TrackState`-Aufrufe inkrementieren die Seitenansichten.
Wenn `state` leer ist, wird in Berichten als &quot;App Name App Version (Build)&quot;angezeigt. Wenn dieser Wert in Berichten auftritt, stellen Sie sicher, dass Sie `state` in jedem `TrackState` -Aufruf festlegen.

   >[!TIP]
   >
   >Dies ist der einzige Verfolgungsaufruf, bei dem die Seitenansichten inkrementiert werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **TrackAction (winJS: trackAction)**

   Verfolgt eine Aktion in der App. Bei Aktionen handelt es sich um die Dinge, die in Ihrer App vor sich gehen, die Sie messen möchten, z. B. &quot;Anmeldungen&quot;, &quot;Banner-Tippvorgänge&quot;, &quot;Feed-Abonnements&quot;und andere Metriken.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackAction("ButtonClick",null); 
      ```

* **GetTrackingIdentifierAsync (winJS: getTrackingIdentifierAsync)**

   Gibt die automatisch generierte Besucher-ID für Analytics zurück. Hierbei handelt es sich um eine App-spezifische Unique Visitor-ID, die beim ersten Start generiert und dann gespeichert und ab diesem Zeitpunkt verwendet wird. Diese ID bleibt zwischen App-Upgrades erhalten und wird bei der Deinstallation entfernt.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String> ^GetTrackingIdentifierAsync(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      vartrackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function(trackingid){
      trackingIdentifier=trackingid;
      });
      ```

* **TrackLocation (winJS: trackLocation)**

   Sendet die aktuellen XY-Koordinaten. Ermittelt außerdem anhand der in der Datei `ADBMobileConfig.json` definierten Zielpunkte (POI), ob der als Parameter angegebene Standort in einem vorhandenen Zielpunkt liegt. Falls die aktuellen Koordinaten auf einen definierten POI passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem `trackLocation`-Aufruf gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      varADB=ADBMobile; 
      ADB.Analytics.trackLocation(47.60621,-122.33207,null);
      ```

* **TrackLifetime &#x200B; ValueIncrease (winJS: trackLifetime &#x200B; ValueIncrease)**

   Erhöht den Lebenszeitwert des Benutzers um `amount`.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackLifetimeValueIncrease(10,null);
      ```

* **TrackTimed &#x200B; ActionStart (winJS: trackTimed &#x200B; ActionStart)**

   Startet eine zeitgesteuerte Aktion mit dem Namen `action`. Wenn Sie diese Methode für eine bereits gestartete Methode aufrufen, wird die vorherige zeitgesteuerte Aktion überschrieben.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void TrackTimedActionStart(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      varADB=ADBMobile;
      ADB.Analytics.trackTimedActionStart("cartToCheckout",null); 
      ```

* **TrackTimed &#x200B; ActionUpdate (winJS: trackTimed &#x200B; ActionUpdate)**

   Übergibt `contextData`, mit denen die Kontextdaten für die vorliegende `action` aktualisiert werden sollen. Die übergebenen `data` werden an die vorhandenen Daten für die Aktion angehängt. Falls bereits ein Schlüssel für die `action` definiert ist, werden die vorhandenen Daten dieses Schlüssels überschrieben.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      varADB = ADBMobile;
      varcontextData = newWindows.Foundation.Collections.PropertySet();
      contextData["quantity"]=3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout",contextData);
      ```

* **TrackTimedActionExistsAsync (winJS: trackTimedActionExistsAsync)**

   Gibt &quot;true&quot;zurück, wenn die angegebene zeitgesteuerte Aktion vorhanden ist, und &quot;false&quot;, wenn sie nicht vorhanden ist.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function(exists){ 
          actionExists = exists; 
      });
      ```

* **TrackTimed &#x200B; ActionEnd (winJS: trackTimed &#x200B; ActionEnd)**

   Beendet eine zeitgesteuerte Aktion.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      varADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **ClearTrackingQueue (winJS: clearTrackingQueue)**

   Löscht alle gespeicherten Treffer aus der Analytics-Tracking-Warteschlange.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void ClearTrackingQueue();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **GetQueueSizeAsync (winJS: getQueueSizeAsync)**

   Gibt die Anzahl der Treffer zurück, die derzeit in der Analytics-Warteschlange gespeichert sind.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      varqueueSize;
      ADBMobile.Analytics.getQueueSizeAsync().then(function(size){ 
          queueSize=size;
      });
      ```
