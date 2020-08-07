---
description: List of Audience Manager methods provided by the Universal Windows Platform library.
seo-description: List of Audience Manager methods provided by the Universal Windows Platform library.
seo-title: Audience Manager-Methoden
solution: Marketing Cloud,Analytics
title: Audience Manager-Methoden
topic: Developer and implementation
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 43%

---


# Audience Manager-Methoden{#audience-manager-methods}

List of Audience Manager methods provided by the Universal Windows Platform library.

The SDK currently has support for multiple Adobe Experience Cloud Solutions, including Analytics, Target, and Audience Manager. Methods are prefixed according to the solution. Audience Manager methods are prefixed with `AudienceManager`.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

If audience manager is configured in your JSON file, a signal that contains lifecycle metrics is sent in with your lifecycle hit.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Gibt das zuletzt erfasste Besucherprofil zurück. Returns `null` if no signal has been submitted yet. Visitor profile is saved in `SharedPreferences` for easy access across multiple launches of your app.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^GetVisitorProfile();
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

   Sendet Audience Management ein Signal mit Eigenschaften und ruft die passenden Segmente in einem Blockrückruf zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static 
      Windows::Foundation::IAsyncOperation<Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^> ^SignalWithData(Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object> ^data);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      var traits = new Windows.Foundation.Collections.PropertySet(); 
      traits["trait"] = "b";
      ADB.AudienceManager.signalWithData(traits).then(function (visitorProfile) { 
        // segments come back here in "visitorProfile", normally found in the "segs" object of your json 
      });
      ```
