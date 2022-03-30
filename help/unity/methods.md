---
description: Konfigurationsmethoden für ADBMobile.cs
keywords: Unity
solution: Experience Cloud Services
title: ADBMobile.cs-Methoden
uuid: af504934-febd-45d9-81e2-2a310f4c65dc
exl-id: d12c16f1-c25c-4698-8943-a660d9c08faf
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 66%

---

# ADBMobile.cs-Methoden {#adbmobile-cs-methods}

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

   Aktivieren Sie lokale Benachrichtigungen in Ihrer App.

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
   * `MOBILE_PRIVACY_STATUS_OPT_IN`: Treffer werden umgehend gesendet.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: Treffer werden verworfen.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: Wenn die Offline-Verfolgung aktiviert ist, werden die Treffer gespeichert, bis der Datenschutzstatus zu &quot;opt-in&quot;(anschließend werden die Treffer gesendet) oder &quot;opt-out&quot;(anschließend werden die Treffer verworfen) geändert wird.

      Ist die Offline-Verfolgung nicht aktiviert, werden die Zugriffe verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird. Der Standardwert wird im [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md) -Datei.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static ADBPrivacyStatus GetPrivacyStatus();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var privacyStatus = ADBMobile.GetPrivacyStatus();
      ```

* **GetUserIdentifier**

   Gibt die benutzerdefinierte Benutzer-ID zurück, wenn eine benutzerdefinierte ID festgelegt wurde. Gibt null zurück, wenn keine benutzerdefinierte ID festgelegt ist. Der Standardwert lautet `null`.

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
   >Diese Methode ist für Apps vorgesehen, die sich für Benachrichtigungen während der Ausführung im Hintergrund registrieren und die nur aus dem Code heraus aufgerufen werden sollen, der aktiv ist, während die App im Hintergrund ausgeführt wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void KeepLifecycleSessionAlive();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.KeepLifecycleSessionAlive();
      ```

* **PauseCollectingLifecycleData (nur Android)**

   Gibt dem SDK gegenüber an, dass die App angehalten ist, sodass die Lebenszyklusmetriken ordnungsgemäß berechnet werden. Beispiel: Bei Pause erfasst einen Zeitstempel, mit dem die Dauer der vorherigen Sitzung bestimmt wird. Dadurch wird auch eine Markierung gesetzt, sodass der Lebenszyklus richtig erkennt, dass die App nicht abgestürzt ist. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.PauseCollectingLifecycleData();
      ```

* **SetContext (nur Android)**

   Gibt dem SDK gegenüber an, dass der Anwendungskontext über die aktuelle Aktivität von UnityPlayer festgelegt werden soll.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SetContext();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.SetContext();
      ```

* **SetDebugLogging**

   Legt die Debug-Protokollierungseinstellung auf &quot;Aktiviert&quot;fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SetDebugLogging (bool enabled);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.SetDebugLogging(true);
      ```

* **SetPrivacyStatus**

   Legt den Datenschutzstatus für den aktuellen Benutzer auf den Status fest. Die folgenden Werte sind zulässig:

   * `MOBILE_PRIVACY_STATUS_OPT_IN`: Treffer werden umgehend gesendet.
   * `MOBILE_PRIVACY_STATUS_OPT_OUT`: Treffer werden verworfen.
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: Wenn die Offline-Verfolgung aktiviert ist, werden die Treffer gespeichert, bis der Datenschutzstatus zu &quot;opt-in&quot;(anschließend werden die Treffer gesendet) oder &quot;opt-out&quot;(anschließend werden die Treffer verworfen) geändert wird. Ist die Offline-Verfolgung nicht aktiviert, werden die Zugriffe verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Syntax:

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **SetUserIdentifier**

   Legt die Benutzer-ID auf userId fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SetUserIdentifier(string userId);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.SetUserIdentifier("myCustomUserId");
      ```

## Analytics-Methoden

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

   Verfolgt einen App-Status mit optionalen Kontextdaten. Status sind die in Ihrer App verfügbaren Ansichten, z. B. &quot;Titelbildschirm&quot;, &quot;Level 1&quot;, &quot;Pause&quot;. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `TrackState`-Aufrufe inkrementieren die Seitenansichten.

   Wenn der Status leer ist, wird er als *`app name app version (build)`* in Berichten. Wenn dieser Wert in Berichten auftritt, stellen Sie sicher, dass Sie in jedem `TrackState` aufrufen.

   >[!TIP]
   >
   >Dies ist der einzige Verfolgungsaufruf, bei dem die Seitenansichten inkrementiert werden.

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

   Verfolgt eine Aktion in der App. Bei Aktionen handelt es sich um die Dinge, die in Ihrer App vor sich gehen, die Sie messen möchten, z. B. &quot;Todesfälle&quot;, &quot;Erreichte Stufe&quot;, &quot;Feed-Abonnements&quot;und andere Metriken.

   >[!TIP]
   >
   >Falls Code aktiv ist, während die App im Hintergrund ausgeführt wird (z. B. Datenabruf im Hintergrund), verwenden Sie stattdessen `trackActionFromBackground`.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackAction(string action, Dictionary<string, object> cdata);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.TrackAction("level gained", null);
      ```

* **TrackActionFromBackground (nur iOS)**

   Verfolgt eine Aktion, die im Hintergrund aufgetreten ist. Dadurch wird das Auslösen von Lebenszyklusereignissen in bestimmten Szenarien unterbunden.

   >[!TIP]
   >
   >Diese Methode sollte nur in Code aufgerufen werden, der aktiv ist, während die App im Hintergrund ausgeführt wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackActionFromBackground(string action, Dictionary<string,object> cdata);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   Sendet die aktuellen Koordinaten (Längen- und Breitengrad). Ermittelt außerdem anhand der in der Datei `ADBMobileConfig.json` definierten Zielpunkte (POI), ob der als Parameter angegebene Standort in einem vorhandenen Zielpunkt liegt. Wenn die aktuellen Koordinaten auf einen definierten POI passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem TrackLocation -Aufruf gesendet.

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

   Erhöht den Lebenszeitwert des Benutzers um einen Wert.

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

   Übergibt Daten, um die Kontextdaten zu aktualisieren, die mit der angegebenen Aktion verknüpft sind. Die übergebenen Daten werden an die vorhandenen Daten für die Aktion angehängt und überschreiben die Daten, wenn der Schlüssel bereits für die Aktion definiert ist.

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

## Experience Cloud-ID-Methoden

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

   Mit der Experience Cloud-ID können Sie zusätzliche Kunden-IDs festlegen, die jedem Besucher zugeordnet werden. Die Besucher-API akzeptiert mehrere Kunden-IDs für denselben Besucher sowie eine Kundentypkennung, die den Umfang der einzelnen Kunden-IDs abgrenzt. Diese Methode entspricht setCustomerIDs in der JavaScript-Bibliothek.

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

## Akquisemethoden 

* **ProcessGooglePlayInstallReferrerUrl** *(Nur Android)*

   Übergeben Sie die Referrer-URL, die von einem Aufruf an die Google Play Install Referrer API zurückgegeben wird, an diese Methode.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void ProcessGooglePlayInstallReferrerUrl(string referrerUrl);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      // in actual implementation, the referrer url should be retrieved
      // from the Google Play Install Referrer API.
      var myReferrer = "utm_source=unityTestSource&utm_content=unityTestContent&utm_campaign=unityTestCampaign";
      ADBMobile.ProcessGooglePlayInstallReferrerUrl(myReferrer);
      ```
