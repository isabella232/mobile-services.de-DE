---
description: Classes and methods provided by the Universal Windows Platform library.
seo-description: Klassen und Methoden, die von der universellen Windows-Plattformbibliothek bereitgestellt werden.
seo-title: SDK methods
solution: Marketing Cloud,Analytics
title: SDK-Methoden
topic: Developer and implementation
uuid: e3aa41d6-7bc0-4208-a662-12907c209a77
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 62%

---


# SDK methods {#sdk-methods}

Klassen und Methoden, die von der universellen Windows-Plattformbibliothek bereitgestellt werden.

>[!TIP]
>
>Wenn Sie Methoden aus winJS (JavaScript) verwenden, wird bei allen Methoden automatisch der erste Buchstabe verringert. `winmd`

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

   * `ADBMobilePrivacyStatusOptIn` - Treffer werden umgehend gesendet.
   * `ADBMobilePrivacyStatusOptOut` - Treffer werden verworfen.
   * `ADBMobilePrivacyStatusUnknown`: Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden Treffer gespeichert, bis sich der Datenschutzstatus zu „optedin“ (Treffer werden gesendet) oder „optedout“ (Treffer werden verworfen) ändert. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

      The default value is set in the `ADBMobileConfig.json` config file. Weitere Informationen finden Sie in der Konfigurationsdatei [ADBMobileConfig.json](/help/universal-windows/c-configuration/c.json.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus>
      ^getPrivacyStatusAsync();
      ```

   * Hier finden Sie Code-Beispiele für diese Methode:

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
   * `ADBMobilePrivacyStatusOptIn`: Treffer werden umgehend gesendet.
   * `ADBMobilePrivacyStatusOptOut`: werden Treffer verworfen.
   * `DBMobilePrivacyStatusUnknown` - Wenn Ihre Report Suite zeitstempelfähig ist, werden die Treffer gespeichert, bis der Datenschutzstatus in &quot;opt-in&quot;(Treffer werden gesendet) oder &quot;opt-out&quot;(Treffer werden verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

      * Hier finden Sie die Syntax für diese Methode:

         ```csharp
         static void SetPrivacyStatus(ADBMobilePrivacyStatus status);
         ```

      * Hier finden Sie Code-Beispiele für diese Methode:

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

   Gibt die benutzerdefinierte Benutzerkennung zurück, wenn eine benutzerdefinierte ID festgelegt wurde. Returns `null` if a custom identifier is not set.
Der Standardwert lautet `null`.

   >[!IMPORTANT]
   >
   >Wenn Ihre App vom Experience Cloud 3.x auf das 4.x-SDK aktualisiert wird, wird der vorherige ID-Dienst (benutzerdefiniert oder automatisch generiert) abgerufen und als benutzerdefinierte Benutzerkennung gespeichert. So werden Besucherdaten auch bei Upgrades des SDK beibehalten. Bei neuen Installationen der SDK-Version 4.x lautet die Benutzer-ID `null`, bis sie festgelegt wird.

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

   Legt die Debug-Protokollierungseinstellung auf `debugLogging` fest. Die Debug-Protokollierung funktioniert nur, wenn die Debug-Version der Bibliothek verwendet wird. Diese Einstellung wird in der Release-Version ignoriert.

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

   Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Nutzung aller Lösungen im SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/universal-windows/metrics.md).

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

   Gibt dem SDK gegenüber an, dass die App angehalten ist, sodass die Lebenszyklusmetriken ordnungsgemäß berechnet werden. For example, on pause collects a timestamp to determine previous session length. Dadurch wird auch ein Flag gesetzt, damit der Lebenszyklus richtig erkennt, dass die App nicht abstürzt. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/universal-windows/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```
