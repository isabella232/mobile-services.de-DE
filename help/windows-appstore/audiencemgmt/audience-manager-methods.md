---
description: Liste der von der Windows 8.1 Universal App Store-Bibliothek bereitgestellten Audience Manager-Methoden.
seo-description: List of Audience Manager methods provided by the Windows 8.1 Universal App Store library.
seo-title: Audience Manager-Methoden
solution: Marketing Cloud,Analytics
title: Audience Manager-Methoden
topic: Developer and implementation
uuid: e39c9c3e-fd53-4b46-8fff-88101a064a9c
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 45%

---


# Audience Manager-Methoden {#audience-manager-methods}

List of Audience Manager methods provided by the Windows 8.1 Universal App Store library.

Das SDK unterstützt derzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Zielgruppe und Audience Manager. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Audience Manager methods are prefixed with &quot;AudienceManager.&quot;

>[!NOTE]
>
>When you consume winmd methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

Wenn Audience Manager in Ihrer JSON-Datei konfiguriert ist, wird ein Signal mit Lebenszyklusmetriken mit Ihrem Lebenszyklustreffer gesendet.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Gibt das zuletzt erfasste Besucherprofil zurück. Returns `null` if no signal has been submitted yet. Visitor profile is saved in `SharedPreferences` for easy access across multiple launches of your app.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **GetDpid (winJS: getDpid)**

   Gibt die aktuelle DPID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Platform::String ^GetDpid();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile; 
      var dpid = ADB.AudienceManager.getDpid();
      ```

* **GetDpuuid (winJS: getDpuuid)**

   Gibt die aktuelle DPUUID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Platform::String ^GetDpuuid();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile; 
      var dpuuid = ADB.AudienceManager.getDpuuid();
      ```

* **SetDpidAndDpuuid (winJS: setDpidAndDpuuid)**

   Legt die DPID und die DPUUID fest. Wenn DPID und DPUUID festgelegt sind, werden sie mit jedem Signal gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **SignalWithData (winJS: signalWithData)**

   Sends Audience Manager a signal with traits and get the matching segments returned in a block callback.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> > ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^data);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile; 
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b"; 
      ADB.AudienceManager.signalWithData(traits).then(function(visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      }); 
      ```

