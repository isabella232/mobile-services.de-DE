---
description: Informationen, die Ihnen bei Video-Analytics helfen.
seo-description: Informationen, die Ihnen bei Video-Analytics helfen.
seo-title: Video-Analytics
solution: Marketing Cloud, Analytics
title: Video-Analytics
topic: Entwickler und Implementierung
uuid: 7 d 4 e 6668-a 1 d 9-41 da -96 c 8-8 baac 660 c 5 b 0
translation-type: tm+mt
source-git-commit: 4b5be6c51c716114e597a80d475f838e23abb1b1

---


# Video Analytics  {#video-analytics}

Informationen, die Ihnen bei Video-Analytics helfen.

Video measurement is described in detail in the [Measuring audio and video in Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html/) guide. Der allgemeine Prozess zur Videomessung ist für sämtliche AppMeasurement-Plattformen sehr ähnlich. Dieser Schnellstart-Abschnitt bietet eine grundlegende Übersicht über die Aufgaben für Entwickler sowie einige Codebeispiele.

In der folgenden Tabelle finden Sie die Mediendaten, die an Analytics gesendet werden. Verwenden Sie Verarbeitungsregeln, um die Kontextdaten einer Analytics-Variable zuzuordnen.

* **a.media.name**

   (Erforderlich) Erfasst den Namen des Videos, wie in der Implementierung angegeben, wenn ein Besucher das Video auf irgendeine Weise ansieht. Sie können Classification für diese Variable hinzufügen.

   (**Optional**) Die Variable „Benutzerspezifischer Insight-Bericht “ bietet Informationen für die Videopfadgebung.

   * Variablentyp: Evar
   * Standardgültigkeit: Besuch
   * Benutzerspezifischer Insight-Bericht (s.prop, wird zur Videopfadsetzung verwendet)

* **a.media.name**

   (Optional) Bietet Informationen zur Videopfadsetzung. Die Pfadgebung für diese Variable muss von ClientCare aktiviert werden.

   Ereignistyp: Benutzerspezifischer Insight-Bericht (s.prop)

   * Variablentyp: Custom Insight (s. prop)

* **a.media.segment**

   (Erforderlich) Erfasst Videosegmentdaten, einschließlich Segmentname und Reihenfolge, in der das Segment im Video erscheint. Diese Variable wird gefüllt, indem Sie die Variable `segmentByMilestones` beim automatischen Verfolgen von Player-Ereignissen aktivieren oder indem Sie einen benutzerspezifischen Segmentnamen beim manuellen Verfolgen der Player-Ereignisse festlegen. For example, when a visitor views the first segment in a video, SiteCatalyst might collect the following in the `1:M:0-25` segment eVar.

   Die standardmäßige Methode zur Videodatenerfassung sammelt Daten an folgenden Punkten:

   * Videostart (Wiedergabe)
   * Segmentbeginn
   * Videoende (Stopp)
   Analytics zeichnet die erste Segmentansicht am Anfang des Segments auf, wenn der Besucher die Wiedergabe startet. Nachfolgende Segmentansichten werden aufgezeichnet, wenn das jeweilige Segment anfängt.

   * Variablentyp: Evar
   * Standardgültigkeit: Seitenansicht


* **a.contentType**

   Erfasst Daten zum Typ des Inhalts, der von einem Besucher angesehen wird. Von der Videomessung gesendete Hits erhalten den Content-Typ „video“. Diese Variable muss nicht exklusiv für die Videoverfolgung reserviert sein. Wenn Sie einrichten, dass andere Inhalte den Content-Typ mit dieser Variable melden, können Sie die Verteilung der Besucher über die verschiedenen Content-Typen hinweg analysieren. Sie könnten z. B. andere Content-Typen mit Werten wie „article“ oder „product page“ über diese Variable mit Tags versehen. Aus einer Videomessung können Sie mit dem Inhaltstyp Videobesucher identifizieren und Videokonversionsraten berechnen.

   * Variablentyp: Evar
   * Standardgültigkeit: Seitenansicht

* **a.media.timePlayed**

   Gibt in Sekunden an, wie lange ein Video seit dem letzten Datenerfassungsprozess (Bildanforderung) angesehen wurde.

   * Variablentyp: Ereignis
   * Typ: Zähler

