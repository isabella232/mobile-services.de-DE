---
description: Klassen und Methoden, die von der universellen Windows-Plattform-Bibliothek bereitgestellt werden.
solution: Experience Cloud Services,Analytics
title: SDK-Methoden
topic-fix: Developer and implementation
uuid: e3aa41d6-7bc0-4208-a662-12907c209a77
exl-id: 0aac477c-074d-457c-b117-bb205119c475
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 64%

---

# SDK-Methoden {#sdk-methods}

Klassen und Methoden, die von der universellen Windows-Plattform-Bibliothek bereitgestellt werden.

>[!TIP]
>
>Wann Sie konsumieren `winmd` -Methoden aus winJS (JavaScript), haben alle Methoden automatisch ihren ersten Buchstaben in Kleinbuchstaben.

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

      Der Standardwert wird im `ADBMobileConfig.json` Konfigurationsdatei. Weitere Informationen finden Sie unter [Konfigurationsdatei &quot;ADBMobileConfig.json&quot;](/help/universal-windows/c-configuration/c.json.md).

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
   * `DBMobilePrivacyStatusUnknown` - Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden die Treffer gespeichert, bis der Datenschutzstatus zu &quot;opt-in&quot;(Treffer werden gesendet) oder &quot;opt-out&quot;(Treffer werden verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

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

   Gibt die benutzerdefinierte Benutzer-ID zurück, wenn eine benutzerdefinierte ID festgelegt wurde. Rückgabe `null` wenn keine benutzerdefinierte ID festgelegt ist.
Der Standardwert lautet `null`.

   >[!IMPORTANT]
   >
   >Wenn für Ihre App ein Upgrade vom Experience Cloud-SDK 3.x auf 4.x vorgenommen wird, wird der vorherige (benutzerdefinierte oder automatisch generierte) ID-Dienst abgerufen und als benutzerdefinierte Benutzer-ID gespeichert. So werden Besucherdaten auch bei Upgrades des SDK beibehalten. Bei neuen Installationen der SDK-Version 4.x lautet die Benutzer-ID `null`, bis sie festgelegt wird.

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

   Legt die Debug-Protokollierungseinstellung auf `debugLogging` fest. Die Debug-Protokollierung funktioniert nur bei Verwendung der Debug-Version der Bibliothek. Diese Einstellung wird von der Release-Version ignoriert.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void SetDebugLogging(bool debugLogging);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      ADB.Config.setDebugLogging(true);
      ```

* **CollectLifecycleData (winJS: collectLifecycleData)**

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

   Gibt dem SDK gegenüber an, dass die App angehalten ist, sodass die Lebenszyklusmetriken ordnungsgemäß berechnet werden. Beispiel: Bei Pause erfasst einen Zeitstempel, mit dem die Dauer der vorherigen Sitzung bestimmt wird. Dadurch wird auch eine Markierung gesetzt, sodass der Lebenszyklus richtig erkennt, dass die App nicht abgestürzt ist. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/universal-windows/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData(); 
      ```
