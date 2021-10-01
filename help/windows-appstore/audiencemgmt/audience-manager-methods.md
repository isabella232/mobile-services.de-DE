---
description: Liste der Audience Manager-Methoden, die von der Windows 8.1 Universal App Store-Bibliothek bereitgestellt werden.
solution: Experience Cloud,Analytics
title: Audience Manager-Methoden
topic-fix: Developer and implementation
uuid: e39c9c3e-fd53-4b46-8fff-88101a064a9c
exl-id: b10d7274-0fc6-4822-a40b-1192b71592b9
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 46%

---

# Audience Manager-Methoden {#audience-manager-methods}

Liste der Audience Manager-Methoden, die von der Windows 8.1 Universal App Store-Bibliothek bereitgestellt werden.

Das SDK unterstützt derzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target und Audience Manager. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Audience Manager-Methoden wird &quot;AudienceManager&quot;vorangestellt.

>[!NOTE]
>
>Wenn Sie winmd-Methoden aus winJS (JavaScript) verwenden, wird bei allen Methoden automatisch der erste Buchstabe kleingeschrieben.

Wenn der Zielgruppen-Manager in Ihrer JSON-Datei konfiguriert ist, wird ein Signal mit Lebenszyklusmetriken mit Ihrem Lebenszyklustreffer gesendet.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Gibt das zuletzt erfasste Besucherprofil zurück. Gibt `null` zurück, wenn noch kein Signal gesendet wurde. Das Besucherprofil wird in `SharedPreferences` gespeichert und steht so bei jedem Start Ihrer App zur Verfügung.

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

   Sendet dem Audience Manager ein Signal mit Eigenschaften und ruft die passenden Segmente ab, die in einem Block-Callback zurückgegeben werden.

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