* **a.media.view**

   Gibt an, dass ein Besucher einen Teil eines Videos betrachtet hat. Es werden aber keine Informationen zu der Länge oder dem Ausschnitt eines vom Besucher angesehenen Videos bereitgestellt.

   * Variable: Ereignis
   * Typ: Zähler

* **a.media.segmentView**

   Gibt an, dass ein Besucher einen Teil eines Videosegments betrachtet hat. Es werden aber keine Informationen zu der Länge oder dem Ausschnitt eines vom Besucher angesehenen Videos bereitgestellt.

   * Variablentyp: Ereignis
   * Typ: Zähler

* **a .media.complete**

   Gibt an, dass ein Besucher ein Video vollständig angesehen hat. Standardmäßig wird das complete-Ereignis 1 Sekunde vor dem Ende des Videos gemessen. Bei der Implementierung können Sie festlegen, wie viele Sekunden vor dem Ende des Videos eine Ansicht als vollständig betrachtet werden soll. Bei Live-Videos und anderen Streams ohne definiertes Ende können Sie einen eigenen Punkt angeben, an dem Beendigungen gemessen werden sollen (z. B. nach einer bestimmten Wiedergabedauer).

   * Variablentyp: Ereignis
   * Typ: Zähler


## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

Konfigurieren Sie ein `MediaSettings`-Objekt mit den Einstellungen, die Sie zur Videoverfolgung verwenden möchten:

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `Play`, `Stop`, and `Close` methods need to be called at the appropriate times. Wenn beispielsweise der Player angehalten wird, muss `Stop` aufgerufen werden. `Play` wird aufgerufen, wenn die Wiedergabe gestartet oder fortgesetzt wird.

## Klassen {#section_16838332727348F990305C0C6B0D795C}

### Klasse: MediaSettings

```
property Platform::String ^name; 
property Platform::String ^playerName; 
property Platform::String ^playerID; 
property double length; 
property Platform::String ^channel; 
property Platform::String ^milestones; 
property Platform::String ^offsetMilestones; 
property bool segmentByMilestones; 
property bool segmentByOffsetMilestones; 
property int trackSeconds; 
property int completeCloseOffsetThreshold; 
 
// MediaAnalytics Ad settings 
property Platform::String ^parentName; 
property Platform::String ^parentPod; 
property Platform::String ^CPM; 
property double parentPodPosition; 
property bool isMediaAd;
```

## Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **Settingswith (winjs: Settingswith)**

   Gibt ein `MediaSetting`-Objekt mit den angegebenen Parametern zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^playerID); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId"); 
      ```

* **Adsettingswith (winjs: Adsettingswith**

   Gibt ein `MediaSettings`-Objekt zur Verfolgung einer Videoanzeige zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^parentName, Platform::String ^parentPod, double parentPosition, Platform::String ^CPM); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var myAdSettings = ADB.Media.adSettingsWith("name", 10, "playerName", "parentName", "parentPod", 5, "myCPM"); 
      ```

* **Open (winjs: open)**

   Tracks a media open using the settings defined in `settings`.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.Media.open(mySettings); 
      ```

* **Schließen (winjs: close)**

   Verfolgt das Schließen des in *name* genannten Medienelements.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void Close(Platform::String ^name);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.Media.close("mediaName");
      ```

* **Play (winjs: play)**

   Verfolgt die Wiedergabe des in *`name`* genannten Mediums mit dem in *offset* (in Sekunden) angegebenen Versatz.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void Play(Platform::String ^name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.Media.play("mediaName", 0);
      ```

* **Abgeschlossen (winjs: complete)**

   Kennzeichnet das Medienelement am angegebenen *offset* (in Sekunden) als abgeschlossen.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void Complete(Platform::String ^name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.Media.complete("mediaName", 8); 
      ```

* **Stopp (winjs: stop)**

   Benachrichtigt das Medienmodul darüber, dass das Video mit dem Versatz *Offset* beendet oder angehalten wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.Media.stop("mediaName", 4);
      ```

* **Klicken Sie (winjs: Klicken)**

   Benachrichtigt das Medienmodul darüber, dass das Medienelement angeklickt wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void Click(Platform::String ^name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.Media.click("mediaName", 3);
      ```

* **Track (winjs: track)**

   Sendet einen Verfolgungsaktionsaufruf (keine Seitenansicht) für den aktuellen Medienstatus.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.Media.track("mediaName", null);
      ```

