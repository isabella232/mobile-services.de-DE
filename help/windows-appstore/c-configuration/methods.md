---
description: Klassen und Methoden der Windows 8.1 Universal App Store-Bibliothek.
seo-description: Klassen und Methoden der Windows 8.1 Universal App Store-Bibliothek.
seo-title: SDK-Methoden
solution: Marketing Cloud, Analytics
title: SDK-Methoden
topic: Entwickler und Implementierung
uuid: 0 f 558 ff 4-73 d 3-4439-9 d 51-62 fbd 74 d 2 cea
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

Klassen und Methoden der Windows 8.1 Universal App Store-Bibliothek.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **Getversion (winjs: Getversion)**

   Gibt die aktuelle Version der Adobe Mobile-Bibliothek zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **Getprivacystatusasync (winjs: Getprivacystatusasync)**

   Gibt die Enum-Darstellung für den Datenschutzstatus des aktuellen Benutzers zurück.

   * `ADBMobilePrivacyStatusOptIn` - Treffer werden sofort gesendet.
   * `ADBMobilePrivacyStatusOptOut` - werden Treffer verworfen.
   * `ADBMobilePrivacyStatusUnknown`: Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden Treffer so lange gespeichert, bis der Datenschutzstatus in „opt-in“ (Treffer werden gesendet) oder „opt-out“ (Treffer werden verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

      The default value is set in the [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md) file.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus> ^getPrivacyStatusAsync(); 
      ```

   * Hier finden Sie die Codebeispiele für diese Methode:

      ```csharp
      public enum class ADBMobilePrivacyStatus : int  {
        ADBMobilePrivacyStatusOptIn = 1, 
        ADBMobilePrivacyStatusOptOut =  2,
        ADBMobilePrivacyStatusUnknown = 3
      };
      ```

      ```js
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
      status = privacyStatus;
      }); 
      ```

* **Setprivacystatus (winjs: Setprivacystatus)**

   Legt für den aktuellen Benutzer den Datenschutzstatus `status` fest. Die folgenden Werte sind zulässig:

   * `ADBMobilePrivacyStatusOptIn` - Treffer werden sofort gesendet.
   * `ADBMobilePrivacyStatusOptOut` - werden Treffer verworfen.
   * `ADBMobilePrivacyStatusUnknown`: Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden Treffer so lange gespeichert, bis der Datenschutzstatus in „opt-in“ (Treffer werden gesendet) oder „opt-out“ (Treffer werden verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```csharp
      public enum class ADBMobilePrivacyStatus : int {
        ADBMobilePrivacyStatusOptIn = 1,
        ADBMobilePrivacyStatusOptOut = 2,
        ADBMobilePrivacyStatusUnknown = 3
        }; 
      ```

      ```js
      var ADB = ADBMobile;
      ADB.Config.setPrivacyStatus(ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn); 
      ```

* **Getlifetimevalue (winjs: Getlifetimevalue)**

   Gibt den Lebenszeitwert für den aktuellen Benutzer zurück. Die Standardeinstellung ist „0“.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static float GetLifetimeValue();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
       var ADB = ADBMobile;
       var ltv = ADB.Config.getLifetimeValue(); 
      ```

* **Getuseridentifier (winjs: Getuseridentifier)**

   Gibt die benutzerdefinierte Benutzerkennung zurück, sofern eine benutzerdefinierte Kennung festgelegt wurde. Gibt null zurück, wenn keine benutzerdefinierte Kennung festgelegt wurde. Der Standardwert lautet `null`.

   >[!TIP]
   >
   >Wenn Ihre App-Upgrades vom Experience Cloud 3. x auf 4. x-SDK aktualisiert werden, wird die vorherige ID (entweder benutzerdefiniert oder automatisch generiert) abgerufen und als benutzerdefinierte Benutzer-ID gespeichert. So werden Besucherdaten auch bei Upgrades des SDK beibehalten. Bei neuen Installationen der SDK-Version 4.x lautet die Benutzerkennung `null`, bis sie festgelegt wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **Setuseridentifier (winjs: Setuseridentifier)**

   Legt die Benutzerkennung auf `identifier` fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId"); 
      ```

* **Getdebuglogging (winjs: Getdebuglogging)**

   Gibt die aktuelle Vorgabe für die Debug-Protokollierung zurück. Der Standardwert lautet `false`.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static bool GetDebugLogging(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging(); 
      ```

* **Setdebuglogging (winjs: Setdebuglogging)**

   Legt die Debug-Protokollierungseinstellung auf `debugLogging` fest. Debug-Protokollierung funktioniert nur, wenn Sie die Debugging-Version der Bibliothek verwenden. Von der Release-Version wird diese Einstellung ignoriert.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void SetDebugLogging(bool debugLogging); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true); 
      ```

* **Collectlifecycledata (winjs: Collectlifecycledata)**

   Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Nutzung aller Lösungen im SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Invoke this method in the `onResume()` method in each Activity inside of your application, as shown in the following example. Wir empfehlen weiterhin, die Aktivität bzw. den Dienst als das Kontextobjekt und nicht als globalen Applikationskontext weiterzugeben.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void CollectLifecycleData();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData(); 
      ```

* **Pausecollectinglifecycledata (winjs: Pausecollectinglifecycledata)**

   Gibt dem SDK gegenüber an, dass die App angehalten ist, sodass die Lebenszyklusmetriken ordnungsgemäß berechnet werden. Beispiel: Beim Anhalten einen Zeitstempel erfassen, mit dem die Dauer der vorherigen Sitzung ermittelt wird. Hiermit wird außerdem ein Flag gesetzt, sodass im Lebenszyklus ersichtlich wird, dass die App nicht abgestürzt ist. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Invoke this method in the `onPause()` methods in each Activity inside Your application, as shown in the example. Wir empfehlen weiterhin, die Aktivität bzw. den Dienst als das Kontextobjekt und nicht als globalen Applikationskontext weiterzugeben.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
