---
description: Hier finden Sie einige Informationen zum Messen von Videos in iOS mithilfe der Meilenstein-Videomessung.
seo-description: Hier finden Sie einige Informationen zum Messen von Videos in iOS mithilfe der Meilenstein-Videomessung.
seo-title: Video Analytics
solution: Experience Cloud,Analytics
title: Videoanalyse
topic-fix: Developer and implementation
uuid: d75fa415-78f6-4f50-a563-76949f040138
exl-id: d4d11ca0-1280-49db-8983-5b6d83856482
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 100%

---

# Video Analytics  {#video-analytics}

Hier finden Sie einige Informationen zum Messen von Videos in iOS mithilfe der Meilenstein-Videomessung.

>[!TIP]
>
>Während der Videowiedergabe werden diesem Dienst häufige Heartbeat-Aufrufe gesendet, um die wiedergegebene Zeit zu messen. Diese Heartbeat-Aufrufe werden alle 10 Sekunden gesendet. Dies führt zu detaillierten Videointeraktionsmetriken und genaueren Video-Fallout-Berichten. Weitere Informationen finden Sie unter [Audio- und Videomessung in Adobe Analytics](https://docs.adobe.com/content/help/de-DE/media-analytics/using/media-overview.html).

Der allgemeine Prozess zur Videomessung ist für alle Plattformen sehr ähnlich. Hier finden Sie eine allgemeine Übersicht der Entwickleraufgaben samt Code-Beispielen.

## Player-Ereignisse Analytics-Variablen zuordnen {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

In der folgenden Tabelle finden Sie die Mediendaten, die an Analytics gesendet werden. Verwenden Sie Verarbeitungsregeln, um die Kontextdaten einer Analytics-Variablen zuzuordnen.

* **a.media.name**

   (Erforderlich) Erfasst den in der Implementierung angegeben Videonamen, wenn sich ein Besucher das Video auf irgendeine Weise ansieht. Sie können für diese Variable Klassifizierungen hinzufügen.

   (Optional) Die Variable „Custom Insight“ enthält Informationen zu Videopfaden.

   * Variablentyp: eVar
   * Standardgültigkeit: Besuch
   * Custom Insight (s.prop, für den Videopfad verwendet)

* **a.media.name**

   (Optional) Bietet Informationen zur Videopfadsetzung. Der Pfad muss für diese Variable von der Kundenunterstützung aktiviert werden.

   * Variablentyp: Custom Insight (benutzerspezifischer Insight-Bericht) (s.prop)
   * Ereignistyp: Benutzerspezifischer Insight-Bericht (s.prop)

* **a.media.segment**

   (Erforderlich) Erfasst Videosegmentdaten, einschließlich Segmentname und Reihenfolge, in der das Segment im Video erscheint. Diese Variable wird gefüllt, indem Sie die Variable `segmentByMilestones` beim automatischen Verfolgen von Player-Ereignissen aktivieren oder indem Sie einen benutzerspezifischen Segmentnamen beim manuellen Verfolgen der Player-Ereignisse festlegen. Beispiel: Wenn ein Besucher das erste Segment in einem Video ansieht, kann SiteCatalyst Folgendes in der Segment-eVar erfassen: `1:M:0-25`.

   Die Standardmethode zur Videodatenerfassung erfasst Daten an folgenden Punkten:

   * Videostart (play)
   * Segmentstart
   * Videoende (Stopp)

   Analytics zählt die erste Segmentansicht am Beginn des Segments, wenn der Besucher zu schauen beginnt. Nachfolgende Segmentansichten bei Segmentbeginn.

   * Variablentyp: eVar
   * Standardgültigkeit: Seitenansicht


* **a.contentType**

   Erfasst Daten zum Typ des Inhalts, der von einem Besucher angesehen wird. Treffer, die durch Videomessung gesendet werden, erhalten den Content-Typ `video` Diese Variable muss nicht ausschließlich für das Video-Tracking reserviert werden. Wenn andere Content-Typen der Inhaltsberichte dieselbe Variable verwenden, können Sie die Verteilung der Besucher auf die verschiedenen Inhaltstypen analysieren. Sie könnten z. B. andere Content-Typen mit Werten wie „article“ oder „product page“ über diese Variable mit Tags versehen. Im Hinblick auf die Videomessung können Sie über den Content-Typ Videobesucher identifizieren und somit Videokonversionsraten berechnen.

   * Variablentyp: eVar
   * Standardgültigkeit: Seitenansicht

* **a.media.timePlayed**

   Gibt in Sekunden an, wie lange ein Video seit dem letzten Datenerfassungsprozess (Bildanforderung) angesehen wurde.

   * Variablentyp: Ereignis
   * Typ: Zähler

* **a.media.view**

   Gibt an, dass ein Besucher einen Teil eines Videos betrachtet hat. Es werden jedoch keine Informationen zu der Länge oder dem Ausschnitt des vom Besucher angesehenen Videos bereitgestellt.

   * Variablentyp: Ereignis
   * Typ: Zähler

* **a.media.segmentView**

   Gibt an, dass ein Besucher einen Teil eines Videosegments betrachtet hat. Es werden jedoch keine Informationen zu der Länge oder dem Ausschnitt des vom Besucher angesehenen Videos bereitgestellt.

   * Variablentyp: Ereignis
   * Typ: Zähler

* **a.media.complete**

   Gibt an, dass ein Besucher ein Video vollständig angesehen hat. Standardmäßig wird das complete-Ereignis 1 Sekunde vor dem Ende des Videos gemessen. Bei der Implementierung können Sie festlegen, wie viele Sekunden vor dem Ende des Videos eine Ansicht als vollständig betrachtet werden soll. Bei Live-Videos und anderen Streams ohne definiertes Ende können Sie einen benutzerdefinierten Punkt angeben, um die Vollständigkeit zu messen, z. B. nach einer bestimmten Wiedergabedauer.

   * Variablentyp: Ereignis
   * Typ: Zähler

## Medieneinstellungen konfigurieren {#section_929945D4183C428AAF3B983EFD3E2500}

Konfigurieren Sie ein `ADBMediaSettings`-Objekt mit den gewünschten Einstellungen zum Verfolgen des Videos:

```objective-c
ADBMediaSettings *mediaSettings = [ADBMobile mediaCreateSettingsWithName:MEDIA_NAME  
length:MEDIA_LENGTH playerName:PLAYER_NAME playerID:PLAYER_ID]; 
 
// milestone tracking. Use either standard milestones (percentage of total length) 
// or offset milestones (seconds elapsed from the beginning of the video) 
mediaSettings.milestones = @"25,50,75"; 
mediaSettings.segmentByMilestones = YES; 
 
mediaSettings.offsetMilestones = @"60,120"; 
mediaSettings.segmentByOffsetMilestones = YES; 
 
// seconds tracking - sends a hit every x seconds 
mediaSettings.trackSeconds = 30; // sends a hit every 30 seconds 
 
// open the video 
[ADBMobile mediaOpenWithSettings:mediaSettings callback:nil]; 
 
// You are now ready to play the video, for example, [movieViewController.moviePlayer play]; 
// Note the mediaPlay, mediaStop and mediaClose methods are called in the 
// event handlers described in the next section
```

## Player-Ereignisse verfolgen {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Zum Messen der Videowiedergabe müssen die Methoden `mediaPlay`, `mediaStop` und `mediaClose` zu den entsprechenden Zeiten aufgerufen werden. Wenn beispielsweise der Player angehalten wird, muss `mediaStop` aufgerufen werden. `mediaPlay` wird aufgerufen, wenn die Wiedergabe gestartet oder fortgesetzt wird.

Im folgenden Beispiel wird das Konfigurieren von Benachrichtigungen und das Aufrufen der Medienmethoden zum Messen des Videos gezeigt:

```objective-c
// configure notifications for when the video is finished, and when the 
media playback state changes 
 
- (void) configureNotifications:(MPMoviePlayerController *) movieController { 
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaFinishedCallback:) 
  name: MPMoviePlayerPlaybackDidFinishNotification 
  object: movieController]; 
  
 [[NSNotificationCenter defaultCenter] 
  addObserver: self 
  selector: @selector(mediaPlaybackChangedCallback:) 
  name: MPMoviePlayerPlaybackStateDidChangeNotification 
  object: movieController]; 
} 
 
// define your notification callbacks. 
 
- (void) mediaFinishedCallback: (NSNotification*) notification { [ADBMobile mediaClose:MEDIA_NAME];} 
 
- (void) mediaPlaybackChangedCallback: (NSNotification*) notification { 
 MPMoviePlayerController *mediaController = notification.object; 
 if (mediaController.playbackState == MPMoviePlaybackStatePlaying) { 
  [ADBMobile mediaPlay:MEDIA_NAME offset: isnan(mediaController.currentPlaybackTime) ? 0.0 : mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingBackward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateSeekingForward) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStatePaused) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateInterrupted) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
 else if (mediaController.playbackState == MPMoviePlaybackStateStopped) { 
  [ADBMobile mediaStop:MEDIA_NAME offset:mediaController.currentPlaybackTime]; 
 } 
}
```

## Klassen {#section_16838332727348F990305C0C6B0D795C}

### Klasse: ADBMediaSettings

```objective-c
bool segmentByMilestones; 
bool segmentByOffsetMilestones; 
double length; 
NSString *channel; 
NSString *name; 
NSString *playerName; 
NSString *playerID; 
NSString *milestones; 
NSString *offsetMilestones; 
NSUInteger trackSeconds; 
NSUInteger completeCloseOffsetThreshold; 
// settings used for ad tracking. For  
bool isMediaAd; 
double parentPodPosition; 
NSString *CPM; 
NSString *parentName; 
NSString *parentPod; 
```

### Klasse: ADBMediaState

```objective-c
bool ad; 
bool clicked; 
bool complete; 
bool eventFirstTime; 
double length; 
double offset; 
double percent; 
double segmentLength; 
double timePlayed; 
double timePlayedSinceTrack; 
double timestamp; 
NSDate *openTime  
NSString *name 
NSString *playerName 
NSString *mediaEvent 
NSString *segment 
NSUInteger milestone 
NSUInteger offsetMilestone 
NSUInteger segmentNum 
NSUInteger eventType
```

## Medienmessungsklasse und Methodenreferenz {#section_50DF9359A7B14DF092634C8E913C77FE}

* **mediaCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;playerID:**

   Gibt ein `ADBMediaSettings`-Objekt mit den angegebenen Parametern zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      +(ADBMediaSettings *) mediaCreateSettingsWithName:(NSString *)name
                                                 length:(double)length
                                              playerName:(NSString *)playerName
                                               playerID:(NSString *)playerID;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMediaSettings *myCatSettings =
            [ADBMobile mediaCreateSettingsWithName:@"catVideo"                                               length:85
                                        playerName:@"catVideoPlayer"
                                          playerID:@"catPlayerId"]; 
      ```

* **mediaAdCreateSettings&#x200B;WithName:&#x200B;length:&#x200B;playerName:&#x200B;parentName:&#x200B;parentPod:&#x200B;parentPodPosition:&#x200B;CPM:**

   Gibt ein `ADBMediaSettings`-Objekt für die Verfolgung einer Videoanzeige zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (ADBMediaSettings *) mediaAdCreateSettingsWithName:(NSString *)name
                                                    length:(double)length   
                                                playerName:(NSString *)playerName
                                                parentName:(NSString *)parentName
                                                 parentPod:(NSString *)parentPod
                                        parentPodPosition:(double)parentPodPosition
                                                      CPM:(NSString *)CPM; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
        ADBMediaSettings *mySettings = 
             [ADBMobile mediaAdCreateSettingsWithName:@"ad"                                       length:30
                                           playerName:@"adPlayer"
                                           parentName:@"catVideo"
                                           parentPod:@"catCollection"
                                           parentPodPosition:2
                                                        CPM:nil];
      ```

* **mediaOpenWithSettings:&#x200B;callback:**

   Öffnet ein `ADBMediaSettings`-Objekt für die Verfolgung.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) mediaOpenWithSettings:(ADBMediaSettings *)settings
                            callback:(void (^)(ADBMediaState *mediaState))callback; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile mediaOpenWithSettings:mySettings callback:^(ADBMediaState *mediaState) {
           // do something with media state if you want}];
      ```

* **mediaClose:**

   Schließt das Medienelement mit dem Namen *name*.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
       + (void) mediaClose:(NSString *)name; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile mediaClose:@"kittiesPlaying"];
      ```

* **mediaPlay:&#x200B;offset:**

   Gibt das Medienelement mit dem Namen *name* mit dem Versatz *offset* (in Sekunden) wieder.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
       + (void) mediaPlay:(NSString *)name offset:(double)offset;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile mediaPlay:@"cats" offset:25];
      ```

* **mediaComplete:&#x200B;offset:**

   Kennzeichnet das Medienelement am angegebenen *offset* (in Sekunden) als abgeschlossen.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
       + (void) mediaComplete:(NSString *)name offset:(double)offset;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
       [ADBMobile mediaComplete:@"meowzah" offset:90]; 
      ```

* **mediaStop:&#x200B;offset:**

   Benachrichtigt das Medienmodul darüber, dass das Video mit dem Versatz *Offset* beendet oder angehalten wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) mediaStop:(NSString *)name offset:(double)offset; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile mediaStop:@"toonses" offset:30]; 
      ```

* **mediaClick:&#x200B;offset:**

   Benachrichtigt das Medienmodul darüber, dass das Medienelement angeklickt wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) mediaClick:(NSString *)name offset:(double)offset;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile mediaClick:@"soManyCats" offset:47];
      ```

* **mediaTrack:&#x200B;withData:**

   Sendet einen Verfolgungsaktionsaufruf (keine Seitenansicht) für den aktuellen Medienstatus.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void) mediaTrack:(NSString *)name withData:(NSDictionary *)data;
      ```
