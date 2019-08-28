---
description: Der Bericht „Ansichtspfade“ basiert auf Pfadanalysen und enthält ein Pfaddiagramm, das die Pfade darstellt, auf denen sich Benutzer von einem App-Status zu einem anderen bewegt haben.
keywords: mobile
seo-description: Der Bericht „Ansichtspfade“ basiert auf Pfadanalysen und enthält ein Pfaddiagramm, das die Pfade darstellt, auf denen sich Benutzer von einem App-Status zu einem anderen bewegt haben.
seo-title: Bericht "Pfade anzeigen «
solution: Marketing Cloud, Analytics
title: Bericht "Pfade anzeigen «
topic: Berichte, Metriken
uuid: bc 73 edce -0 cc 0-4349-9 a 48-e 0 a 40 cbe 1 b 67
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Bericht "Pfade anzeigen « {#view-paths}

Der Bericht **[!UICONTROL Ansichtspfade]basiert auf Pfadanalysen und enthält ein Pfaddiagramm, das die Pfade darstellt, auf denen sich Benutzer von einem App-Status zu einem anderen bewegt haben.**

>[!TIP]
>
>The **[!UICONTROL View Paths]** and **[!UICONTROL View Action]** reports are similar because both are pathing reports. Im Bericht **[!UICONTROL Ansichtspfade]wird angezeigt, wie Benutzer in der App von einem Bildschirm zum nächsten navigieren.** Der Bericht **[!UICONTROL Aktionspfade]zeigt die Abfolge von Aktionen und Ereignissen, wie z. B. Klicks, Auswahlen, Größenänderungen usw., die der Benutzer in Ihrer App durchführt.** Sie können die Navigation und Aktionen in einem Bericht mithilfe eines Trichterberichts kombinieren. For more information, see [Funnel](/help/using/usage/reports-funnel.md).

![Ansichtspfade](assets/view_paths.png)

Jeder boxförmige Knoten stellt einen Status in den Pfaden der Benutzer durch eine App dar. In der oben stehenden Abbildung beispielsweise stellt der oberste Knoten die Anzahl der Benutzer dar, die die App gestartet haben und zur Hauptansicht navigiert sind.

Wenn Sie auf einen Knoten klicken, werden zur Anpassung des Diagramms zusätzliche Option, wie z. B. **[!UICONTROL Fokus]** oder **Erweitern], angezeigt.[!UICONTROL ** Wenn Sie beispielsweise im obersten Knoten auf den Status **[!UICONTROL MainView]** klicken, werden die Symbole **[!UICONTROL Fokus]und** Erweitern] angezeigt.**[!UICONTROL **

To expand the view, click the **[!UICONTROL +]** icon to display the additional paths that come in to or go from the node. In der unten stehenden Abbildung steht Status 1 für das Starten der App und Status 2 für das Aufrufen der Hauptseite der App. Status 3 enthält die folgenden von Benutzern genutzten Pfade:

* Navigation zu „Aufnahmen“
* Navigation zur Elementauswahl
* Navigation zur Kamera
* Navigation zur Infoseite des Elements

![](assets/view_paths_expand.png)

Click ![focus icon](assets/icon_focus.png) to isolate the node and to show the paths that are coming into and going out of the selected node. In der unten stehenden Ansicht gingen folgende Pfade Benutzern voraus, die die Hauptseite der App aufgerufen haben:

* Elementinfo
* Elementauswahl
* Aufnahmen
* Kamera

![Anzeigepfadfokus](assets/view_paths_focus.png)

Sie können mehrere Knoten fokussieren oder erweitern, um eine detaillierte Darstellung der Pfade zu erhalten, denen Benutzer in Ihrer App folgen. Beispiel:

![Ansichtspfad mehrere](assets/view_paths_mult.png)

Für diesen Bericht können folgende Optionen konfiguriert werden:

* **[!UICONTROL Zeitraum Klicken Sie]** auf das **[!UICONTROL Kalendersymbol]** , um einen benutzerdefinierten Zeitraum auszuwählen oder einen vorgegebenen Zeitraum aus der Dropdownliste auszuwählen.
* **[!UICONTROL Passen Sie]**Ihre Berichte individuell an,
indem Sie die Optionen **[!UICONTROL "Anzeigen nach"]** ändern, Metriken und Filter hinzufügen sowie zusätzliche Reihen (Metriken) und mehr hinzufügen. For more information, see [Customize Reports](/help/using/usage/reports-customize/reports-customize.md).
* **[!UICONTROL Filtern]**
Sie den Filter Filter **** , um einen Filter zu erstellen, der verschiedene Berichte umfasst, um zu sehen, wie ein Segment in allen Mobilberichten funktioniert. Mit einem fixierbaren Filter können Sie einen Filter definieren, der auf alle Berichte (außer auf Pfadsetzungsberichte) angewendet werden kann. Weitere Informationen finden Sie unter [Fixierbaren Filter hinzufügen](/help/using/usage/reports-customize/t-sticky-filter.md).
* **[!UICONTROL Klicken Sie auf]****[!UICONTROL PDF]** oder **[!UICONTROL CSV]** herunterladen,
um Dokumente herunterzuladen oder zu öffnen und für Benutzer freizugeben, die keinen Zugriff auf Mobile Services haben oder die Datei in Präsentationen verwenden.