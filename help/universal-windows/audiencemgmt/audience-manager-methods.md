---
description: Liste von Audience Manager-Methoden, die von der universellen Windows-Plattformbibliothek bereitgestellt werden.
seo-description: Liste von Audience Manager-Methoden, die von der universellen Windows-Plattformbibliothek bereitgestellt werden.
seo-title: Audience Manager-Methoden
solution: Experience Cloud,Analytics
title: Audience Manager-Methoden
topic: Developer and implementation
uuid: efbe8f33-7f53-40a6-b7aa-a36ac718c047
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 43%

---


# Audience Manager-Methoden{#audience-manager-methods}

Liste von Audience Manager-Methoden, die von der universellen Windows-Plattformbibliothek bereitgestellt werden.

Das SDK unterstützt derzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Zielgruppe und Audience Manager. Methods are prefixed according to the solution. Audience Manager methods are prefixed with `AudienceManager`.

>[!TIP]
>
>Wenn Sie Methoden aus winJS (JavaScript) verwenden, wird bei allen Methoden automatisch der erste Buchstabe verringert. `winmd`

Wenn Audience Manager in Ihrer JSON-Datei konfiguriert ist, wird ein Signal mit Lebenszyklusmetriken mit Ihrem Lebenszyklustreffer gesendet.

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
