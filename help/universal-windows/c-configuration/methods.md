---
description: Klassen und Methoden, die von der universellen Windows-Plattform-Bibliothek bereitgestellt werden.
seo-description: Klassen und Methoden, die von der universellen Windows-Plattform-Bibliothek bereitgestellt werden.
seo-title: SDK-Methoden
solution: Marketing Cloud,Analytics
title: SDK-Methoden
topic: Entwickler und Implementierung
uuid: e3aa41d6-7bc0-4208-a662-12907c209a77
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# SDK methods {#sdk-methods}

Klassen und Methoden, die von der universellen Windows-Plattform-Bibliothek bereitgestellt werden.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

* **GetVersion (winJS: getVersion)**

   Gibt die aktuelle Version der Adobe Mobile-Bibliothek zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;var libVersion = ADB.Config.getVersion();
      ```

* **GetPrivacyStatusAsync (winJS: getPrivacyStatusAsync)**

   Gibt die Enum-Darstellung für den Datenschutzstatus des aktuellen Benutzers zurück.

   * `ADBMobilePrivacyStatusOptIn` - Hits are sent immediately.
   * `ADBMobilePrivacyStatusOptOut` - Treffer werden verworfen.
   * `ADBMobilePrivacyStatusUnknown`: Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden Treffer gespeichert, bis sich der Datenschutzstatus zu „optedin“ (Treffer werden gesendet) oder „optedout“ (Treffer werden verworfen) ändert. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

      The default value is set in the `ADBMobileConfig.json` config file. Weitere Informationen finden Sie in der Konfigurationsdatei [ADBMobileConfig.json](/help/universal-windows/c-configuration/c.json.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * Hier sind die Codebeispiele für diese Methode:

      **C Scharf**

      ```csharp
      public enum class ADBMobilePrivacyStatus : int { ADBMobilePrivacyStatusOptIn = 1, 
      ADBMobilePrivacyStatusOptOut = 2, 
      ADBMobilePrivacyStatusUnknown = 3};
      ```

      **JavaScript**

      ```javascript
      var ADB = ADBMobile;
      var status;
      ADB.Config.getPrivacyStatusAsync.then(function(privacyStatus) {
        status = privacyStatus;}
      );
      ```

* **SetPrivacyStatus (winJS: setPrivacyStatus)**

   Legt für den aktuellen Benutzer den Datenschutzstatus `status` fest. Die folgenden Werte sind zulässig:
   * `ADBMobilePrivacyStatusOptIn` - Treffer werden sofort gesendet.
   * `ADBMobilePrivacyStatusOptOut` - werden Treffer verworfen.
   * `DBMobilePrivacyStatusUnknown` - Wenn Ihre Report Suite zeitstempelfähig ist, werden die Treffer gespeichert, bis der Datenschutzstatus in "opt-in"(Treffer werden gesendet) oder "opt-out"(Treffer werden verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

      * Hier finden Sie die Syntax für diese Methode:

         ```csharp
         static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
         ```

      * Hier sind die Codebeispiele für diese Methode:

         **C-scharf**

         ```csharp
         public enum class ADBMobilePrivacyStatus : int { 
           ADBMobilePrivacyStatusOptIn = 1, 
           ADBMobilePrivacyStatusOptOut = 2
           ADBMobilePrivacyStatusUnknown = 3
         };
         ```

         **JavaScript**

         ```js
         var ADB = ADBMobile;
         ADB.Config.setPrivacyStatus (ADB.ADBMobilePrivacyStatus.adbmobilePrivacyStatusOptIn
         );
         ```

* **GetLifetimeValue (winJS: getLifetimeValue)**

   Gibt den Lebenszeitwert für den aktuellen Benutzer zurück. Der Standardwert lautet `0`.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static float GetLifetimeValue(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      var ltv = ADB.Config.getLifetimeValue();
      ```

* **GetUserIdentifier (winJS: getUserIdentifier)**

   Gibt die benutzerdefinierte Benutzerkennung zurück, sofern eine benutzerdefinierte Kennung festgelegt wurde. Returns `null` if a custom identifier is not set.
Der Standardwert lautet `null`.

   >[!IMPORTANT]
   >
   >Wenn Ihre App vom Experience Cloud-SDK 3.x auf das SDK 4.x aktualisiert, wird der vorherige ID-Dienst (benutzerdefiniert oder automatisch generiert) abgerufen und als benutzerdefinierte Benutzerkennung gespeichert. So werden Besucherdaten auch bei Upgrades des SDK beibehalten. Bei neuen Installationen der SDK-Version 4.x lautet die Benutzer-ID `null`, bis sie festgelegt wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Platform::String ^GetUserIdentifier(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```csharp
      var ADB = ADBMobile;
      var userId = ADB.Config.getUserIdentifier(); 
      ```

* **SetUserIdentifier (winJS: setUserIdentifier)**

   Legt die Benutzerkennung auf `identifier` fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void SetUserIdentifier(Platform::String ^userIdentifier); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      var ADB = ADBMobile;
      ADB.Config.setUserIdentifier("someUserId");
      ```

* **GetDebugLogging (winJS: getDebugLogging)**

   Gibt die aktuelle Vorgabe für die Debug-Protokollierung zurück. Der Standardwert lautet `false`.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static bool GetDebugLogging();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```javascript
      var ADB = ADBMobile;
      var logging = ADB.Config.getDebugLogging();
      ```

* **SetDebugLogging (winJS: setDebugLogging)**

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

* **CollectLifecycleData (winJS: collectionLifecycleData)**

   Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Nutzung aller Lösungen im SDK erfasst werden sollen. For more information, see  [Lifecycle metrics](/help/universal-windows/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void CollectLifecycleData();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      ADB.Config.collectLifecycleData();
      ```

* **PauseCollecting &#x200B; LifecycleData (winJS: pauseCollecting &#x200B; LifecycleData)**

   Gibt dem SDK gegenüber an, dass die App angehalten ist, sodass die Lebenszyklusmetriken ordnungsgemäß berechnet werden. Beispiel: Beim Anhalten einen Zeitstempel erfassen, mit dem die Dauer der vorherigen Sitzung ermittelt wird. Hiermit wird außerdem ein Flag gesetzt, sodass im Lebenszyklus ersichtlich wird, dass die App nicht abgestürzt ist. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/universal-windows/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```
