---
description: Android-Methoden für Xamarin-Komponenten für Experience Cloud-Lösungen mit SDK 4.x.
keywords: Xamarin
solution: Experience Cloud
title: Android-Methoden
uuid: 860af1c4-f57e-4bcb-8308-4e316da9a27b
exl-id: 0de1fa11-37e9-49be-8d42-a13cb4a3f0e3
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '1755'
ht-degree: 68%

---

# Android-Methoden{#android-methods}

Android-Methoden für Xamarin-Komponenten für Experience Cloud-Lösungen mit SDK 4.x.

## Konfigurationsmethoden {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **DebugLogging**

   Gibt die aktuelle Debug-Protokollierungseinstellung zurück und die Standardeinstellung ist &quot;false&quot;.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static Boolean DebugLogging;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      getter: var debuglog = Config.DebugLogging;
      setter: Config.DebugLogging = (Java.Lang.Boolean)true;
      ```

* **LifetimeValue**

   Gibt den Lebenszeitwert für den aktuellen Benutzer zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static BigDecimal LifetimeValue; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
       var lifetimeValue = Config.LifetimeValue;
      ```

* **PrivacyStatus**

   Gibt die Enum-Darstellung für den Datenschutzstatus des aktuellen Benutzers zurück.
   * `ADBMobilePrivacyStatus.OptIn`: Treffer werden umgehend gesendet.
   * `ADBMobilePrivacyStatus.OptOut`: werden Treffer verworfen.
   * `ADBMobilePrivacyStatus.Unknown`: Bei aktivierter Offline-Verfolgung werden die Treffer so lange gespeichert, bis sich der Datenschutzstatus in „opt-in“ (anschließend werden die Treffer gesendet) oder „opt-out“ (anschließend werden die Treffer verworfen) ändert. Ist die Offline-Verfolgung nicht aktiviert, werden die Zugriffe verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird.

   Der Standardwert wird in der Datei [ADBMobileConfig.json](/help/android/configuration/json-config/json-config.md) festgelegt.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static MobilePrivacyStatus PrivacyStatus; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      getter: var privacyStatus = Config.PrivacyStatus; 
      setter: Config.PrivacyStatus = MobilePrivacyStatus.MobilePrivacyStatusUnknown;
      ```


* **UserIdentifier**

   Wenn eine benutzerdefinierte ID festgelegt wurde, wird diese Kennung zurückgegeben. Wenn keine benutzerdefinierte ID festgelegt ist, wird null zurückgegeben. Der Standardwert lautet `null`.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static UserIdentifier();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      getter: var userId = Config.UserIdentifier;
      setter: Config.UserIdentifier = "imBatman";
      ```

* **Version**

   Ruft die Bibliotheksversion ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static string Version;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var version = ADBMobile.Version;
      ```

* **PauseCollectingLifecycleData**

   Gibt dem SDK gegenüber an, dass die App angehalten ist, sodass die Lebenszyklusmetriken ordnungsgemäß berechnet werden. Beispiel: Bei Pause erfasst einen Zeitstempel, mit dem die Dauer der vorherigen Sitzung bestimmt wird. Dadurch wird auch eine Markierung gesetzt, sodass der Lebenszyklus richtig erkennt, dass die App nicht abgestürzt ist. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void PauseCollectingLifecycleData (); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Config.PauseCollectingLifecycleData();
      ```

* **CollectLifecycleData (Activity activity)**

   (4.2 oder höher) Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Verwendung aller Lösungen im SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void collectLifecycleData(Activity activity); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Config.CollectLifecycleData (this);
      ```

* **CollectLifecycleData (Activity activity)**

   (4.2 oder höher) Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Verwendung aller Lösungen im SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void collectLifecycleData(Activity activity, IDictionary<string, Object> context));
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      IDictionary<string, Java.Lang.Object> context = new Dictionary<string, 
      Java.Lang.Object> ();
      context.Add ("key", "value");
      Config.CollectLifecycleData (this, context);
      ```

* **OverrideConfigStream**

   (4.2 oder höher) Ermöglicht das Laden einer anderen `ADBMobile JSON` Konfigurationsdatei beim Start der Anwendung. Die andere Konfiguration wird verwendet, bis die Anwendung geschlossen wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void OverrideConfigStream (Stream stream);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Stream st1 = Assets.Open ("ADBMobileConfig-2.json"); 
      Config.OverrideConfigStream (st1); 
      ```

* **SetLargeIconResourceId(int resourceId)**

   (4.2 oder höher) Legt das große Symbol fest, das für vom SDK erstellte Benachrichtigungen verwendet wird. Dieses Symbol wird als primäres Bild angezeigt, wenn der Benutzer die vollständige Benachrichtigung in der Mitteilungszentrale öffnet.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SetLargeIconResourceId( int resourceId);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Config.SetLargeIconResourceId(R.drawable.appIcon);
      ```

