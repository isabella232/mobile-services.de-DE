---
description: Klassen und Methoden, die von der Windows 8.1 Universal App Store-Bibliothek bereitgestellt werden.
seo-description: Klassen und Methoden, die von der Windows 8.1 Universal App Store-Bibliothek bereitgestellt werden.
seo-title: SDK-Methoden
solution: Experience Cloud,Analytics
title: SDK-Methoden
topic: Developer and implementation
uuid: 0f558ff4-73d3-4439-9d51-62fbd74d2cea
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 50%

---


# SDK-Methoden {#sdk-methods}

Klassen und Methoden, die von der Windows 8.1 Universal App Store-Bibliothek bereitgestellt werden.

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
      varADB = ADBMobile;var libVersion = ADB.Config.getVersion(); 
      ```

* **GetPrivacyStatusAsync (winJS: getPrivacyStatusAsync)**

   Gibt die Enum-Darstellung für den Datenschutzstatus des aktuellen Benutzers zurück.

   * `ADBMobilePrivacyStatusOptIn`: Treffer werden umgehend gesendet.
   * `ADBMobilePrivacyStatusOptOut`: werden Treffer verworfen.
   * `ADBMobilePrivacyStatusUnknown` - Wenn Ihre Report Suite zeitstempelfähig ist, werden die Treffer gespeichert, bis der Datenschutzstatus in &quot;opt-in&quot;(Zugriffe werden gesendet) oder &quot;opt-out&quot;(Zugriffe werden dann verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

      The default value is set in the [ADBMobileConfig.json config](/help/windows-appstore/c-configuration/c.json.md) file.

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
   * `ADBMobilePrivacyStatusUnknown` - Wenn Ihre Report Suite zeitstempelfähig ist, werden die Treffer gespeichert, bis der Datenschutzstatus in &quot;opt-in&quot;(Zugriffe werden gesendet) oder &quot;opt-out&quot;(Zugriffe werden dann verworfen) geändert wird. Wenn für Ihre Report Suite keine Zeitstempel aktiviert sind, werden die Treffer verworfen, bis der Datenschutzstatus zu „optedin“ geändert wird.

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

   Gibt die benutzerdefinierte Benutzerkennung zurück, wenn eine benutzerdefinierte ID festgelegt wurde. Gibt null zurück, wenn kein benutzerdefinierter Bezeichner festgelegt ist. Der Standardwert lautet `null`.

   >[!TIP]
   >
   >Wenn Ihre App vom Experience Cloud 3.x auf das 4.x-SDK aktualisiert wird, wird die vorherige ID (benutzerdefinierte oder automatisch generierte) abgerufen und als benutzerdefinierte Benutzerkennung gespeichert. So werden Besucherdaten auch bei Upgrades des SDK beibehalten. For new installations on the 4.x SDK, user identifier is `null` until set.

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

   Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Nutzung aller Lösungen im SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Rufen Sie diese Methode in der `onResume()` Methode in jeder Aktivität Ihrer Anwendung auf, wie im folgenden Beispiel gezeigt. Es wird außerdem empfohlen, die Aktivität oder den Dienst als Kontextobjekt anstelle des globalen Anwendungskontexts zu übergeben.

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

   Gibt dem SDK gegenüber an, dass die App angehalten ist, sodass die Lebenszyklusmetriken ordnungsgemäß berechnet werden. Beispiel: Beim Anhalten wird ein Zeitstempel erfasst, um die Länge der vorherigen Sitzung zu bestimmen. Dadurch wird auch ein Flag gesetzt, damit der Lebenszyklus richtig erkennt, dass die App nicht abstürzt. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/windows-appstore/metrics.md).

   >[!TIP]
   >
   >Rufen Sie diese Methode in den `onPause()` Methoden in den einzelnen Aktivitäten Ihrer Anwendung auf, wie im Beispiel gezeigt. Es wird außerdem empfohlen, die Aktivität oder den Dienst als Kontextobjekt anstelle des globalen Anwendungskontexts zu übergeben.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void PauseCollectingLifecycleData();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      ADB.Config.pauseCollectingLifecycleData();
      ```
