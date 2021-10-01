---
description: Klassen und Methoden, die von der Windows 8.1 Universal App Store-Bibliothek bereitgestellt werden.
solution: Experience Cloud,Analytics
title: SDK-Methoden
topic-fix: Developer and implementation
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2cea
exl-id: c328fd79-6e10-43b7-9d08-8da395098b60
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 51%

---

# SDK-Methoden {#sdk-methods}

Klassen und Methoden, die von der Windows 8.1 Universal App Store-Bibliothek bereitgestellt werden.

>[!TIP]
>
>Wenn Sie `winmd`-Methoden aus winJS (JavaScript) verwenden, wird für alle Methoden automatisch der erste Buchstabe kleingeschrieben.

* **GetVersion (winJS: getVersion)**

   Gibt die aktuelle Version der Adobe Mobile-Bibliothek zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Platform::String ^GetVersion();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **GetPrivacyStatusAsync (winJS: getPrivacyStatusAsync)**

   Gibt die Enum-Darstellung für den Datenschutzstatus des aktuellen Benutzers zurück.

   * `ADBMobilePrivacyStatusOptIn`: Treffer werden umgehend gesendet.
   * `ADBMobilePrivacyStatusOptOut`: werden Treffer verworfen.
   * `ADBMobilePrivacyStatusUnknown` - Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden die Treffer gespeichert, bis der Datenschutzstatus zu &quot;opt-in&quot;(anschließend werden die Treffer gesendet) oder &quot;opt-out&quot;(anschließend werden die Treffer verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

      Der Standardwert wird in der Datei [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md) festgelegt.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<ADBMobilePrivacyStatus> ^getPrivacyStatusAsync(); 
      ```

   * Hier finden Sie Code-Beispiele für diese Methode:

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

* **SetPrivacyStatus (winJS: setPrivacyStatus)**

   Legt für den aktuellen Benutzer den Datenschutzstatus `status` fest. Die folgenden Werte sind zulässig:

   * `ADBMobilePrivacyStatusOptIn`: Treffer werden umgehend gesendet.
   * `ADBMobilePrivacyStatusOptOut`: werden Treffer verworfen.
   * `ADBMobilePrivacyStatusUnknown` - Wenn für Ihre Report Suite Zeitstempel aktiviert sind, werden die Treffer gespeichert, bis der Datenschutzstatus zu &quot;opt-in&quot;(anschließend werden die Treffer gesendet) oder &quot;opt-out&quot;(anschließend werden die Treffer verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

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

* **GetLifetimeValue (winJS: getLifetimeValue)**

   Gibt den Lebenszeitwert für den aktuellen Benutzer zurück. Standard: 0.

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

   Gibt die benutzerdefinierte Benutzer-ID zurück, wenn eine benutzerdefinierte ID festgelegt wurde. Gibt null zurück, wenn keine benutzerdefinierte ID festgelegt ist. Der Standardwert lautet `null`.

   >[!TIP]
   >
   >Wenn für Ihre App ein Upgrade vom Experience Cloud-SDK 3.x auf 4.x vorgenommen wird, wird die vorherige (benutzerdefinierte oder automatisch generierte) ID abgerufen und als benutzerdefinierte Benutzer-ID gespeichert. So werden Besucherdaten auch bei Upgrades des SDK beibehalten. Für neue Installationen für das SDK der Version 4.x lautet die Benutzer-ID `null` , bis sie festgelegt wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Platform::String^GetUserIdentifier();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
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

      ```js
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

      ```js
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

   Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Nutzung aller Lösungen im SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Rufen Sie diese Methode in der `onResume()`-Methode in jeder Aktivität in Ihrer Anwendung auf, wie im folgenden Beispiel gezeigt. Es wird außerdem empfohlen, die Aktivität oder den Dienst als Kontextobjekt anstelle des globalen Anwendungskontexts weiterzugeben.

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

   Gibt dem SDK gegenüber an, dass die App angehalten ist, sodass die Lebenszyklusmetriken ordnungsgemäß berechnet werden. Beispiel: Bei Pause erfasst einen Zeitstempel, mit dem die Dauer der vorherigen Sitzung bestimmt wird. Dadurch wird auch eine Markierung gesetzt, sodass der Lebenszyklus richtig erkennt, dass die App nicht abgestürzt ist. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Rufen Sie diese Methode in den `onPause()`-Methoden in jeder Aktivität in Ihrer Anwendung auf, wie im Beispiel gezeigt. Es wird außerdem empfohlen, die Aktivität oder den Dienst als Kontextobjekt anstelle des globalen Anwendungskontexts weiterzugeben.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
