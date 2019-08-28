---
description: Sie können Zielpunkte erstellen und verwalten, mit denen Sie geografische Standorte definieren können, die Sie für Korrelationszwecke, zum Ansprechen von Zielgruppen mit In-App-Nachrichten und vieles mehr verwenden können. Wenn ein Treffer innerhalb eines Zielpunkts gesendet wird, wird der Zielpunkt an den Treffer angehängt.
keywords: mobile
seo-description: Sie können Zielpunkte erstellen und verwalten, mit denen Sie geografische Standorte definieren können, die Sie für Korrelationszwecke, zum Ansprechen von Zielgruppen mit In-App-Nachrichten und vieles mehr verwenden können. Wenn ein Treffer innerhalb eines Zielpunkts gesendet wird, wird der Zielpunkt an den Treffer angehängt.
seo-title: Zielpunkte verwalten
solution: Marketing Cloud, Analytics
title: Zielpunkte verwalten
topic: Metriken
uuid: 7 b 362534-54 fb -43 a 3-b 6 b 2-dfc 8 f 45 ff 7 c 6
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Manage points of interest {#manage-points-of-interest}

Sie können pois erstellen und verwalten, mit denen Sie geografische Standorte definieren können, die Sie für Korrelationszwecke, Target mit In-App-Nachrichten usw. verwenden können. Wenn ein Treffer in einem POI gesendet wird, wird der Name an den Treffer angehängt.

Bevor Sie Speicherort verwenden können, überprüfen Sie die folgenden Anforderungen:

* Sie müssen über Analytics – Mobile Apps oder Analytics Premium verfügen.
* Sie müssen **[!UICONTROL Standort-Berichte]für die App aktivieren.**
* If you are using a version of the iOS SDK or Android SDK older than version 4.2, after adding new **[!UICONTROL Points of Interest]**, you must download a new configuration file and give it to your app developers.

   If you are using the iOS SDK or Android SDK version 4.2 or later, you do not need to submit an app update to the store to update your **[!UICONTROL Points of Interest]**. Wenn Sie auf der Seite "Zielpunkte verwalten" auf **[!UICONTROL " Speichern]**" klicken, werden die Änderungen in die **[!UICONTROL Zielpunktliste]** und die Konfigurationsdatei für die Live-App aktualisiert. Außerdem wird die Liste der Punkte in Ihrer App auf den Benutzergeräten aktualisiert, sofern die App das aktualisierte SDK und die Konfiguration mit einer Remote-POI-URL verwendet.

On the user's device, for a hit to be assigned to a **[!UICONTROL Points of Interest]**, location must be enabled for the app.

Führen Sie zum Verwenden der Position die folgenden Aufgaben aus:

1. Klicken Sie auf den Namen der App, um die zugehörige Seite App-Einstellungen verwalten aufzurufen.
1. Click **[!UICONTROL Location]** &gt; **[!UICONTROL Manage Points of Interest]**.

   ![Schritt Ergebnis](assets/poi.png)

1. Geben Sie die Informationen in die folgenden Felder ein:

   * **[!UICONTROL Punkt-Bezeichnung]**

      Geben Sie den Namen des **[!UICONTROL Zielpunkts]ein.**

      Dabei kann es sich um den Namen einer Stadt, eines Bundeslands oder einer Region handeln. Sie können auch **[!UICONTROL Zielpunkte]für spezifische Standorte wie Sportstadien oder Geschäfte erstellen.**

   * **[!UICONTROL Breitengrad]**

      Geben Sie den Breitengrad des **[!UICONTROL Zielpunkts ein]**. Sie können diese Information über andere Quellen wie das Internet herausfinden.

   * **[!UICONTROL Längengrad]**

      Geben Sie den Längengrad des **[!UICONTROL Zielpunkts ein]**. Sie können diese Information über andere Quellen wie das Internet herausfinden.

   * **[!UICONTROL Radius (Meter)]**

      Geben Sie den Radius (in Metern) um den **[!UICONTROL Zielpunkt]ein, der mit eingeschlossen werden soll.** Wenn Sie beispielsweise einen POI für Denver, Colorado erstellen, können Sie einen Radius angeben, der groß genug ist, um die Stadt Denver und die umliegenden Bereiche einzuschließen, aber Colorado Springs ausschließen.

   * **[!UICONTROL Landkartensymbol]**

      Wählen Sie ein Symbol aus, das in den Berichten ["Übersicht](/help/using/location/c-location-overview.md) " und" [Zuordnung"](/help/using/location/c-map-points.md) angezeigt wird.

1. Fügen Sie nach Bedarf weitere pois hinzu.

   Es wird empfohlen, nicht mehr als 5.000 pois hinzuzufügen. Wenn Sie mehr als 5.000 Zielpunkte hinzufügen, können Sie die Punkte zwar speichern, Sie erhalten jedoch eine Warnmeldung, dass gemäß den Best Practices weniger als 5.000 Zielpunkte vorhanden sein sollten.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

To delete one or more POIs, select the applicable check boxes, and click **[!UICONTROL Remove Selected]**.

Click **[!UICONTROL Import]** or **[!UICONTROL Export]** to work with the data by using a `.csv` file instead of using the Adobe Mobile user interface.
