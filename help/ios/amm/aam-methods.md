---
description: Hier finden Sie eine Liste der Audience Manager-Methoden, die von der iOS-Bibliothek bereitgestellt werden.
solution: Experience Cloud,Analytics
title: Audience Manager-Methoden
topic-fix: Developer and implementation
uuid: 97658bd6-4c4f-4875-abe9-36dad4ec8bae
exl-id: b843a52f-2b83-4e19-9f43-895bd582d4ef
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 100%

---

# Audience Manager-Methoden {#audience-manager-methods}

Hier finden Sie eine Liste der Audience Manager-Methoden, die von der iOS-Bibliothek bereitgestellt werden.

Das SDK unterstützt zurzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target, Audience Manager und Identity-Dienst für Adobe Experience Platform. Die Methoden haben ein der Lösung entsprechendes Präfix und die Manager-Methoden enthalten das Präfix „`audience`audience“.

Wenn Audience Manager in Ihrer JSON-Datei konfiguriert ist, wird ein Signal, das Lebenszyklusmetriken enthält, mit `application:didFinishLaunchingWithOptions:` : gesendet.

* **audienceVisitorProfile**

   Gibt das Besucherprofil zurück, das zuletzt erfasst wurde, und gibt `null` zurück, wenn kein Signal gesendet wurde. Das Besucherprofil wird in `NSUserDefaults` gespeichert und steht so bei jedem Start der App zur Verfügung.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (NSDictionary *) audienceVisitorProfile;
      ```

   * Hier finden Sie ein Code-Beispiel für dieses Menü:

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

   Legt die DPID und die DPUUID fest. Wenn sie festgelegt sind, werden beide an jedes Signal angehängt.

   * Die **DPID (Data Provider ID (DPID) = Datenanbieter-ID)** ist die vom Audience Manager zugewiesene Datenpartner-ID.
   * Die **DPUUID (Data Provider Unique User ID = eindeutige Benutzer-ID des Datenanbieters)** ist die eindeutige ID des Datenanbieters für den Benutzer.

      >[!IMPORTANT]
      >
      >Vor Version 4.13.x wurde die DPUUID nicht automatisch verschlüsselt. Ab Version 4.13.x entschlüsselt das SDK zuerst den übergebenen Wert und verschlüsselt diesen Wert dann erneut. Dieser Prozess stellt sicher, dass das SDK die Abwärtskompatibilität nicht beeinträchtigt.

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
