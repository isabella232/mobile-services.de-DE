---
description: Im Folgenden finden Sie eine Liste von Methoden, die durch die Android-Bibliothek bereitgestellt werden.
keywords: android; library; mobile; sdk
seo-description: Im Folgenden finden Sie eine Liste von Methoden, die durch die Android-Bibliothek bereitgestellt werden.
seo-title: Konfigurationsmethoden
solution: Marketing Cloud, Analytics
title: Konfigurationsmethoden
topic: Entwickler und Implementierung
uuid: 663 aeb 6 c -1 b 97-4 a 3 a -8 c 0 e-dd 4 c 2 ec 28 c 01
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Configuration methods{#configuration-methods}

Im Folgenden finden Sie eine Liste von Methoden, die durch die Android-Bibliothek bereitgestellt werden.

## Initial configuration {#section_9169243ECC4744A899A8271F92090ECD}

Die folgende Methode muss einmal in der Methode `onCreate` Ihrer Hauptaktivität aufgerufen werden:

* `setContext`
Hier finden Sie ein Code-Beispiel für diese Methode:

   ```java
    @Override
    public void onCreate(BundlesavedInstanceState){
      super.onCreate(savedInstanceState)
      setContentView(R.layout.main);
      Config.setContext(this.getApplicationContext());
    }
   ````


## SDK settings (Config Class) {#section_C1EB977043C04D2B93E5A63DB72828B6}

* **registerAdobeDataCallback**

   * Registriert ein Objekt, das die `AdobeDataCallback`-Schnittstelle implementiert. The overwritten "call" method will be invoked with a `Config.MobileDataEvent` value and the associated data in a `Map<String, Object>` for the triggering event. Weitere Informationen darüber, welche Ereignisse diesen Rückruf auslösen, finden Sie unter *mobiledataeventenum* unten in diesem Thema.

      >[!TIP]
      >
      >Für diese Methode ist Version 4.9.0 oder höher erforderlich.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void registerAdobeDataCallback(final AdobeDataCallback&amp;nbsp;callback);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
        Config.registerAdobeDataCallback(new Config.AdobeDataCallback() {
          @Override
          public void call(Config.MobileDataEvent event, Map<String, Object> contextData) {
              // handle each event type accordingly 
              if (event == Config.MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL) {
                   // do something with acquisition data found in contextData parameter
                   HashMap<String, Object> acquisitionData = new HashMap<String, Object>(contextData);
              }
          }
      });
      ```

* **getVersion**

   * Gibt die aktuelle Version der Adobe Mobile-Bibliothek zurück.
   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static String getVersion();
      ```

   * Hier finden Sie ein Codebeispiel für diese Methode:

      ```java
      String libraryVersion = Config.getVersion(); 
      ```

* **getPrivacyStatus**

   * Gibt die Enum-Darstellung für den Datenschutzstatus des aktuellen Benutzers zurück.

      Dies sind die Werte zum Datenschutzstatus:

      * `MOBILE_PRIVACY_STATUS_OPT_IN`, wo die Treffer sofort gesendet werden.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`, wo die Elemente verworfen werden.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`: Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden Treffer gespeichert, bis sich der Datenschutzstatus zu „opt-in“ (Treffer werden gesendet) oder „opt-out“ (Treffer werden verworfen) ändert.

         Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird. Der Standardwert wird in der Datei `ADBMobileConfig.json` festgelegt.
   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static MobilePrivacyStatus getPrivacyStatus(); 
      ```

   * Hier finden Sie ein Codebeispiel für diese Methode:

      ```java
      MobilePrivacyStatus privacyStatus Config.getPrivacyStatus();
      ```


* **setPrivacyStatus**

   * Legt für den aktuellen Benutzer den Datenschutzstatus `status` fest.

      Sie können den Datenschutzstatus auf einen der folgenden Werte festlegen:
      * `MOBILE_PRIVACY_STATUS_OPT_IN`, wo die Treffer sofort gesendet werden. Diese Treffer werden sofort gesendet.
      * `MOBILE_PRIVACY_STATUS_OPT_OUT`, wo die Elemente verworfen werden. Diese Treffer werden verworfen.
      * `MOBILE_PRIVACY_STATUS_UNKNOWN`: Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden Treffer gespeichert, bis sich der Datenschutzstatus zu „opt-in“ (Treffer werden gesendet) oder „opt-out“ (Treffer werden verworfen) ändert.
Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird.
   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void setPrivacyStatus(MobilePrivacyStatus status); 
      ```

   * Hier finden Sie ein Codebeispiel für diese Methode:

      ```java
      Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
      ```


* **getLifetimeValue**

   * Gibt den Lebenszeitwert für den aktuellen Benutzer zurück. Der Standardwert lautet `0`.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static BigDecimal getLifetimeValue();
      ```

   * Hier finden Sie ein Codebeispiel für diese Methode:

      ```java
      BigDecimal currentLifetimeValue Config.getLifetimeValue(); 
      ```

* **getUserIdentifier**

   * Wenn eine anwenderdefinierte ID festgelegt wurde, wird die anwenderdefinierte Benutzer-ID zurückgegeben. Wenn keine anwenderdefinierte ID festgelegt wurde, wird `null` zurückgegeben. Der Standardwert lautet `null`.

      >[!TIP]
      >
      >Wenn Ihre App-Upgrades von Experience Cloud 3. x auf das 4. x-SDK aktualisiert werden, wird die vorherige oder automatisch erzeugte Besucher-ID abgerufen und als benutzerdefinierte Benutzer-ID gespeichert. Dadurch werden Besucherdaten zwischen SDK-Upgrades beibehalten. Bei Neuinstallationen mit SDK 4.x ist die Benutzer-ID `null`.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static String&amp getUserIdentifier();
      ```

   * Hier finden Sie das Codebeispiel für diese Methode:

      ```java
      String userId = Config.getUserIdentifier();
      ```

* **setUserIdentifier**

   * Legt die Benutzerkennung auf `identifier` fest.
   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void setUserIdentifer(String identifier);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Config.setUserIdentifier("billybob"); 
      ```

* **getDebugLogging**

   * Gibt die aktuelle Vorgabe für die Debug-Protokollierung zurück. Der Standardwert lautet `false`.
   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static Boolean getDebugLogging(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Boolean debugging = Config.getDebugLogging(); 
      ```

* **setDebugLogging**
   * Legt die Debug-Protokollierungseinstellung auf `debugLogging` fest. 
   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void setDebugLogging(Boolea debugLogging);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Config.setDebugLogging(true);
      ```

* **collectLifecycleData**
   * Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Nutzung aller Lösungen im SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/configuration/methods.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void collectLifecycleData(final Activity activity,final Map<String, Object>contextData); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      @Override
      protectedvoid  onResume()  {
        super.onResume();
        Config.collectLifecycleData(this);
        } 
      ```

      Mit zusätzlichen Kontextdaten:

      ```java
      @Override
      public  void  onResume()  {
        HashMap<String, Object> contextData = new HashMap<String, Object>();
        contextData.put("myapp.category", "Game");        Config.collectLifecycleData(this, contextData);} 
      ```

* **collectLifecycleData (Activity activity)**

   * (**Version 4.2 oder höher**) Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Nutzung aller Lösungen im SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).
   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void collectLifecycleData(final Activity activity);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      @Overrideprotected void onResume() {
        super.onResume()
        // assume being called in an Activity class Config.collectLifecycleData(this);
        } 
        ```
      
* **pauseCollecting&#x200B;LifecycleData**

   * Gibt dem SDK gegenüber an, dass die App angehalten ist, sodass die Lebenszyklusmetriken ordnungsgemäß berechnet werden. Beispiel: `onPause` erfasst einen Zeitstempel, mit dem die Dauer der vorherigen Sitzung ermittelt wird. Hiermit wird außerdem eine Markierung gesetzt, so dass im Lebenszyklus ersichtlich wird, dass die App nicht abgestürzt ist. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void pauseCollectingLifecycleData(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      @Override
      protected void onPause() {
        super.onPause();
        Config.pauseCollectingLifecycleData();
      } 
      ```

* **setSmallIconResourceId(int resourceId)**

   * (**Version 4.2 oder höher**) Legt das kleine Symbol fest, das für die vom SDK erstellten Benachrichtigungen verwendet wird. Dieses Symbol wird in der Statusleiste angezeigt. Es wird als sekundäres Bild angezeigt, wenn der Benutzer die vollständige Benachrichtigung im Notification Center öffnet.
   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **setLargeIconResourceId(int resourceId)**

   * (**Version 4.2 oder höher**) Legt das große Symbol fest, das für die vom SDK erstellten Benachrichtigungen verwendet wird. Dieses Symbol wird als primäres Bild angezeigt, wenn der Benutzer die vollständige Benachrichtigung im Notification Center öffnet.
   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void setLargeIconResourceId(final int  resourceId);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```Java
      Config.setLargeIconResourceId(R.drawable.appIcon);
      ```

* **overrideConfigStream(InputStream configInput)**

   * (**Version 4.2 oder höher**) Ermöglicht Ihnen das Laden einer anderen ADBMobile-JSON-Konfigurationsdatei, wenn die Anwendung startet. Die andere Konfiguration wird verwendet, bis die Anwendung geschlossen wird.
   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void overrideConfigStream(final InputStream configInput);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
       try {
          InputStream configInput = getAssets().open("ExampleJSONFile.json") 
          Config.overrideConfigStream(configInput)
          } catch (IOException ex) { 
          //do something with the exception if needed
      }
      ```

* **setPushIdentifier**

   * Legt das Geräte-Token für Push-Benachrichtigungen fest.
   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void setPushIdentifier(final String registrationId); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      ...// note the code to retreive the push token must run in the background
      InstanceID instanceID= InstanceID.getInstance(getApplicationContext());String token=instanceID.getToken("835015092242", GoogleCloudMessaging.INSTANCE_ID_SCOPE null);Config.setPushIdentifier(token);
      ...
      ```

* **submitAdvertisingIdentifierTask**

   * Stellt dem SDK ein Callable bereit, das die Zeichenfolge der Advertising-ID der Google Play Services zurückgibt. Das SDK führt diese Aufgabe in einem Hintergrund-Thread aus und legt eine interne Variable für die Advertising-ID fest, die auf dem vom Callable zurückgegebenen Wert basiert.

      >[!IMPORTANT]
      > 
      >If you want to use the Advertising Identifier in Acquisition or Lifecycle, call it before calling `Config.collectLifecycleData`.

      * Hier finden Sie die Syntax für diese Methode:

         ```java
         public static void submitAdvertisingIdentifierTask(final Callable<String> task); 
         ```

      * Hier finden Sie ein Code-Beispiel für diese Methode:

         ```java
         @Override
         public void  onResume() {
             super.onResume();
             final  Callable<String>; task = new Callable<String>(){
                 @Override
                 public String call() throws Exception {
                    AdvertisingIdClient.Info idInfo;
                    String adid = null;
                    Context appContext = CLASSNAME.this.getApplicationContext();
                    try {
                         idInfo = AdvertisingIdClient.getAdvertisingIdInfo(appContext);
                         if (idInfo != null) { 
                             adid = idInfo.getId();
                         } 
                    } catch  (Exception ex) {
                        Log.e("Error",  ex.getLocalizedMessage());
                    }
                    return  adid;
                 }
           };
           Config.submitAdvertisingIdentifierTask(task); 
           Config.collectLifecycleData(this);
         }
         ```


## AdobeDataCallback-Schnittstelle {#section_600A63B3136F47DCB928071485C5117C}

```java
public interface AdobeDataCallback {  
    void call(MobileDataEvent event, Map<String, Object> contextData);  
} 
```

## MobileDataEvent Enum {#section_92732814141646E294782BC9020367EB}

```java
public enum MobileDataEvent {  
    MobileDataEvent.MOBILE_EVENT_LIFECYCLE, // triggers on a lifecycle hit  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL, // triggers on a app install that has acquisition data  
    MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH // triggers on launch when the device previously installed via acquisition  
}
```
