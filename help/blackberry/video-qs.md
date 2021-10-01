---
description: Der allgemeine Prozess zur Videomessung ist für alle AppMeasurement-Plattformen sehr ähnlich. Dieser Abschnitt bietet einen grundlegenden Überblick über die Aufgaben für Entwickler sowie Codebeispiele.
title: Video Analytics
uuid: 0d2731f3-77a9-4db1-9a8c-1e56c212ecb4
exl-id: 90da1a9e-2faa-429c-969e-869ebedf08cc
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 70%

---

# Video Analytics  {#video-analytics}

Der allgemeine Prozess zur Videomessung ist für alle AppMeasurement-Plattformen sehr ähnlich. Dieser Abschnitt bietet einen grundlegenden Überblick über die Aufgaben für Entwickler sowie Codebeispiele.

Weitere Informationen zur Videomessung finden Sie im Handbuch [Messen von Streaming-Medien in Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=de) .  In der folgenden Tabelle finden Sie die Mediendaten, die an Analytics gesendet werden. Verwenden Sie Verarbeitungsregeln, um die Kontextdaten in der Spalte Kontextdatenvariable einer Analytics-Variablen zuzuordnen, wie in der Spalte Variablentyp beschrieben.

## Player-Ereignisse Analytics-Variablen zuordnen

* **a.media.name**

   (Erforderlich) Erfasst den in der Implementierung angegebenen Videonamen, wenn ein Besucher das Video auf irgendeine Weise anzeigt. Sie können für diese Variable Classifications hinzufügen.

   **(Optional)** Die Custom Insight-Variable enthält Informationen zu Videopfaden.

   * Variablenname: eVar
      * Standardgültigkeit: Besuch
      * Custom Insight (s.prop, für den Videopfad verwendet)

* **a.media.name**

   (**Optional**) Bietet Informationen zur Videopfadsetzung. Der Pfad muss für diese Variable von der Kundenunterstützung aktiviert werden.

   * Ereignistyp: Benutzerspezifischer Insight-Bericht (s.prop)
   * Custom Insight (s.prop)

* **a.media.segment**

   (**Erforderlich**) Erfasst Videosegmentdaten, einschließlich Segmentname und Reihenfolge, in der das Segment im Video erscheint. Diese Variable wird gefüllt, indem Sie die Variable `segmentByMilestones` beim automatischen Verfolgen von Player-Ereignissen aktivieren oder indem Sie einen benutzerspezifischen Segmentnamen beim manuellen Verfolgen der Player-Ereignisse festlegen.

   Wenn beispielsweise ein Besucher das erste Segment in einem Video anzeigt, kann SiteCatalyst `1:M:0-25` in der eVar Segmente erfassen. Die standardmäßige Methode zur Videodatenerfassung erfasst Daten am Videostartpunkt (Wiedergabe), Segmentbeginn und am Ende des Videos (Stopp).

   Analytics zählt die erste Segmentansicht am Beginn des Segments, wenn der Besucher zu schauen beginnt. Nachfolgende Segmentansichten bei Segmentbeginn.

   * Variablentyp: eVar
   * Standardgültigkeit: Seitenansicht

* **a.contentType**

   Erfasst Daten zum Typ des Inhalts, der von einem Besucher angesehen wird. Den von der Videomessung gesendeten Treffern wird der Content-Typ &quot;Video&quot;zugewiesen. Diese Variable muss nicht ausschließlich für das Video-Tracking reserviert werden. Wenn andere Content-Typen den Content-Typ mit dieser Variablen melden, können Sie die Verteilung der Besucher über die verschiedenen Inhaltstypen analysieren. Sie können beispielsweise mithilfe dieser Variablen andere Content-Typen mit Werten wie &quot;article&quot;oder &quot;product page&quot;taggen. Im Hinblick auf die Videomessung können Sie über den Content-Typ Videobesucher identifizieren und somit Videokonversionsraten berechnen.

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

* **a .media.complete**

   Gibt an, dass ein Besucher ein Video vollständig angesehen hat. Standardmäßig wird das complete-Ereignis 1 Sekunde vor dem Ende des Videos gemessen. Bei der Implementierung können Sie festlegen, wie viele Sekunden vor dem Ende des Videos eine Ansicht als vollständig betrachtet werden soll. Bei Live-Videos und anderen Streams ohne definiertes Ende können Sie einen eigenen Punkt angeben, an dem Beendigungen gemessen werden sollen Beispielsweise nach einer bestimmten Zeit, in der das Video betrachtet wurde.

   * Variablentyp: Ereignis
   * Typ: Zähler

## Player-Ereignisse verfolgen {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Zum Messen der Videowiedergabe müssen die Methoden `mediaPlay`, `mediaStop` und `mediaClose` zu den entsprechenden Zeiten aufgerufen werden. Wenn beispielsweise der Player angehalten wird, muss `mediaStop` aufgerufen werden. `mediaPlay` wird aufgerufen, wenn die Wiedergabe gestartet oder fortgesetzt wird.

## Medienmessungsklasse und Methodenreferenz {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   Öffnet ein Video zum Tracking.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      void open(QString name, double length, QString playerName, QString playerID = QString()); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
        ADBMediaAnalytics::sharedInstance()->open("name", 10.0, "playerName", "playerID"); 
      ```

* **openAd**

   Öffnet ein `MediaSettings`-Objekt zur Verfolgung.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      void openAd(QString name, double length, QString playerName, QString parentName, QString parentPod, double parentPodPosition, QString CPM); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->openAd("name", 10, "playerName", "parentName", "podName", 0, "CPM"); 
      ```

* **close**

   Schließt das Medienelement mit dem Namen *`name`*.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      void close(QString name);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name");
      ```

* **play**

   Gibt das Medienelement mit dem Namen *`name`* mit dem Versatz *`offset`* (in Sekunden) wieder.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      void play(QString name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **Fertig**

   Kennzeichnet das Medienelement am angegebenen *`offset`* (in Sekunden) als abgeschlossen.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      void complete(QString name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->complete("name", 0);
      ```

* **stop**

   Benachrichtigt das Medienmodul darüber, dass das Video mit dem Versatz *Offset* beendet oder angehalten wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      stop(QString name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->stop("name", 0);
      ```

* **click**

   Benachrichtigt das Medienmodul darüber, dass das Medienelement angeklickt wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      void click(QString name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->close("name", 0);
      ```

* **track**

   Sendet einen Verfolgungsaktionsaufruf (keine Seitenansicht) für den aktuellen Medienstatus.

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      track(QString name, QHash<QString, QString> additionalData = QHash<QString, QString>()); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->track("name", null);
      ```
