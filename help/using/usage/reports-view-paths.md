---
description: Der Bericht „Ansichtspfade“ basiert auf Pfadanalysen und enthält ein Pfaddiagramm, das die Pfade darstellt, auf denen sich Benutzer von einem App-Status zu einem anderen bewegt haben.
keywords: mobile
seo-description: Der Bericht „Ansichtspfade“ basiert auf Pfadanalysen und enthält ein Pfaddiagramm, das die Pfade darstellt, auf denen sich Benutzer von einem App-Status zu einem anderen bewegt haben.
seo-title: View Paths report
solution: Marketing Cloud, Analytics
title: View Paths report
topic: Berichte, Metriken
uuid: bc73edce-0cc0-4349-9a48-e0a40cbe1b67
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# View Paths report {#view-paths}

Der Bericht **[!UICONTROL Ansichtspfade]basiert auf Pfadanalysen und enthält ein Pfaddiagramm, das die Pfade darstellt, auf denen sich Benutzer von einem App-Status zu einem anderen bewegt haben.**

>[!TIP]
>
>The **[!UICONTROL View Paths]** and **[!UICONTROL View Action]** reports are similar because both are pathing reports. Im Bericht **[!UICONTROL Ansichtspfade]wird angezeigt, wie Benutzer in der App von einem Bildschirm zum nächsten navigieren.** Der Bericht **[!UICONTROL Aktionspfade]zeigt die Abfolge von Aktionen und Ereignissen, wie z. B. Klicks, Auswahlen, Größenänderungen usw., die der Benutzer in Ihrer App durchführt.** You can use a funnel report to combine navigation and actions in one report. For more information, see [Funnel](/help/using/usage/reports-funnel.md).

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

![view path focus](assets/view_paths_focus.png)

Sie können mehrere Knoten fokussieren oder erweitern, um eine detaillierte Darstellung der Pfade zu erhalten, denen Benutzer in Ihrer App folgen. Beispiel:

![view path multi](assets/view_paths_mult.png)

Für diesen Bericht können folgende Optionen konfiguriert werden:

* **[!UICONTROL Zeitraum]** Klicken Sie auf das Symbol **[!UICONTROL Kalender]** , um einen benutzerspezifischen Zeitraum auszuwählen oder einen voreingestellten Zeitraum aus der Dropdownliste auszuwählen.
* **[!UICONTROL Passen Sie]** Sie Ihre Berichte an, indem Sie die Optionen **[!UICONTROL Anzeigen nach]** ändern, Metriken und Filter hinzufügen, zusätzliche Reihen (Metriken) hinzufügen und vieles mehr. For more information, see [Customize Reports](/help/using/usage/reports-customize/reports-customize.md).
* **[!UICONTROL Filter]** Klicken Sie auf **[!UICONTROL Filter]** , um einen Filter zu erstellen, der verschiedene Berichte umfasst, um zu sehen, wie ein Segment in allen Mobilberichten funktioniert. Mit einem fixierbaren Filter können Sie einen Filter definieren, der auf alle Berichte (außer auf Pfadsetzungsberichte) angewendet werden kann. For more information, see Add Sticky Filter.[](/help/using/usage/reports-customize/t-sticky-filter.md)
* **[!UICONTROL Download
Click PDF or CSV to download or open documents and share with users who do not have access to Mobile Services or to use the file in presentations.]**********