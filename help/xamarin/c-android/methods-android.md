---
description: Android methods for Xamarin components for Experience Cloud solutions 4.x SDK.
keywords: Xamarin
seo-description: Android methods for Xamarin components for Experience Cloud solutions 4.x SDK.
seo-title: Android-Methoden
solution: Marketing Cloud,Developer
title: Android-Methoden
uuid: 860af1c4-f57e-4bcb-8308-4e316da9a27b
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '1767'
ht-degree: 66%

---


# Android-Methoden{#android-methods}

Android-Methoden für Xamarin-Komponenten für Experience Cloud Solutions 4.x SDK.

## Konfigurationsmethoden {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **DebugLogging**

   Gibt die aktuelle Einstellung für die Debug-Protokollierung zurück, die Standardeinstellung ist &quot;false&quot;.

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

   The default value is set in the [ADBMobileConfig.json](/help/android/configuration/json-config/json-config.md) file.

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

   Wenn eine benutzerdefinierte ID festgelegt wurde, gibt diese ID zurück. Wenn kein benutzerdefinierter Bezeichner festgelegt ist, gibt null zurück. Der Standardwert lautet `null`.

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

   Gibt dem SDK gegenüber an, dass die App angehalten ist, sodass die Lebenszyklusmetriken ordnungsgemäß berechnet werden. Beispiel: Beim Anhalten wird ein Zeitstempel erfasst, um die Länge der vorherigen Sitzung zu bestimmen. Dadurch wird auch ein Flag gesetzt, damit der Lebenszyklus richtig erkennt, dass die App nicht abstürzt. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void PauseCollectingLifecycleData (); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Config.PauseCollectingLifecycleData();
      ```

* **CollectLifecycleData (Aktivität-Aktivität)**

   (4.2 oder höher) Gibt dem SDK an, dass Lebenszyklusdaten für die Verwendung in allen Lösungen des SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void collectLifecycleData(Activity activity); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Config.CollectLifecycleData (this);
      ```

* **CollectLifecycleData (Activity activity)**

   (4.2 or later) Indicates to the SDK that lifecycle data should be collected for use across all solutions in the SDK. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

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

   (4.2 oder höher) Ermöglicht das Laden einer anderen `ADBMobile JSON` Konfigurationsdatei beim Beginn der Anwendung. Die andere Konfiguration wird verwendet, bis die Anwendung geschlossen wird.

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

   (4.2 oder höher) Legt das kleine Symbol fest, das für vom SDK erstellte Benachrichtigungen verwendet wird. Dieses Symbol wird in der Statusleiste angezeigt und ist das sekundäre Bild, das angezeigt wird, wenn der Benutzer die vollständige Benachrichtigung im Benachrichtigungscenter sieht.

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

   Gibt die automatisch generierte ID für Analytics zurück. Hierbei handelt es sich um eine App-spezifische eindeutige ID, die beim ersten Start generiert und ab diesem Zeitpunkt gespeichert und verwendet wird. Diese ID bleibt zwischen den App-Aktualisierungen erhalten und wird bei der Deinstallation entfernt.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static string TrackingIdentifier;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Var trackingId = Analytics.TrackingIdentifier
      ```

* **TrackState**

   Verfolgt einen App-Status mit optionalen Kontextdaten. `States` sind die Ansichten, die in Ihrer App verfügbar sind, wie &quot;Titelbildschirm&quot;, &quot;Level 1&quot;, &quot;Pause&quot;usw. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `TrackState`-Aufrufe inkrementieren die Seitenansichten. Wenn der Status leer ist, wird in Berichten als &quot;App-Name-App-Version (Build)&quot;angezeigt. If you see this value in reports, make sure you are setting state in each `TrackState` call.

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

   Verfolgt eine Aktion in der App. Actions are the things that happen in your app that you want to measure, such as &quot;deaths&quot;, &quot;level gained&quot;, &quot;feed subscriptions&quot;, and other metrics.

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

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Übergeben Sie Daten, um die Kontextdaten zu aktualisieren, die der angegebenen Aktion zugeordnet sind. Die weitergeleiteten Daten werden an die vorhandenen Daten für die jeweilige Aktion angehängt und überschreiben die Daten, wenn derselbe Schlüssel bereits für die Aktion definiert ist.

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

   Retrieves the number of hits that are currently in the offline queue.

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

   Mit der Experience Cloud-ID können Sie weitere Kunden-IDs festlegen, die jedem Besucher zugeordnet werden. Die Besucher-API akzeptiert mehrere Kunden-IDs für denselben Besucher sowie eine Kundentypkennung, die den Umfang der einzelnen Kunden-IDs abgrenzt. Diese Methode entspricht `setCustomerIDs` in der JavaScript-Bibliothek.

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

   Convenience constructor to create an `ADBTargetLocationRequest` object with the given parameters.

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

   Löscht Zielgruppen-Cookies aus Ihrer App.

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

   Legt die `dpid` und `dpuuid`fest. Wenn `dpid` und `dpuuid` werden sie mit jedem Signal gesendet.

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

* **Zurücksetzen**

   Resets audience manager `UUID` and purges current visitor profile.

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

* **Klicken Sie auf**

   Benachrichtigt das Medienmodul darüber, dass das Medienelement angeklickt wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void Click ( string name, double offset); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.Click (settings.Name, 3); 
      ```

* **verfolgen**

   Sendet einen Verfolgungsaktionsaufruf (keine Seitenansicht) für den aktuellen Medienstatus.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void Track ( string name, NSDictionary data); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.Track (settings.Name, null); 
      ```
