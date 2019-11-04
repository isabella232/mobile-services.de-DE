---
description: Der Bericht „Ansichtspfade“ basiert auf Pfadanalysen und enthält ein Pfaddiagramm, das die Pfade darstellt, auf denen sich Benutzer von einem App-Status zu einem anderen bewegt haben.
keywords: mobile
seo-description: Der Bericht „Ansichtspfade“ basiert auf Pfadanalysen und enthält ein Pfaddiagramm, das die Pfade darstellt, auf denen sich Benutzer von einem App-Status zu einem anderen bewegt haben.
seo-title: Bericht „Ansichtspfade“
solution: Experience Cloud,Analytics
title: Bericht „Ansichtspfade“
topic: Berichte, Metriken
uuid: bc73edce-0cc0-4349-9a48-e0a40cbe1b67
translation-type: ht
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Bericht „Ansichtspfade“ {#view-paths}

Der Bericht **[!UICONTROL Ansichtspfade]** basiert auf Pfadanalysen und enthält ein Pfaddiagramm, das die Pfade darstellt, auf denen sich Benutzer von einem App-Status zu einem anderen bewegt haben.

>[!TIP]
>
>Die Berichte **[!UICONTROL Ansichtspfade]** und **[!UICONTROL Aktionspfade]** sind sehr ähnlich, da es sich bei beiden um Pfadsetzungsberichte handelt. Im Bericht **[!UICONTROL Ansichtspfade]** wird angezeigt, wie Benutzer in der App von einem Bildschirm zum nächsten navigieren. Der Bericht **[!UICONTROL Aktionspfade]** zeigt die Abfolge von Aktionen und Ereignissen, wie z. B. Klicks, Auswahlen, Größenänderungen usw., die der Benutzer in Ihrer App durchführt. Sie können einen Trichterbericht verwenden, um Navigation und Aktionen in einem Bericht zu kombinieren. Weitere Informationen finden Sie in [Trichter](/help/using/usage/reports-funnel.md).

![Ansichtspfade](assets/view_paths.png)

Jeder boxförmige Knoten stellt einen Status in den Pfaden der Benutzer durch eine App dar. In der oben stehenden Abbildung beispielsweise stellt der oberste Knoten die Anzahl der Benutzer dar, die die App gestartet haben und zur Hauptansicht navigiert sind.

Wenn Sie auf einen Knoten klicken, werden zur Anpassung des Diagramms zusätzliche Optionen, wie z. B. **[!UICONTROL Fokus]** oder **[!UICONTROL Erweitern]**, angezeigt. Wenn Sie beispielsweise im obersten Knoten auf den Status **[!UICONTROL MainView]** klicken, werden die Symbole **[!UICONTROL Fokus]** und **[!UICONTROL Erweitern]** angezeigt.

Um die Ansicht zu erweitern, klicken Sie auf das Symbol **[!UICONTROL +]**. So werden zusätzliche Pfade angezeigt, die zum Knoten hin oder von ihm weg führen. In der unten stehenden Abbildung steht Status 1 für das Starten der App und Status 2 für das Aufrufen der Hauptseite der App. Status 3 enthält die folgenden von Benutzern genutzten Pfade:

* Navigation zu „Aufnahmen“
* Navigation zur Elementauswahl
* Navigation zur Kamera
* Navigation zur Infoseite des Elements

![](assets/view_paths_expand.png)

Klicken Sie auf ![Fokussymbol](assets/icon_focus.png), um einen Knoten zu isolieren und nur die ein- und ausgehenden Pfade dieses Knotens anzuzeigen. In der unten stehenden Ansicht gingen folgende Pfade Benutzern voraus, die die Hauptseite der App aufgerufen haben:

* Elementinfo
* Elementauswahl
* Aufnahmen
* Kamera

![Ansichtspfad – Fokus](assets/view_paths_focus.png)

Sie können mehrere Knoten fokussieren oder erweitern, um eine detaillierte Darstellung der Pfade zu erhalten, denen Benutzer in Ihrer App folgen. Beispiel:

![Ansichtspfad – Mehrere](assets/view_paths_mult.png)

Für diesen Bericht können folgende Optionen konfiguriert werden:

* **[!UICONTROL Zeitraum]**
Klicken Sie auf das Symbol **[!UICONTROL Kalender]** und wählen Sie einen benutzerdefinierten oder einen vorgegebenen Zeitraum aus der Dropdownliste aus.
* **[!UICONTROL Anpassen]**
Passen Sie Ihre Berichte an, indem Sie beispielsweise die Option **[!UICONTROL Anzeigen nach]** ändern oder Metriken und Filter bzw. zusätzliche Reihen (Metriken) hinzufügen. Weitere Informationen finden Sie in [Berichte anpassen](/help/using/usage/reports-customize/reports-customize.md).
* **[!UICONTROL Filter]**
Klicken Sie auf **[!UICONTROL Filter]**, um einen Filter zu erstellen, der verschiedene Berichte umfasst. Auf diese Weise können Sie die Performance eines Segments für alle Mobilberichte anzeigen. Mit einem fixierbaren Filter können Sie einen Filter definieren, der auf alle Berichte (außer auf Pfadsetzungsberichte) angewendet werden kann. Weitere Informationen finden Sie unter [Fixierbaren Filter hinzufügen](/help/using/usage/reports-customize/t-sticky-filter.md).
* **[!UICONTROL Herunterladen]**
Klicken Sie auf **[!UICONTROL PDF]** oder **[!UICONTROL CSV]**, um Dokumente herunterzuladen bzw. zu öffnen und diese mit Benutzern zu teilen, die keinen Zugriff auf Mobile Services haben, oder in Präsentationen zu verwenden.