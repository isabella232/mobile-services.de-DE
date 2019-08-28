---
description: Der allgemeine Prozess zur Videomessung ist für sämtliche AppMeasurement-Plattformen sehr ähnlich. Dieser Abschnitt bietet eine grundlegende Übersicht der Aufgaben des Entwicklers sowie Codebeispiele.
seo-description: Der allgemeine Prozess zur Videomessung ist für sämtliche AppMeasurement-Plattformen sehr ähnlich. Dieser Abschnitt bietet eine grundlegende Übersicht der Aufgaben des Entwicklers sowie Codebeispiele.
seo-title: Video-Analytics
title: Video-Analytics
uuid: 0 d 2731 f 3-77 a 9-4 db 1-9 a 8 c -1 e 56 c 212 ecb 4
translation-type: tm+mt
source-git-commit: 5fbba02eb61679344f638b6465e47b0d9ae5a988

---


# Video Analytics  {#video-analytics}

Der allgemeine Prozess zur Videomessung ist für sämtliche AppMeasurement-Plattformen sehr ähnlich. Dieser Abschnitt bietet eine grundlegende Übersicht der Aufgaben des Entwicklers sowie Codebeispiele.

Weitere Informationen zur Videomessung finden Sie im [Handbuch Messen von Audio und Video in Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html) . Die folgende Tabelle enthält die Mediendaten, die an Analytics gesendet werden. Verwenden Sie Verarbeitungsregeln, um die Kontextdaten in der Spalte „Kontextdatenvariable“ zu einer Analytics-Variablen so zuzuordnen, wie dies in der Spalte „Variablentyp“ beschrieben wird.

## Player-Ereignisse Analytics-Variablen zuordnen

* **a.media.name**

   (Erforderlich) Erfasst den Namen des Videos, wie in der Implementierung angegeben, wenn ein Besucher das Video auf irgendeine Weise ansieht. Sie können Classification für diese Variable hinzufügen.

   **(Optional)** Die Custom Insight-Variable stellt Videopfadinformationen bereit.

   * Variablenname: Evar
      * Standardgültigkeit: Besuch
      * Benutzerspezifischer Insight-Bericht (s.prop, wird zur Videopfadsetzung verwendet)

* **a.media.name**

   (**Optional**) Bietet Informationen zur Videopfadsetzung. Die Pfadgebung für diese Variable muss von ClientCare aktiviert werden.

   * Ereignistyp: Benutzerspezifischer Insight-Bericht (s.prop)
   * Benutzerspezifischer Insight-Bericht (s.prop)

* **a.media.segment**

   (**Erforderlich**) Erfasst Videosegmentdaten, einschließlich Segmentname und Reihenfolge, in der das Segment im Video erscheint. Diese Variable wird gefüllt, indem Sie die Variable `segmentByMilestones` beim automatischen Verfolgen von Player-Ereignissen aktivieren oder indem Sie einen benutzerspezifischen Segmentnamen beim manuellen Verfolgen der Player-Ereignisse festlegen.

   For example, when a visitor views the first segment in a video, SiteCatalyst might collect `1:M:0-25` in the Segments eVar. Bei der Standardmethode zur Videodatenerfassung werden Daten beim Videostart (play), Segmentbeginn und Videoende (stop) erfasst.

   Analytics zeichnet die erste Segmentansicht am Anfang des Segments auf, wenn der Besucher die Wiedergabe startet. Nachfolgende Segmentansichten werden aufgezeichnet, wenn das jeweilige Segment anfängt.

   * Variablentyp: Evar
   * Standardgültigkeit: Seitenansicht

* **a.contentType**

   Erfasst Daten zum Typ des Inhalts, der von einem Besucher angesehen wird. Von der Videomessung gesendete Hits erhalten den Content-Typ „video“. Diese Variable muss nicht exklusiv für die Videoverfolgung reserviert sein. Wenn Sie einrichten, dass andere Inhalte den Content-Typ mit dieser Variable melden, können Sie die Verteilung der Besucher über die verschiedenen Content-Typen hinweg analysieren. Sie könnten z. B. andere Content-Typen mit Werten wie „article“ oder „product page“ über diese Variable mit Tags versehen. Im Hinblick auf die Videomessung können Sie über den Content-Typ Videobesucher identifizieren und somit Videokonversionsraten berechnen.

   * Variablentyp: Evar
   * Standardgültigkeit: Seitenansicht

* **a.media.timePlayed**

   Gibt in Sekunden an, wie lange ein Video seit dem letzten Datenerfassungsprozess (Bildanforderung) angesehen wurde.

   * Variablentyp: Ereignis
   * Typ: Zähler

* **a.media.view**

   Gibt an, dass ein Besucher einen Teil eines Videos betrachtet hat. Es werden aber keine Informationen zu der Länge oder dem Ausschnitt eines vom Besucher angesehenen Videos bereitgestellt.

   * Variablentyp: Ereignis
   * Typ: Zähler

* **a.media.segmentView**

   Gibt an, dass ein Besucher einen Teil eines Videosegments betrachtet hat. Es werden aber keine Informationen zu der Länge oder dem Ausschnitt eines vom Besucher angesehenen Videos bereitgestellt.

   * Variablentyp: Ereignis
   * Typ: Zähler

* **a .media.complete**

   Gibt an, dass ein Besucher ein Video vollständig angesehen hat. Standardmäßig wird das complete-Ereignis 1 Sekunde vor dem Ende des Videos gemessen. Bei der Implementierung können Sie festlegen, wie viele Sekunden vor dem Ende des Videos eine Ansicht als vollständig betrachtet werden soll. Bei Live-Videos und anderen Streams ohne definiertes Ende können Sie einen eigenen Punkt angeben, an dem Beendigungen gemessen werden sollen (z. B. nach einer bestimmten Wiedergabedauer).

   * Variablentyp: Ereignis
   * Typ: Zähler

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, The `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. Wenn beispielsweise der Player angehalten wird, muss `mediaStop` aufgerufen werden. `mediaPlay` wird aufgerufen, wenn die Wiedergabe gestartet oder fortgesetzt wird.

## Media measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

* **open**

   Öffnet ein Video für die Verfolgung.

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

   Plays the media item named *`name`* at the given *`offset`* (in seconds).

   * Hier finden Sie die Syntax für diese Methode:

      ```cpp
      void play(QString name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```cpp
      ADBMediaAnalytics::sharedInstance()->play("name", 0); 
      ```

* **Fertig**

   Kennzeichnet das Medienelement am angegebenen *`offset`(in Sekunden) als abgeschlossen.*

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
