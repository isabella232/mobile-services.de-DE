---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: ADBMobile.cs-Methoden
solution: Experience Cloud
title: ADBMobile.cs-Methoden
uuid: af504934-febd-45d9-81e2-2a310f4c65dc
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
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
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: Wenn die Offline-Verfolgung aktiviert ist, werden die Treffer gespeichert, bis der Datenschutzstatus zu &quot;opt-in&quot;(Zugriffe werden gesendet) oder &quot;opt-out&quot;(Zugriffe werden dann verworfen) geändert wird.

      Ist die Offline-Verfolgung nicht aktiviert, werden die Zugriffe verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird. The default value is set in the [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md) file.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static ADBPrivacyStatus GetPrivacyStatus();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var privacyStatus = ADBMobile.GetPrivacyStatus();
      ```

* **GetUserIdentifier**

   Gibt die benutzerdefinierte Benutzerkennung zurück, wenn eine benutzerdefinierte ID festgelegt wurde. Gibt null zurück, wenn kein benutzerdefinierter Bezeichner festgelegt ist. Der Standardwert lautet `null`.

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

   Gibt dem SDK gegenüber an, dass die App angehalten ist, sodass die Lebenszyklusmetriken ordnungsgemäß berechnet werden. Beispiel: Beim Anhalten wird ein Zeitstempel erfasst, um die Länge der vorherigen Sitzung zu bestimmen. Dadurch wird auch ein Flag gesetzt, damit der Lebenszyklus richtig erkennt, dass die App nicht abstürzt. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void PauseCollectingLifecycleData();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.PauseCollectingLifecycleData();
      ```

* **SetContext (nur Android)**

   Gibt dem SDK gegenüber an, dass der Anwendungskontext aus der aktuellen Aktivität von UnityPlayer festgelegt werden soll.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SetContext();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ADBMobile.SetContext();
      ```

* **SetDebugLogging**

   Legt fest, dass die Voreinstellung für die Debug-Protokollierung aktiviert ist.

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
   * `MOBILE_PRIVACY_STATUS_UNKNOWN`: Wenn die Offline-Verfolgung aktiviert ist, werden die Treffer gespeichert, bis der Datenschutzstatus zu &quot;opt-in&quot;(Zugriffe werden gesendet) oder &quot;opt-out&quot;(Zugriffe werden dann verworfen) geändert wird. Ist die Offline-Verfolgung nicht aktiviert, werden die Zugriffe verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SetPrivacyStatus(ADBPrivacyStatusstatus);
      ```

   * Im Folgenden finden Sie das Codebeispiel für diese Syntax:

      ```java
      ADBMobile.SetPrivacyStatus(ADBMobile.ADBPrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN);
      ```

* **SetUserIdentifier**

   Legt die Benutzerkennung auf userId fest.

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

   Verfolgt einen App-Status mit optionalen Kontextdaten. Statusangaben sind die Ansichten, die in Ihrer App verfügbar sind, z. B. &quot;Titelbildschirm&quot;, &quot;Level 1&quot;, &quot;Pause&quot;usw. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `TrackState`-Aufrufe inkrementieren die Seitenansichten.

   Wenn der Status leer ist, wird er wie *`app name app version (build)`* in Berichten angezeigt. If you see this value in reports, make sure you are setting state in each `TrackState` call.

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

   Verfolgt eine Aktion in der App. Aktionen sind die Vorgänge, die in Ihrer App stattfinden und die Sie messen möchten, z. B. &quot;Todesfälle&quot;, &quot;erzielte Werte&quot;, &quot;Feed-Abonnement&quot;und andere Metriken.

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

   Sendet die aktuellen Koordinaten (Längen- und Breitengrad). Ermittelt außerdem anhand der in der Datei `ADBMobileConfig.json` definierten Zielpunkte (POI), ob der als Parameter angegebene Standort in einem vorhandenen Zielpunkt liegt. Wenn sich die aktuellen Koordinaten innerhalb eines definierten POI befinden, wird eine Kontextdatenvariable ausgefüllt und mit dem TrackLocation-Aufruf gesendet.

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

   Fügt dem Lebenszeitwert des Benutzers einen Wert hinzu.

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

   Übergeben Sie Daten, um die mit der jeweiligen Aktion verknüpften Kontextdaten zu aktualisieren. Die weitergeleiteten Daten werden an die vorhandenen Daten für die jeweilige Aktion angehängt und überschreiben die Daten, wenn derselbe Schlüssel bereits für die Aktion definiert ist.

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

   Mit der Experience Cloud-ID können Sie weitere Kunden-IDs festlegen, die jedem Besucher zugeordnet werden. Die Besucher-API akzeptiert mehrere Kunden-IDs für denselben Besucher zusammen mit einer Kundentypkennung, um den Umfang der verschiedenen Kunden-IDs zu trennen. Diese Methode entspricht setCustomerIDs in der JavaScript-Bibliothek.

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

* **ProcessGooglePlayInstallReferrerUrl** *(nur Android)*

   Geben Sie die Werber-URL, die von einem Aufruf an die Google Play Install Werber API zurückgegeben wird, an diese Methode weiter.

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
