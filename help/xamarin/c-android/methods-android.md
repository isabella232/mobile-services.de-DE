---
description: Android-Methoden für Xamarin-Komponenten für das Experience Cloud-Lösungen-4.x-SDK
keywords: Xamarin
seo-description: Android-Methoden für Xamarin-Komponenten für das Experience Cloud-Lösungen-4.x-SDK
seo-title: Android methods
solution: Marketing Cloud,Developer
title: Android methods
uuid: 860af1c4-f57e-4bcb-8308-4e316da9a27b
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Android methods{#android-methods}

Android-Methoden für Xamarin-Komponenten für das Experience Cloud-Lösungen-4.x-SDK

## Configuration methods {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **DebugLogging**

   Returns the current debug logging preference, and the default is false.

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
   * `ADBMobilePrivacyStatus.OptIn` - Treffer werden sofort gesendet.
   * `ADBMobilePrivacyStatus.OptOut` - werden Treffer verworfen.
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

   If a custom identifier has been set, returns this identifier. Wenn keine benutzerdefinierte ID festgelegt ist, gibt null zurück. Der Standardwert lautet `null`.

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

   Gibt dem SDK gegenüber an, dass die App angehalten ist, sodass die Lebenszyklusmetriken ordnungsgemäß berechnet werden. Beispiel: Beim Anhalten einen Zeitstempel erfassen, mit dem die Dauer der vorherigen Sitzung ermittelt wird. Hiermit wird außerdem ein Flag gesetzt, sodass im Lebenszyklus ersichtlich wird, dass die App nicht abgestürzt ist. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void PauseCollectingLifecycleData (); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Config.PauseCollectingLifecycleData();
      ```

* **CollectLifecycleData (Activity-Aktivität)**

   (4.2 oder höher) Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Nutzung aller Lösungen im SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void collectLifecycleData(Activity activity); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Config.CollectLifecycleData (this);
      ```

* **CollectLifecycleData (Activity-Aktivität)**

   (4.2 oder höher) Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Nutzung aller Lösungen im SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

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

   (4.2 or later) Lets you load a different `ADBMobile JSON` config file when the application starts. Die andere Konfiguration wird verwendet, bis die Anwendung geschlossen wird.

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

   (4.2 oder höher) Legt das große Symbol fest, das für vom SDK erstellte Benachrichtigungen verwendet wird. Dieses Symbol ist das primäre Bild, das angezeigt wird, wenn der Benutzer die vollständige Benachrichtigung im Benachrichtigungscenter sieht.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SetLargeIconResourceId( int resourceId);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Config.SetLargeIconResourceId(R.drawable.appIcon);
      ```

* **SetSmallIconResourceId(int resourceId)**

   (4.2 oder höher) Legt das kleine Symbol fest, das für vom SDK erstellte Benachrichtigungen verwendet wird. Dieses Symbol wird in der Statusleiste angezeigt und ist das sekundäre Bild, das angezeigt wird, wenn der Benutzer die vollständige Benachrichtigung im Benachrichtigungscenter sieht.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void SetSmallIconResourceId( int resourceId); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
       Config.SetSmallIconResourceId(R.drawable.appIcon);
      ```

## Analytics methods {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Gibt die automatisch erzeugte ID für Analytics zurück. Hierbei handelt es sich um eine App-spezifische eindeutige ID, die beim ersten Start generiert und ab diesem Zeitpunkt gespeichert und verwendet wird. Diese ID bleibt zwischen App-Aktualisierungen erhalten und wird bei der Deinstallation entfernt.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static string TrackingIdentifier;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **TrackState**

   Verfolgt einen App-Status mit optionalen Kontextdaten. `States`entsprechen den verfügbaren Ansichten in der App, z. B. „Titelbild“, „Level 1“ oder „Pause“. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `TrackState`-Aufrufe inkrementieren die Seitenansichten. Wenn der Status leer ist, wird „AppName AppVersion (Build)“ in Berichten aufgeführt. Wenn dieser Wert in einem Bericht auftritt, müssen Sie den Status in jedem `TrackState`-Aufruf festlegen.

   >[!TIP]
   >
   >Dies ist der einzige Verfolgungsaufruf, durch den die Seitenansichten inkrementiert werden.

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

   Verfolgt eine Aktion in der App. Aktionen sind die Vorgänge in der App, die gemessen werden sollen, z. B. „Tode“, „Level bestanden“, „Feed-Abonnements“ und weitere Metriken.

   >[!TIP]
   >
   >
   >If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

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

   Sendet die aktuellen Koordinaten (Längen- und Breitengrad). Also uses points of interest defined in the `ADBMobileConfig.json` file to determine whether the location that was provided as a parameter is in any of your POIs. Falls die aktuellen Koordinaten auf einen definierten Zielpunkt passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem `TrackLocation`-Aufruf gesendet.

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

   * Im Folgenden finden Sie ein Codebeispiel für diese Methode:

      ```java
      Analytics.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Übergibt Daten, mit denen die Kontextdaten für die vorliegende Aktion aktualisiert werden sollen. Die übergebenen Daten werden an die vorhandenen Daten für die Aktion angehängt. Falls ein Schlüssel bereits für die Aktion definiert ist, werden die vorhandenen Daten dieses Schlüssels überschrieben.

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

   Erzwingt, dass die Bibliothek alle Treffer in der Offline-Warteschlange sendet, unabhängig davon, wie viele Treffer sich derzeit in der Warteschlange befinden.

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

## Experience Cloud ID methods {#section_157919E46030443DBB5CED60D656AD9F}

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

   Mit der Experience Cloud ID können Sie weitere Kunden-IDs festlegen, die den einzelnen Besuchern zugewiesen werden. Die Besucher-API akzeptiert mehrere Kunden-IDs für denselben Besucher sowie eine Kundentypkennung, die den Umfang der einzelnen Kunden-IDs abgrenzt. Diese Methode entspricht `setCustomerIDs` in der JavaScript-Bibliothek.

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

   Sends a request to your configured Target server and returns the string value of the offer generated in a `Action<NSDictionary>` callback.

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

   Vordefinierter Konstruktor zum Erzeugen eines `ADBTargetLocationRequest`-Objekts mit den angegebenen Parametern.

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

   Erstellt eine `ADBTargetLocationRequest`.

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

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **VisitorProfile**

   Gibt das zuletzt erfasste Besucherprofil zurück. Gibt null zurück, falls noch kein Signal übertragen wurde. Das Besucherprofil wird in `NSUserDefaults` gespeichert und steht so bei jedem Start der App zur Verfügung.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static IDictionary<string, Object> VisitorProfile; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      NSDictionary profile = AudienceManager.VisitorProfile; 
      ```

* **Dpid**

   Returns the current `DPID`.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static string Dpuuid; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      string currentDpid = AudienceManager.Dpid;
      ```

* **Dpuuid**

   Returns the current `DPUUID`.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static string AudienceDpuuid; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      string currentDpuuid = AudienceManager.Dpuuid;
      ```

* **AudienceSetDpidAndDpuuid**

   Legt die `dpid` und `dpuuid`fest. If `dpid` and `dpuuid` are set, they are sent with each signal.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void AudienceSetDpidAndDpuuid (string Dpid, String Dpuuid);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      AudienceManager.SetDpidAndDpuuid ("testDpid", "testDpuuid");
      ```

* **SignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>` callback.

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

* **Rücksetzen**

   Setzt die `UUID` des Zielgruppen-Managers zurück und löscht das aktuelle Besucherprofil.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void Reset ();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
       AudienceManager.Reset ();
      ```

## Video {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

Weitere Informationen zu Video Analytics finden Sie unter [Videoanalyse](/help/android/analytics-main/video-qs.md).

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

* **Close**

   Schließt das angegebene Medienelement.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void Close(string name);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.Close (settings.Name); 
      ```

* **Abspielen**

   Gibt das angegebene Medienelement am angegebenen Offset (in Sekunden) wieder.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void Play ( string name, double offset); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.Play (settings.Name, 0); 
      ```

* **Abgeschlossen**

   Kennzeichnet das Medienelement am angegebenen Offset (in Sekunden) als abgeschlossen.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void Complete (string name, double offset); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.Complete (settings.Name, 5); 
      ```

* **Stop**

   Benachrichtigt das Medienmodul, dass das Video am angegebenen Offset beendet oder angehalten wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void Stop ( string name, double offset); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.Stop (settings.Name, 3);
      ```

* **Klicken**

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
