---
description: Im Folgenden finden Sie einige Informationen zur Messung von Videos unter Android mithilfe der Videomessung.
keywords: Android;Bibliothek;Mobile;SDK
solution: Experience Cloud,Analytics
title: Video Analytics
topic-fix: Developer and implementation
uuid: a137cc27-dc28-48c0-b08e-2ca17d2c7e1d
exl-id: 1b7f5523-767a-45e8-b2e7-ecf9984849e4
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 98%

---

# Video Analytics  {#video-analytics}

Im Folgenden finden Sie einige Informationen zur Messung von Videos unter Android mithilfe der Videomessung.

>[!TIP]
>
>Während der Videowiedergabe werden diesem Dienst häufige Heartbeat-Aufrufe gesendet, um die wiedergegebene Zeit zu messen. Diese Heartbeat-Aufrufe werden alle 10 Sekunden gesendet. Dies führt zu detaillierten Videointeraktionsmetriken und genaueren Video-Fallout-Berichten. Weitere Informationen zur Videomessungslösung von Adobe finden Sie unter [Messen von Streaming-Medien in Adobe Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=de).

Der allgemeine Prozess zur Videomessung ist für alle Plattformen ähnlich. Hier finden Sie eine Übersicht der Entwickleraufgaben samt Code-Beispielen. In der folgenden Tabelle finden Sie die Mediendaten, die an Analytics gesendet werden. Verarbeitungsregeln werden verwendet, um die Kontextdaten einer Analytics-Variablen zuzuordnen.

## Player-Ereignisse Analytics-Variablen zuordnen {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

* **a.media.name**
   * Variablentyp: eVar
      * Standardgültigkeit: Besuch
      * Custom Insight (s.prop, für den Videopfad verwendet)
   * (**Erforderlich**) Wenn ein Besucher das Video auf irgendeine Weise betrachtet, erfasst diese Kontextdatenvariable den Namen des Videos, wie in der Implementierung angegeben. Sie können für diese Variable Klassifizierungen hinzufügen.
   * (**Optional**) Die Variable „Custom Insight“ enthält Informationen zu Videopfaden.

* **a.media.name**
   * Variablentyp: Custom Insight (benutzerspezifischer Insight-Bericht) (s.prop)
   * (**Optional**) Bietet Informationen zur Videopfadsetzung.

      >[!IMPORTANT]
      >
      >Der Pfad muss für diese Variable von ExpCare aktiviert werden.
   * Ereignistyp: Benutzerspezifischer Insight-Bericht (s.prop)

* **a.media.segment**
   * Variablentyp: eVar
   * Standardgültigkeit: Seitenansicht
   * (**Erforderlich**) Erfasst Videosegmentdaten, einschließlich Segmentname und Reihenfolge, in der das Segment im Video erscheint.

      Diese Variable wird gefüllt, indem Sie beim automatischen Verfolgen von Player-Ereignissen die Variable `segmentByMilestones` aktivieren oder beim manuellen Verfolgen der Player-Ereignisse einen benutzerdefinierten Segmentnamen festlegen. Beispiel: Wenn ein Besucher das erste Segment in einem Video ansieht, kann SiteCatalyst Folgendes in der Segment-eVar erfassen: `1:M:0-25`.

      Die Standardmethode zur Videodatenerfassung erfasst Daten an folgenden Punkten:

      * Videostart (play)
      * Segmentstart
      * Videoende (Stopp)

      Analytics zählt die erste Segmentansicht am Beginn des Segments, wenn der Besucher zu schauen beginnt. Nachfolgende Segmentansichten bei Segmentbeginn.


* **a.contentType**
   * Variablentyp: eVar
   * Standardgültigkeit: Seitenansicht
   * Erfasst Daten zum Typ des Inhalts, der von einem Besucher angesehen wird.

      Den von der Videomessung gesendeten Treffern wird der Content-Typ `video` zugewiesen. Im Hinblick auf die Videomessung können Sie über den **Content-Typ** Videobesucher identifizieren und somit Videokonversionsraten berechnen.

* **a.media.timePlayed**
   * Variablentyp: Ereignis
   * Typ: Zähler
   * Gibt in Sekunden an, wie lange ein Video seit dem letzten Datenerfassungsprozess (Bildanforderung) angesehen wurde.

* **a.media.view**
   * Variablentyp: Ereignis
   * Typ: Zähler
   * Gibt an, dass ein Besucher einen Teil eines Videos betrachtet hat.

      Es werden jedoch keine Informationen zu der Länge oder dem Ausschnitt des vom Besucher angesehenen Videos bereitgestellt.

* **a.media.segmentView**
   * Variablentyp: Ereignis
   * Typ: Zähler
   * Gibt an, dass ein Besucher einen Teil eines Videosegments betrachtet hat.

      Es werden jedoch keine Informationen zu der Länge oder dem Ausschnitt des vom Besucher angesehenen Videos bereitgestellt.

