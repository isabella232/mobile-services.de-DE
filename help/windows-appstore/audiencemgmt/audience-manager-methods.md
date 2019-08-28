---
description: Hier finden Sie eine Liste der Audience Manager-Methoden, die durch die Windows 8.1 Universal App Store-Bibliothek bereitgestellt werden.
seo-description: Hier finden Sie eine Liste der Audience Manager-Methoden, die durch die Windows 8.1 Universal App Store-Bibliothek bereitgestellt werden.
seo-title: Audience Manager-Methoden
solution: Marketing Cloud, Analytics
title: Audience Manager-Methoden
topic: Entwickler und Implementierung
uuid: e 39 c 9 c 3 e-fd 53-4 b 46-8 fff -88101 a 064 a 9 c
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Audience Manager methods {#audience-manager-methods}

Hier finden Sie eine Liste der Audience Manager-Methoden, die durch die Windows 8.1 Universal App Store-Bibliothek bereitgestellt werden.

Das SDK unterstützt zurzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target und Audience Manager. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Audience Manager-Methoden ist „AudienceManager“ als Präfix vorangestellt.

>[!NOTE]
>
>Wenn Sie Winmd-Methoden aus winjs (javascript) verbrauchen, erhalten alle Methoden automatisch ihren ersten Buchstaben.

Wenn Audience Manager in Ihrer JSON-Datei konfiguriert ist, wird ein Signal mit Lebenszyklusmetriken mit Ihrem Lebenszyklustreffer gesendet.

* **Getvisitorprofile (winjs: Getvisitorprofile)**

   Gibt das zuletzt erfasste Besucherprofil zurück. Gibt `null` zurück, falls noch kein Signal übertragen wurde. Das Besucherprofil wird in `SharedPreferences` gespeichert und steht so bei jedem Start der Anwendung zur Verfügung.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static fWindows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^GetVisitorProfile();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile; 
      var profile = ADB.AudienceManager.getVisitorProfile();
      ```

* **Getdpid (winjs: Getdpid)**

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

* **Getdpuuid (winjs: Getdpuuid)**

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

* **Setdpidanddpuuid (winjs: Setdpidanddpuuid)**

   Legt die DPID und die DPUUID fest. Wenn die DPID und die DPUUID festgelegt sind, werden sie mit jedem Signal gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void SetDpidAndDpuuid(Platform::String ^dpid, Platform::String ^dpuuid); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile; 
      ADB.AudienceManager.setDpidAndDpuuid("newDpid", "newDpuuid");
      ```

* **Signalwithdata (winjs: Signalwithdata)**

   Sendet Audience Manager ein Signal mit Eigenschaften und ruft die passenden Segmente ab, die in einem Blockrückruf zurückgegeben werden.

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

