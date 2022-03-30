---
description: Informationen, die Sie bei Video Analytics unterstützen.
solution: Experience Cloud Services,Analytics
title: Video Analytics
topic-fix: Developer and implementation
uuid: 7d4e6668-a1d9-41da-96c8-8baac860c5b0
exl-id: 86d70a6f-db12-4f94-a37f-4b1d4b99e0f1
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 71%

---

# Video Analytics  {#video-analytics}

Informationen, die Sie bei Video Analytics unterstützen.

Die Videomessung wird im Abschnitt [Messen von Streaming-Medien in Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=de) Handbuch. Der allgemeine Prozess zur Videomessung ist für alle AppMeasurement-Plattformen sehr ähnlich. Dieser Schnellstartabschnitt bietet einen grundlegenden Überblick über die Entwickleraufgaben sowie Codebeispiele.

In der folgenden Tabelle finden Sie die Mediendaten, die an Analytics gesendet werden. Verwenden Sie Verarbeitungsregeln, um die Kontextdaten einer Analytics-Variablen zuzuordnen.

* **a.media.name**

   (Erforderlich) Erfasst den in der Implementierung angegebenen Videonamen, wenn ein Besucher das Video auf irgendeine Weise anzeigt. Sie können für diese Variable Classifications hinzufügen.

   (**Optional**) Die Variable „Custom Insight“ enthält Informationen zu Videopfaden.

   * Variablentyp: eVar
   * Standardgültigkeit: Besuch
   * Custom Insight (s.prop, für den Videopfad verwendet)

* **a.media.name**

   (Optional) Bietet Informationen zur Videopfadsetzung. Der Pfad muss für diese Variable von der Kundenunterstützung aktiviert werden.

   Ereignistyp: Benutzerspezifischer Insight-Bericht (s.prop)

   * Variablentyp: Custom Insight (benutzerspezifischer Insight-Bericht) (s.prop)

* **a.media.segment**

   (Erforderlich) Erfasst Videosegmentdaten, einschließlich Segmentname und Reihenfolge, in der das Segment im Video erscheint. Diese Variable wird gefüllt, indem Sie die Variable `segmentByMilestones` beim automatischen Verfolgen von Player-Ereignissen aktivieren oder indem Sie einen benutzerspezifischen Segmentnamen beim manuellen Verfolgen der Player-Ereignisse festlegen. Wenn beispielsweise ein Besucher das erste Segment in einem Video anzeigt, kann SiteCatalyst Folgendes in der `1:M:0-25` Segment-eVar.

   Die Standardmethode zur Videodatenerfassung erfasst Daten an folgenden Punkten:

   * Videostart (play)
   * Segmentstart
   * Videoende (Stopp)

   Analytics zählt die erste Segmentansicht am Beginn des Segments, wenn der Besucher zu schauen beginnt. Nachfolgende Segmentansichten bei Segmentbeginn.

   * Variablentyp: eVar
   * Standardgültigkeit: Seitenansicht


* **a.contentType**

   Erfasst Daten zum Typ des Inhalts, der von einem Besucher angesehen wird. Den von der Videomessung gesendeten Treffern wird der Content-Typ &quot;Video&quot;zugewiesen. Diese Variable muss nicht ausschließlich für das Video-Tracking reserviert werden. Wenn andere Content-Typen den Content-Typ mit dieser Variablen melden, können Sie die Verteilung der Besucher über die verschiedenen Inhaltstypen analysieren. Sie können beispielsweise mithilfe dieser Variablen andere Content-Typen mit Werten wie &quot;article&quot;oder &quot;product page&quot;taggen. Im Hinblick auf die Videomessung können Sie mit dem Content-Typ Videobesucher identifizieren und Videokonversionsraten berechnen.

   * Variablentyp: eVar
   * Standardgültigkeit: Seitenansicht

* **a.media.timePlayed**

   Gibt in Sekunden an, wie lange ein Video seit dem letzten Datenerfassungsprozess (Bildanforderung) angesehen wurde.

   * Variablentyp: Ereignis
   * Typ: Zähler

* **a.media.view**

   Gibt an, dass ein Besucher einen Teil eines Videos betrachtet hat. Es werden jedoch keine Informationen zu der Länge oder dem Ausschnitt des vom Besucher angesehenen Videos bereitgestellt.

   * Variable: Ereignis
   * Typ: Zähler

