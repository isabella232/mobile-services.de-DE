---
description: Hier finden Sie Informationen zur Verwendung des Windows 8.1 Universal App Store-SDK mit Adobe Analytics.
seo-description: Hier finden Sie Informationen zur Verwendung des Windows 8.1 Universal App Store-SDK mit Adobe Analytics.
seo-title: Analytics-Methoden
solution: Marketing Cloud, Analytics
title: Analytics-Methoden
topic: Entwickler und Implementierung
uuid: 79 db 105 c -216 c -4061-97 f 3-a 55954995 e 67
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

Hier finden Sie Informationen zur Verwendung des Windows 8.1 Universal App Store-SDK mit Adobe Analytics.

Das SDK unterstützt derzeit mehrere Adobe Experience Cloud-Lösungen], einschließlich Analytics], Target] und Audience Manager]. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Analysemethoden ist „Analytics“ als Präfix vorangestellt.

Jede dieser Methoden wird zum Senden von Daten in Ihre Adobe Analytics Report Suite verwendet.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **Trackstate (winjs: Trackstate)**

   Verfolgt einen App-Status mit optionalen Kontextdaten. Status sind die in Ihrer App verfügbaren Ansichten wie „Startseiten-Dashboard“, „App-Einstellungen“, „Warenkorb“ usw. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `TrackState`-Aufrufe inkrementieren die Seitenansichten. Wenn `state` leer ist, wird es in Berichten als „app name app version (build)“ angezeigt. If you see this value in reports, make sure you are setting `state` in each `TrackState` call.

   >[!TIP]
   >
   >Dies ist der einzige Verfolgungsaufruf, der Seitenansichten inkrementiert.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void TrackState(Platform::String ^state, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^contextData); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      ADB.Analytics.trackState("loginScreen", null);
      ```

* **Trackaction (winjs: Trackaction)**

   Verfolgt eine Aktion in der App. Bei Aktionen handelt es sich um die Dinge, die in Ihrer App vor sich gehen, die Sie messen möchten, beispielsweise „Anmeldungen“, „Banner-Tippvorgänge“, „Feed-Abonnements“ und andere Metriken.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void TrackAction(Platform::String ^action, Windows::Foundation::Collections::IMap <Platform::String^, Platform::Object> ^contextData);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackAction("Button Click", null); 
      ```

* **Gettrackingidentifierasync (winjs: Gettrackingidentifierasync)**

   Gibt die automatisch erzeugte Besucherkennung für Analytics zurück. Diese appspezifische, eindeutige Besucherkennung wird beim ersten Starten erzeugt, gespeichert und dann fortlaufend weiterverwendet. Die ID bleibt bei der Aktualisierung der App erhalten und wird beim Deinstallieren entfernt.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String^> ^GetTrackingIdentifierAsync(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var trackingIdentifier; 
      ADBMobile.Analytics.getTrackingIdentifierAsync().then(function (trackingid) { 
         trackingIdentifier = trackingid; 
      });
      ```

* **Tracklocation (winjs: Tracklocation)**

   Sendet die aktuellen XY-Koordinaten. Ermittelt außerdem anhand der in der Datei `ADBMobileConfig.json` definierten Zielpunkte (POI), ob der als Parameter angegebene Standort in einem vorhandenen Zielpunkt liegt. Falls die aktuellen Koordinaten auf einen definierten POI passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem `trackLocation`-Aufruf gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void TrackLocation(double lat, double lon, double accuracy, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLocation(47.60621, -122.33207, null);
      ```

* **Tracklifetimevalueincrease (winjs: Tracklifetimevalueincrease)**

   Erhöht den Lebenszeitwert des Benutzers um `amount`.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void TrackLifetimeValueIncrease(float amount, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackLifetimeValueIncrease(10, null); 
      ```

* **Tracktimedactionstart (winjs: Tracktimedactionstart)**

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
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionStart("cartToCheckout", null); 
      ```

* **Tracktimedactionupdate (winjs: Tracktimedactionupdate)**

   Übergibt `contextData`, mit denen die Kontextdaten für die vorliegende `action` aktualisiert werden sollen. The `data` passed is appended to the existing data for the given action, and overwrites the data if the same key is already defined for `action`.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void TrackTimedActionUpdate(Platform::String ^action, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile; 
      var contextData = new Windows.Foundation.Collections.PropertySet(); 
      contextData["quantity"] = 3; 
      ADB.Analytics.trackTimedActionUpdate("cartToCheckout", contextData); 
      ```

* **Tracktimedactionexistsasync (winjs: Tracktimedactionexistsasync)**

   Gibt „true“ zurück, wenn die angegebene zeitgesteuerte Aktion vorhanden ist, und andernfalls „false“.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<bool> ^TrackTimedActionExistsAsync(Platform::String ^action); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADBMobile.Analytics.trackTimedActionExistsAsync("signUp").then(function (exists) { 
          actionExists = exists; 
      });
      ```

* **Tracktimedactionend (winjs: Tracktimedactionend)**

   Beendet eine zeitgesteuerte Aktion.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void TrackTimedActionEnd(Platform::String ^action);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile; 
      ADB.Analytics.trackTimedActionEnd("cartToCheckout"); 
      ```

* **Cleartrackingqueue (winjs: Cleartrackingqueue)**

   Löscht alle gespeicherten Treffer aus der Tracking-Warteschlange in Analytics.

   * Hier finden Sie die Syntax für diese Nachricht:

      ```csharp
      static void ClearTrackingQueue();
      ```

   * Im Folgenden finden Sie das Codebeispiel:

      ```js
      ADBMobile.Analytics.clearTrackingQueue();
      ```

* **Getqueuesizeasync (winjs: Getqueuesizeasync)**

   Gibt die Anzahl der Treffer zurück, die zurzeit in der Analytics-Warteschlange gespeichert sind.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<int> ^GetQueueSizeAsync();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var queueSize; 
      ADBMobile.Analytics.getQueueSizeAsync().then(function (size) { 
          queueSize = size; 
      });
      ```
