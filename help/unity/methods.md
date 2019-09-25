---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: ADBMobile.cs-Methoden
solution: Marketing Cloud, Entwickler
title: ADBMobile.cs methods
uuid: af504934-febd-45d9-81e2-2a310f4c65dc
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# ADBMobile.cs methods {#adbmobile-cs-methods}

## Konfigurationsmethoden

* **CollectLifecycleData**

   Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Nutzung aller Lösungen im SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/ios/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void CollectLifecycleData();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.CollectLifecycleData(); 
      ```

* **EnableLocalNotifications (nur iOS)**

   Ermöglicht lokale Benachrichtigungen in der App.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void EnableLocalNotifications();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.EnableLocalNotifications(); 
      ```

* **GetDebugLogging**

   Gibt die aktuelle Vorgabe für die Debug-Protokollierung zurück. Der Standardwert lautet `false`.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static bool GetDebugLogging();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var debugEnabled = ADBMobile.GetDebugLogging();
      ```

* **GetLifetimeValue**

   Gibt den Lebenszeitwert für den aktuellen Benutzer zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static double GetLifetimeValue();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var lifetimeValuea = ADBMobile.GetLifetimeValue();
      ```

* **GetPrivacyStatus**

   Gibt die Enum-Darstellung für den Datenschutzstatus des aktuellen Benutzers zurück.
   * `MOBILE_PRIVACY_STATUS_OPT_IN`: Treffer werden sofort gesendet.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: Treffer werden verworfen.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: Bei aktivierter Offline-Verfolgung werden die Treffer so lange gespeichert, bis sich der Datenschutzstatus in „opt-in“ (anschließend werden die Treffer gesendet) oder „opt-out“ (anschließend werden die Treffer verworfen) ändert.

      Ist die Offline-Verfolgung nicht aktiviert, werden die Zugriffe verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird. Der Standardwert wird in der Datei [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md) festgelegt.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static ADBPrivacyStatus GetPrivacyStatus();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var privacyStatus = ADBMobile.GetPrivacyStatus();
      ```

* **GetUserIdentifier**

   Gibt die benutzerdefinierte Benutzerkennung zurück, sofern eine benutzerdefinierte Kennung festgelegt wurde. Gibt null zurück, wenn keine benutzerdefinierte Kennung festgelegt wurde. Der Standardwert lautet `null`.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static string GetUserIdentifier();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var userId = ADBMobile.GetUserIdentifier(); 
      ```

* **GetVersion**

   Ruft die Bibliotheksversion ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static string GetVersion();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var version = ADBMobile.GetVersion();
      ```

* **KeepLifecycleSessionAlive (nur iOS)**

   Gibt dem SDK gegenüber an, dass beim nächsten Fortsetzen aus der Ausführung im Hintergrund keine neue Sitzung gestartet werden soll, unabhängig vom Wert für den Lebenszyklussitzungs-Timeout in der Konfigurationsdatei.

   >[!TIP]
   >
   >Diese Methode soll für Apps verwendet werden, die sich für Benachrichtigungen im Hintergrund registrieren und nur aus dem Code heraus aufgerufen werden sollten, der ausgeführt wird, während die App im Hintergrund ausgeführt wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void KeepLifecycleSessionAlive(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.KeepLifecycleSessionAlive(); 
      ```

* **PauseCollectingLifecycleData (nur Android)**

   Gibt dem SDK gegenüber an, dass die App angehalten ist, sodass die Lebenszyklusmetriken ordnungsgemäß berechnet werden. Beispiel: Beim Anhalten einen Zeitstempel erfassen, mit dem die Dauer der vorherigen Sitzung ermittelt wird. Hiermit wird außerdem ein Flag gesetzt, sodass im Lebenszyklus ersichtlich wird, dass die App nicht abgestürzt ist. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.PauseCollectingLifecycleData(); 
      ```

* **SetContext (nur Android)**

   Indicates to the SDK that it should set its application context from the UnityPlayer's current activity.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SetContext();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.SetContext(); 
      ```

* **SetDebugLogging**

   Aktiviert die Vorgabe für die Debug-Protokollierung.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SetDebugLogging (bool enabled); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.SetDebugLogging(true); 
      ```

* **SetPrivacyStatus**

   Legt den Datenschutzstatus für den aktuellen Benutzer auf „status“ fest. Die folgenden Werte sind zulässig:

   * `MOBILE_PRIVACY_STATUS_OPT_IN`: Treffer werden sofort gesendet.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: Hits are discarded.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: Bei aktivierter Offline-Verfolgung werden die Treffer so lange gespeichert, bis sich der Datenschutzstatus in „opt-in“ (anschließend werden die Treffer gesendet) oder „opt-out“ (anschließend werden die Treffer verworfen) ändert. Ist die Offline-Verfolgung nicht aktiviert, werden die Zugriffe verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus); 
      ```

   * Here is the code sample for this syntax:

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **SetUserIdentifier**

   Legt die Benutzerkennung auf „userId“ fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SetUserIdentifier(string userId); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.SetUserIdentifier("myCustomUserId"); 
      ```

## Analysemethoden

* **GetTrackingIdentifier**

   Ruft die Analytics-Tracking-ID ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static string GetTrackingIdentifier();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var trackingId = ADBMobile.GetTrackingIdentifier(); 
      ```