* **a .media.complete**
   * Variablentyp: Ereignis
   * Typ: Zähler
   * Gibt an, dass ein Besucher ein Video vollständig angesehen hat.

      Standardmäßig wird das complete-Ereignis 1 Sekunde vor dem Ende des Videos gemessen. Bei der Implementierung können Sie festlegen, wie viele Sekunden vor dem Ende des Videos eine Ansicht als vollständig betrachtet werden soll. Bei Live-Videos und anderen Streams ohne definiertes Ende können Sie einen benutzerdefinierten Punkt angeben, um die Vollständigkeit zu messen (z. B. nach einer bestimmten Wiedergabedauer).


## Medieneinstellungen konfigurieren {#section_929945D4183C428AAF3B983EFD3E2500}

Konfigurieren Sie ein `MediaSettings`-Objekt mit den Einstellungen, die Sie zur Videoverfolgung verwenden möchten:

```java
MediaSettings mySettings = Media.settingsWith("name", 10, "playerName", "playerId");
```

## Player-Ereignisse verfolgen {#section_C7F43AECBC0D425390F7FCDF3035B65D}

Zum Messen der Videowiedergabe müssen die Methoden `mediaPlay`, `mediaStop` und `mediaClose` zu den entsprechenden Zeiten aufgerufen werden. Wenn beispielsweise der Player angehalten wird, muss `mediaStop` aufgerufen werden. `mediaPlay` wird aufgerufen, wenn die Wiedergabe gestartet oder fortgesetzt wird.

## Klassen {#section_16838332727348F990305C0C6B0D795C}

**Klasse: MediaSettings**

```java
public String name; 
public String playerName; 
public String playerID; 
public double length; 
public String channel; 
public String milestones; 
public String offsetMilestones; 
public boolean segmentByMilestones; 
public boolean segmentByOffsetMilestones; 
public int trackSeconds = 0; 
public int completeCloseOffsetThreshold = 1; 
 
// MediaAnalytics Ad settings 
public String parentName; 
public String parentPod; 
public String CPM; 
public double parentPodPosition; 
public boolean isMediaAd;
```

**Klasse: MediaState**

```java
public Date openTime = new Date(); 
public String name; 
public String segment; 
public String playerName; 
public String mediaEvent; 
public int offsetMilestone; 
public int segmentNum; 
public int milestone; 
public double length; 
public double offset; 
public double percent; 
public double timePlayed; 
public double segmentLength; 
public boolean complete = false; 
public boolean clicked = false; 
public boolean ad; 
public boolean eventFirstTime;
```

## Medienmessungsklasse und Methodenreferenz {#section_50DF9359A7B14DF092634C8E913C77FE}

Im Folgenden finden Sie die Methoden der Medienmessungsklasse:

* **settingsWith**

   Gibt ein `MediaSettings`-Objekt mit den angegebenen Parametern zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      MediaSettingsmySettings = Media.settingsWith("name", 10, "playerName", "playerId");
      ```

* **adSettingsWith**

   Gibt ein `MediaSettings`-Objekt zur Verfolgung einer Videoanzeige zurück.
   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

* **open**

   Öffnet ein `MediaSettings`-Objekt zur Verfolgung.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void open(MediaSettings settings, MediaCallback callback); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.open(mySettings, new Media.MediaCallback() { 
        @Override 
        public void call(Object item)
        {//  monitor  callback  if  you  want  to  be  notified  every  second  the  media  is  playing  }
        }); 
      ```

   * **close**

      Schließt das Medienelement mit dem Namen *name*.

      * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void close(String name);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.close("name"); 
      ```


* **play**
   * Gibt das Medienelement namens *Name* mit dem Versatz *offset* (in Sekunden) wieder.
   * Hier finden Sie die Syntax für diese Methode:

      ```java
      publicstatic void play(String name, double offset); 
      ```

* **Fertig**

   Kennzeichnet das Medienelement mit dem Versatz *Offset* (in Sekunden) manuell als abgeschlossen.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void complete(String name, double offset); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.complete("name", 0); 
      ```

* **stop**

   Benachrichtigt das Medienmodul darüber, dass das Video mit dem Versatz *Offset* beendet oder angehalten wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void stop(String name, double offset); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.stop("name", 0);
      ```

* **click**

   Benachrichtigt das Medienmodul darüber, dass das Medienelement angeklickt wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void click(String name double offset); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.click("name", 0);
      ```

* **track**

   Sendet einen Verfolgungsaktionsaufruf (keine Seitenansicht) für den aktuellen Medienstatus.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      publicstatic void track(String name, Map<String, Object> data); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.track("name", null); 
      ```
