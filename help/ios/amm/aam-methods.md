---
description: Hier finden Sie eine Liste der Audience Manager-Methoden, die von der iOS-Bibliothek bereitgestellt werden.
seo-description: Hier finden Sie eine Liste der Audience Manager-Methoden, die von der iOS-Bibliothek bereitgestellt werden.
seo-title: Audience Manager-Methoden
solution: Marketing Cloud, Analytics
title: Audience Manager-Methoden
topic: Entwickler und Implementierung
uuid: 97658 bd 6-4 c 4 f -4875-abe 9-36 dad 4 ec 8 bae
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Audience Manager methods {#audience-manager-methods}

Hier finden Sie eine Liste der Audience Manager-Methoden, die von der iOS-Bibliothek bereitgestellt werden.

Das SDK unterstützt derzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target, Audience Manager und Adobe Experience Platform Identity Service. Die Methoden haben ein der Lösung entsprechendes Präfix und die Manager-Methoden enthalten das Präfix „`audience`audience“.

Wenn Audience Manager in Ihrer JSON-Datei konfiguriert ist, wird ein Signal, das Lebenszyklusmetriken enthält, mit `application:didFinishLaunchingWithOptions:` : gesendet.

* **audienceVisitorProfile**

   Gibt das Besucherprofil zurück, das zuletzt erfasst wurde, und gibt `null` zurück, wenn kein Signal gesendet wurde. Das Besucherprofil wird in `NSUserDefaults` gespeichert und steht so bei jedem Start der App zur Verfügung.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (NSDictionary *) audienceVisitorProfile;
      ```

   * Hier finden Sie das Codebeispiel für dieses Menü:

      ```objective-c
      NSDictionary *profile = [ADBMobile audienceVisitorProfile]; 
      ```

* **audienceDpid** 

   Gibt die aktuelle DPID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +(NSString *) audience Dpid;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSString *currentDpid = [ADBMobileaudience Dpid]; 
      ```

* **audienceDpuuid**

   Gibt die aktuelle DPUUID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +(NSString *) audienceDpuuid;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSString *currentDpuuid = [ADBMobileaudience Dpuuid]; 
      ```

* **audienceSetDpid:&#x200B;dpuuid:**

   Legt die DPID und die DPUUID fest. Nach der Einrichtung werden beide an das jeweilige Signal angehängt.

   * Die **Datenanbieter-ID (DPID)** ist die Partner-ID, die vom Audience Manager zugewiesen wird.
   * Die **Datenanbieter-Unique User-ID (DPUUID)** ist die eindeutige ID des Datenanbieters für den Benutzer.

      >[!IMPORTANT]
      >
      >Vor Version 4.13. x wurde DPUUID nicht automatisch kodiert. Ab Version 4.13.x entschlüsselt das SDK zunächst den übermittelten Wert und verschlüsselt ihn dann neu. Mithilfe dieses Verfahrens wird sichergestellt, dass das SDK die Rückkompatibilität nicht beeinträchtigt.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) audienceSetDpid: (NSString*)   
                      dpiddpuuid:(NSString*)dpuuid;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-
      [ADBMobile audienceSetDpid:@"290"
                        dpuuid:@"99301393920493"];
      ```

* **audienceReset**

   Setzt die Audience Manager-UUID zurück und löscht das aktuelle Besucherprofil.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +(void) audienceReset;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile audienceReset]; 
      ```

* **audienceSignalWithData::&#x200B;callback:**

   Sendet dem Zielgruppen-Management ein Signal mit Eigenschaften und ruft die passenden Segmente ab, die in einem Block-Callback zurückgegeben werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) audienceSignalWithData:(NSDictionary*)data
                            callback:(void(^)(NSDictionary
      *response))callback; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile audienceSignalWithData:traits
                               callback:^(NSDictionary*response){
                                 //do something with returned segments
                               }];
      ```

## Beispiel

```objective-c
// setup your traits dictionary 
NSDictionary *traits = @{@"trait":@"b"}; 
// submit your signal and take action on results 
[ADBMobile audienceSignalWithData:traits  
                         callback:^(NSDictionary *response) { 
                             // do something with visitor segments here 
                             if ([response[@"gender"] isEqualToString:@"male"]) { 
                             // do something with gender  
                             } 
                         }];
```