* **TrackState**

   Verfolgt einen App-Status mit optionalen Kontextdaten. Die Statusangaben entsprechen den verfügbaren Ansichten in der App, z. B. „Titelbild“, „Level 1“ oder „Pause“. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `TrackState`-Aufrufe inkrementieren die Seitenansichten.

   If state is empty, it displays as *`app name app version (build)`* in reports. Wenn dieser Wert in einem Bericht auftritt, müssen Sie den Status in jedem `TrackState`-Aufruf festlegen.

   >[!TIP]
   >
   >Dies ist der einzige Verfolgungsaufruf, durch den die Seitenansichten inkrementiert werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackState(string state, Dictionary<string, object> cdata);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var contextData = new Dictionary<string, object>); 
      contextData.Add ("user", "jim");
      ADBMobile.TrackState("title screen", contextData);
      ```

* **TrackAction**

   Verfolgt eine Aktion in der App. Aktionen sind die Vorgänge in der App, die gemessen werden sollen, z. B. „Tode“, „Level bestanden“, „Feed-Abonnements“ und weitere Metriken.

   >[!TIP]
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackAction(string action, Dictionary<string, object> cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.TrackAction("level gained", null); 
      ```

* **TrackActionFromBackground (nur iOS)**

   Verfolgt eine Aktion, die im Hintergrund abläuft. Hiermit wird das Auslösen von Lebenszyklusereignissen in bestimmten Situationen unterbunden.

   >[!TIP]
   >
   >Diese Methode sollte nur in Code aufgerufen werden, der ausgeführt wird, während die App im Hintergrund ausgeführt wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackActionFromBackground(string action, Dictionary<string,object> cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   Sendet die aktuellen Koordinaten (Längen- und Breitengrad). Ermittelt außerdem anhand der in der Datei `ADBMobileConfig.json` definierten Zielpunkte (POI), ob der als Parameter angegebene Standort in einem vorhandenen Zielpunkt liegt. Falls die aktuellen Koordinaten auf einen definierten Zielpunkt passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem TrackLocation-Aufruf gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackLocation(float latValue, float lonValue, Dictionary<string, object> cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.TrackLocation(28.418649, -81.581324, null); 
      ```

* **TrackBeacon**

   Verfolgt das Eintreten eines Benutzers in den Radius eines Beacons.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackBeacon(int major, int minor, string uuid, ADBBeaconProximity proximity, Dictionary<string, object> cdata); 
      ```

* **TrackingClearCurrentBeacon**

   Löscht die Beacon-Daten, sobald der Benutzer den Radius des Beacons verlässt.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackingClearCurrentBeacon(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   Erhöht den Lebenszeitwert des Benutzers.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackLifetimeValueIncrease(double amount, Dictionary<string, object> cdata);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.TrackLifetimeValueIncrease(5, null); 
      ```

* **TrackTimedActionStart**

   Beginnt eine zeitgesteuerte Aktion mit einer benannten Aktion. Wenn Sie diese Methode für eine bereits gestartete Methode aufrufen, wird die vorherige zeitgesteuerte Aktion überschrieben.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackTimedActionStart(string action, Dictionary<string,object> cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Übergibt Daten, mit denen die Kontextdaten für die vorliegende Aktion aktualisiert werden sollen. Die übergebenen Daten werden an die vorhandenen Daten für die Aktion angehängt. Falls ein Schlüssel bereits für die Aktion definiert ist, werden die vorhandenen Daten dieses Schlüssels überschrieben.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackTimedActionUpdate(string action, Dictionary<string, object> cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var contextData = new Dictionary<string, object>; 
      contextData.Add("checkpoint", "1:32"); 
         ADBMobile.TrackTimedActionUpdate("level2", contextData);
      ```

* **TrackTimedActionEnd**

   Beendet eine zeitgesteuerte Aktion.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackTimedActionEnd(string action); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.TrackTimedActionEnd("level2"); 
      ```

* **TrackingTimedActionExists**

   Gibt an, ob derzeit eine zeitgesteuerte Aktion ausgeführt wird oder nicht.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
       var level2InProgress = ADBMobile.TrackingTimedActionExists("level2"); 
      ```

* **TrackingSendQueuedHits**

   Erzwingt in der Bibliothek das Senden aller Zugriffe aus der Offline-Warteschlange, unabhängig von der Anzahl der Zugriffe.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackingSendQueuedHits();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **TrackingClearQueue**

   Löscht alle Zugriffe aus der Offline-Warteschlange.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackingClearQueue();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.TrackingClearQueue(); 
      ```

* **TrackingGetQueueSize**

   Ruft die Anzahl der Zugriffe ab, die sich derzeit in der Offline-Warteschlange befinden.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static int TrackingGetQueueSize();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var queueSize = ADBMobile.TrackingGetQueueSize();
      ```

## Experience Cloud ID-Methoden

* **GetMarketingCloudID**

   Ruft die Experience Cloud ID vom ID-Service ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static string GetMarketingCloudID(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Mit der Experience Cloud ID können Sie weitere Kunden-IDs festlegen, die den einzelnen Besuchern zugewiesen werden. Die Besucher-API akzeptiert mehrere Kunden-IDs für denselben Besucher sowie eine Kundentypkennung, die den Umfang der einzelnen Kunden-IDs abgrenzt. Diese Methode entspricht setCustomerIDs in der JavaScript-Bibliothek.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void VisitorSyncIdentifiers(Dictionary<string, object> identifiers); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var ids = new Dictionary<string, object> (); 
      ids.Add ("player1", "jimbob"); 
      ADBMobile.VisitorSyncIdentifiers(ids);
      ```