* **SetSmallIconResourceId(int resourceId)**

   (4.2 oder höher) Legt das kleine Symbol fest, das für vom SDK erstellte Benachrichtigungen verwendet wird. Dieses Symbol wird in der Statusleiste angezeigt und ist das sekundäre Bild, das angezeigt wird, wenn der Benutzer die vollständige Benachrichtigung im Benachrichtigungszentrum sieht.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SetSmallIconResourceId( int resourceId); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
       Config.SetSmallIconResourceId(R.drawable.appIcon);
      ```

## Analytics-Methoden {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Gibt die automatisch generierte ID für Analytics zurück. Dies ist eine App-spezifische eindeutige ID, die beim ersten Start generiert und ab diesem Zeitpunkt gespeichert und verwendet wird. Diese ID bleibt zwischen App-Upgrades erhalten und wird bei der Deinstallation entfernt.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static string TrackingIdentifier;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **TrackState**

   Verfolgt einen App-Status mit optionalen Kontextdaten. `States` sind die Ansichten, die in Ihrer App verfügbar sind, z. B. &quot;Titelbildschirm&quot;, &quot;Level 1&quot;, &quot;Pause&quot; usw. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `TrackState`-Aufrufe inkrementieren die Seitenansichten. Wenn der Status leer ist, wird in Berichten als &quot;App Name App Version (Build)&quot;angezeigt. Wenn dieser Wert in Berichten auftritt, stellen Sie sicher, dass Sie den Status in jedem `TrackState` -Aufruf festlegen.

   >[!TIP]
   >
   >Dies ist der einzige Verfolgungsaufruf, bei dem die Seitenansichten inkrementiert werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackState (string state, IDictionary<string, Object> cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object>(); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackState ("stateName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackAction**

   Verfolgt eine Aktion in der App. Bei Aktionen handelt es sich um die Dinge, die in Ihrer App vor sich gehen, die Sie messen möchten, z. B. &quot;Todesfälle&quot;, &quot;Erreichte Stufe&quot;, &quot;Feed-Abonnements&quot;und andere Metriken.

   >[!TIP]
   >
   >
   >Falls Code aktiv ist, während die App im Hintergrund ausgeführt wird (z. B. Datenabruf im Hintergrund), verwenden Sie stattdessen `trackActionFromBackground`.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackAction(string action, IDictionary<string,Object> cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var cdata = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value");
      Analytics.TrackAction ("actionName", (IDictionary<string, 
      Java.Lang.Object>)cdata);
      ```