* **a.media.segmentView**

   Gibt an, dass ein Besucher einen Teil eines Videosegments betrachtet hat. Es werden jedoch keine Informationen zu der Länge oder dem Ausschnitt des vom Besucher angesehenen Videos bereitgestellt.

   * Variablentyp: Ereignis
   * Typ: Zähler

* **a .media.complete**

   Gibt an, dass ein Besucher ein Video vollständig angesehen hat. Standardmäßig wird das complete-Ereignis 1 Sekunde vor dem Ende des Videos gemessen. Bei der Implementierung können Sie festlegen, wie viele Sekunden vor dem Ende des Videos eine Ansicht als vollständig betrachtet werden soll. Bei Live-Videos und anderen Streams ohne definiertes Ende können Sie einen eigenen Punkt angeben, an dem Beendigungen gemessen werden sollen Beispielsweise nach einer bestimmten Zeit, in der das Video betrachtet wurde.

   * Variablentyp: Ereignis
   * Typ: Zähler

## Medieneinstellungen konfigurieren {#section_929945D4183C428AAF3B983EFD3E2500}

Konfigurieren Sie ein `MediaSettings`-Objekt mit den Einstellungen, die Sie zur Videoverfolgung verwenden möchten:

```js
var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId");
```

## Player-Ereignisse verfolgen {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Zum Messen der Videowiedergabe müssen die Methoden `Play`, `Stop` und `Close` zu den entsprechenden Zeiten aufgerufen werden. Wenn beispielsweise der Player angehalten wird, muss `Stop` aufgerufen werden. `Play` wird aufgerufen, wenn die Wiedergabe gestartet oder fortgesetzt wird.

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

## Medienmessungsklasse und Methodenreferenz {#section_50DF9359A7B14DF092634C8E913C77FE}

* **SettingsWith (winJS: settingsWith)**

   Gibt ein `MediaSetting`-Objekt mit den angegebenen Parametern zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static MediaSettings ^SettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^playerID); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var mySettings = ADB.Media.settingsWith("name", 10, "playerName", "playerId"); 
      ```

* **AdSettingsWith (winJS: adSettingsWith**

   Gibt ein `MediaSettings`-Objekt zur Verfolgung einer Videoanzeige zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static MediaSettings ^AdSettingsWith(Platform::String ^name, double length, Platform::String ^playerName, Platform::String ^parentName, Platform::String ^parentPod, double parentPosition, Platform::String ^CPM); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var myAdSettings = ADB.Media.adSettingsWith("name", 10, "playerName", "parentName", "parentPod", 5, "myCPM"); 
      ```

* **Öffnen Sie (winJS: open)**

   Verfolgt das Öffnen eines Mediums mithilfe der Einstellungen, die unter `settings`.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void Open(MediaSettings ^settings);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.Media.open(mySettings); 
      ```

* **Close (winJS: close)**

   Zeichnet ein Medienende für das Medienelement mit dem Namen *name*.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void Close(Platform::String ^name);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.Media.close("mediaName");
      ```

* **Play (winJS: play)**

   Verfolgt eine Medienwiedergabe für das Medienelement mit dem Namen *`name`* nach *offset* (in Sekunden).

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void Play(Platform::String ^name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.Media.play("mediaName", 0);
      ```

* **Complete (winJS: complete)**

   Kennzeichnet das Medienelement am angegebenen *offset* (in Sekunden) als abgeschlossen.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void Complete(Platform::String ^name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.Media.complete("mediaName", 8); 
      ```

* **Stopp (winJS: stop)**

   Benachrichtigt das Medienmodul darüber, dass das Video mit dem Versatz *Offset* beendet oder angehalten wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void Stop(Platform::String ^name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.Media.stop("mediaName", 4);
      ```

* **Klicken Sie auf (winJS: click)**

   Benachrichtigt das Medienmodul darüber, dass das Medienelement angeklickt wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void Click(Platform::String ^name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.Media.click("mediaName", 3);
      ```

* **Track (winJS: track)**

   Sendet einen Verfolgungsaktionsaufruf (keine Seitenansicht) für den aktuellen Medienstatus.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void Track(Platform::String ^name, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^contextData);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADB.Media.track("mediaName", null);
      ```
