---
description: Liste der von der Windows 8.1 Universal App Store-Bibliothek bereitgestellten Audience Manager-Methoden.
solution: Experience Cloud Services,Analytics
title: Audience Manager-Methoden
topic-fix: Developer and implementation
uuid: e39c9c3e-fd53-4b46-8fff-88101a064a9c
exl-id: b10d7274-0fc6-4822-a40b-1192b71592b9
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 46%

---

# Audience Manager-Methoden {#audience-manager-methods}

Liste der von der Windows 8.1 Universal App Store-Bibliothek bereitgestellten Audience Manager-Methoden.

Das SDK unterstützt derzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target und Audience Manager. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Audience Manager-Methoden wird &quot;AudienceManager&quot;vorangestellt.

>[!NOTE]
>
>Wenn Sie winmd-Methoden aus winJS (JavaScript) verwenden, wird bei allen Methoden automatisch der erste Buchstabe kleingeschrieben.

Wenn der Zielgruppen-Manager in Ihrer JSON-Datei konfiguriert ist, wird ein Signal mit Lebenszyklusmetriken mit Ihrem Lebenszyklustreffer gesendet.

* **GetVisitorProfile (winJS: getVisitorProfile)**

   Gibt das zuletzt erfasste Besucherprofil zurück. Rückgabe `null` wenn noch kein Signal gesendet wurde. Das Besucherprofil wird gespeichert in `SharedPreferences` für einfachen Zugriff über mehrere Starts Ihrer App hinweg.

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