* **TrackLocation**

   Sendet die aktuellen Koordinaten (Längen- und Breitengrad). Ermittelt außerdem anhand der in der Datei `ADBMobileConfig.json` definierten Zielpunkte (POIs), ob der als Parameter angegebene Standort in einem vorhandenen Zielpunkt liegt. Falls die aktuellen Koordinaten auf einen definierten Zielpunkt passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem `TrackLocation`-Aufruf gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackLocation(Location location, IDictionary<string, Object> cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
       Location loc = new Location(LocationManager.GpsProvider);;
       loc.Latitude = 111; 
       loc.Longitude = 44; 
       loc.Accuracy = 5; 
       Analytics.TrackLocation (loc, null);
      ```

* **TrackBeacon**

   Verfolgt das Eintreten eines Benutzers in den Radius eines Beacons.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackBeacon (string uuid, string major, string minor,  Analytics.BEACON_PROXIMITY prox, IDictionary<string, Object> cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.TrackBeacon ("UUID", "1", "2", 
      Analytics.BEACON_PROXIMITY.ProximityImmediate, null); 
      ```

* **ClearBeacon**

   Löscht die Beacon-Daten, sobald der Benutzer den Radius des Beacons verlässt.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackingClearCurrentBeacon();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.ClearBeacon(); 
      ```

* **TrackLifetimeValueIncrease**

   Erhöht den Lebenszeit-Wert des Benutzers.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackLifetimeValueIncrease (double amount, IDictionary<string,Object> cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.TrackLifetimeValueIncrease(5,null);
      ```

* **TrackTimedActionStart**

   Beginnt eine zeitgesteuerte Aktion mit einer benannten Aktion. Wenn Sie diese Methode für eine bereits gestartete Methode aufrufen, wird die vorherige zeitgesteuerte Aktion überschrieben.

   >[!TIP]
   >
   > Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackTimedActionStart(string action,IDictionary<string, Object> cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Übergeben Sie diesen Wert in Daten, um die Kontextdaten zu aktualisieren, die der gegebenen Aktion zugewiesen sind. Die übergebenen Daten werden an die vorhandenen Daten für die Aktion angehängt und überschreiben die Daten, wenn der Schlüssel bereits für die Aktion definiert ist.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackTimedActionUpdate(string action, IDictionary<string, Object> cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var updatedData = new Dictionary<string, Java.Lang.Object> (); 
      cdata.Add ("key", (Java.Lang.Object)"value"); 
      Analytics.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   Beendet eine zeitgesteuerte Aktion.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void TrackTimedActionEnd(string action,
        Analytics.ITimedActionBlock block);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.TrackTimedActionEnd ("level2", new TimedActionBlock()); 
           class TimedActionBlock: Java.Lang.Object, 
      Analytics.ITimedActionBlock{ 
           public Java.Lang.Object Call (long inAppDuration, long 
      totalDuration IDictionary<string, Java.Lang.Object> contextData){ 
           return Java.Lang.Boolean.True; 
        } 
      }
      ```

* **TrackingTimedActionExists**

   Gibt zurück, ob derzeit eine zeitgesteuerte Aktion ausgeführt wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var level2InProgress = Analytics.TrackingTimedActionExists("level2"); 
      ```

* **SendQueuedHits**

   Erzwingt in der Bibliothek das Senden aller Treffer aus der Offline-Warteschlange, unabhängig von der Anzahl der Treffer, die sich derzeit in der Warteschlange befinden.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SendQueuedHits();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.SendQueuedHits(); 
      ```

* **ClearQueue**

   Löscht alle Zugriffe aus der Offline-Warteschlange.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void ClearQueue(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.ClearQueue(); 
      ```

* **QueueSize**

   Ruft die Anzahl der Treffer ab, die sich derzeit in der Offline-Warteschlange befinden.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static long QueueSize(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var queueSize = Analytics.QueueSize();
      ```

## Experience Cloud-ID-Methoden {#section_157919E46030443DBB5CED60D656AD9F}

* **MarketingCloudId**

   Ruft die Experience Cloud ID vom ID-Service ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static string MarketingCloudId;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var mcid = Visitor.MarketingCloudId;
      ```

* **SyncIdentifiers**

   Mit der Experience Cloud-ID können Sie zusätzliche Kunden-IDs festlegen, die jedem Besucher zugeordnet werden. Die Besucher-API akzeptiert mehrere Kunden-IDs für denselben Besucher sowie eine Kundentypkennung, die den Umfang der einzelnen Kunden-IDs abgrenzt. Diese Methode entspricht `setCustomerIDs` in der JavaScript-Bibliothek.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SyncIdentifiers((IDictionary<string> identifiers);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      IDictionary<string,string> ids = new Dictionary<string, string> ();
      ids.Add ("pushID", ;"value2");
      Visitor.SyncIdentifiers (ids);
      ```

## Target-Methoden {#section_C1E4121CAF9D43538511D857A1F549A7}

* **LoadRequest**

   Sendet eine Anfrage an Ihren konfigurierten Target-Server und gibt den Zeichenfolgenwert des in einem `Action<NSDictionary>` -Rückruf generierten Angebots zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void LoadRequest (TargetLocationRequest request, Target.ITargetCallback callback); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      class TargetBlock: Java.Lang.Object, Target.ITargetCallback{ 
          public void Call (Java.Lang.Object content) 
         { 
          Console.WriteLine (content.ToString()); 
         } 
      } 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
           Target.LoadRequest (req, new TargetBlock()); 
      ```

* **CreateRequest**

   Komfortabler Konstruktor zum Erstellen eines `ADBTargetLocationRequest`-Objekts mit den angegebenen Parametern.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static TargetLocationRequest TargetCreateRequest(string name,string defaultContent,IDictionary<string,string> parameters); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      IDictionary<string, Java.Lang.Object> parameters = new Dictionary> string, Java.Lang.Object> (); 
          parameters.Add ("key1", "value2"); 
      var req = Target.CreateRequest ("AndroidTest", "defGal", parameters); 
      ```

* **CreateOrderConfirmRequest**

   Erstellt ein `ADBTargetLocationRequest`-Objekt.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static TargetLocationRequest TargetCreateRequest (string name, string defaultContent, IDictionary<;string, string> parameters);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      var orderConfirm = Target.CreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **ClearCookies**

   Löscht Target-Cookies aus Ihrer App.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void ClearCookies(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Target.ClearCookies (); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **VisitorProfile**

   Gibt das zuletzt erfasste Besucherprofil zurück. Gibt null zurück, wenn noch kein Signal gesendet wurde. Das Besucherprofil wird in `NSUserDefaults` gespeichert und steht so bei jedem Start der App zur Verfügung.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static IDictionary<string, Object> VisitorProfile; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      NSDictionary profile = AudienceManager.VisitorProfile; 
      ```

* **Dpid**

   Gibt die aktuelle `DPID` zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static string Dpuuid; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      string currentDpid = AudienceManager.Dpid;
      ```

* **Dpuuid**

   Gibt die aktuelle `DPUUID` zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static string AudienceDpuuid; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      string currentDpuuid = AudienceManager.Dpuuid;
      ```

* **AudienceSetDpidAndDpuuid**

   Legt die `dpid` und `dpuuid` fest. Wenn `dpid` und `dpuuid` festgelegt sind, werden sie mit jedem Signal gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void AudienceSetDpidAndDpuuid (string Dpid, String Dpuuid);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      AudienceManager.SetDpidAndDpuuid ("testDpid", "testDpuuid");
      ```

* **SignalWithData**

   Sendet dem Zielgruppen-Management ein Signal mit Eigenschaften und ruft die passenden Segmente ab, die in einem `Action<NSDictionary>` -Rückruf zurückgegeben werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SignalWithData (IDictionary<string, Object> audienceData, AudienceManager.IAudienceManagerCallback callback); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      class AudienceManagerCallback: Java.Lang.Object, 
       AudienceManager.IAudienceManagerCallback{ 
         public void Call (Java.Lang.Object content) 
        {
          Console.WriteLine (content.ToString()); 
        }
      }
      IDictionary<string, Java.Lang.Object> traits = new Dictionary<string, 
      Java.Lang.Object> (); 
         traits.Add ("trait", "b");
      AudienceManager.SignalWithData (traits, new AudienceManagerCallback());
      ```

* **Zurücksetzen**

   Setzt den Zielgruppen-Manager `UUID` zurück und löscht das aktuelle Besucherprofil.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void Reset ();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
       AudienceManager.Reset ();
      ```

## Video {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

Weitere Informationen zu Video Analytics finden Sie unter [Video Analytics](/help/android/analytics-main/video-qs.md).

* **MediaSettings**

   Gibt ein `MediaSettings`-Objekt mit den angegebenen Parametern zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static MediaSettings SettingsWith (string name, double length, string playerName, string playerID);  
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      MediaSettings settings = Media.SettingsWith("name1", 10, "playerName1", "playerID1");
      ```

* **AdSettingsWith**

   Gibt ein `MediaSettings`-Objekt für die Verfolgung einer Videoanzeige zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static MediaSettings AdSettingsWith ( string name, double length, 
        string playerName, string parentName, string parentPod, 
      double parentPodPosition, string CPM); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      MediaSettings adSettings = Media.AdSettingsWith ("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1"); 
      ```

* **Öffnen**

   Öffnet ein `ADBMediaSettings`-Objekt für die Verfolgung.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void Open (MediaSettings settings, Media.IMediaCallback callback);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      MediaSettings settings = Media.SettingsWith ("name1", 10, "playerName1", "playerID1"); 
         Media.Open (settings, new MediaCallback()); 
         class MediaCallback: Java.Lang.Object, Media.IMediaCallback{ 
      public void Call (Java.Lang.Object content) 
      {
      }
      }
      ```

* **Schließen**

   Schließt das Medienelement mit dem Namen name.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void Close(string name);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.Close (settings.Name); 
      ```

* **Play**

   Gibt das Medienelement mit dem Namen name mit dem Versatz offset (in Sekunden) wieder.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void Play ( string name, double offset); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.Play (settings.Name, 0); 
      ```

* **Abgeschlossen**

   Kennzeichnet das Medienelement am angegebenen offset (in Sekunden) als abgeschlossen.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void Complete (string name, double offset); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.Complete (settings.Name, 5); 
      ```

* **Anhalten**

   Benachrichtigt das Medienmodul darüber, dass das Video mit dem Versatz Offset beendet oder angehalten wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void Stop ( string name, double offset); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.Stop (settings.Name, 3);
      ```

* **Klick**

   Benachrichtigt das Medienmodul darüber, dass das Medienelement angeklickt wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void Click ( string name, double offset); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.Click (settings.Name, 3); 
      ```

* **Verfolgen**

   Sendet einen Verfolgungsaktionsaufruf (keine Seitenansicht) für den aktuellen Medienstatus.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void Track ( string name, NSDictionary data); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.Track (settings.Name, null); 
      ```
