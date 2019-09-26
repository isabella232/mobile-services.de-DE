---
description: You can create or edit Marketing Links to provide deep linking into your mobile app or your website.
keywords: mobile
seo-description: Sie können Marketing-Links erstellen oder bearbeiten, um Deep-Linking in Ihrer mobilen App oder Ihrer Website bereitzustellen.
seo-title: Marketing-Links erstellen oder bearbeiten
solution: Marketing Cloud, Analytics
title: Marketing-Links erstellen oder bearbeiten
topic: Metriken
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Create or edit marketing links{#create-or-edit-marketing-links}

Sie können Marketing-Links erstellen oder bearbeiten, um Deep-Linking zu Ihrer mobilen App oder Ihrer Website bereitzustellen. Weitere Informationen finden Sie unter [Apple Universal Links und Android App Links](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. In your app, in the left navigation pane, expand **[!UICONTROL Acquisition]** and click **[!UICONTROL Marketing Link Builder]**.
1. Führen Sie eine der folgenden Aufgaben aus:

   * To create a Marketing Link, click **[!UICONTROL Create New]**.
   * Klicken Sie zum Bearbeiten eines Links in der Spalte **[!UICONTROL Titel]auf den Namen des entsprechenden Links.**

1. Geben Sie Informationen in folgende Felder ein:

   * **[!UICONTROL Name des Marketinglinks]**:

      (**Required**) Specify a descriptive name for your Marketing Link. Der Name wird auf der Seite Marketing-Links der Benutzeroberfläche von Adobe Mobile Services angezeigt. Ein beschreibender Name hilft Ihnen und anderen in Ihrer Organisation schnell einen bestimmten Link zu finden und seinen Zweck nachzuvollziehen.

   * **[!UICONTROL Eindeutiger Trackingcode]**:

      (**Required**) Specify the desired tracking code or click (![generate icon](assets/icon_generate.png) to create a new tracking code. Sie können Berichte anzeigen, in denen die Verwendung des Trackingcodes detailliert dargestellt wird.

   * **[!UICONTROL Verfolgungskontextdaten hinzufügen]**:

      (**Optional**) Click the **[!UICONTROL +]** icon and type the relevant information to track your campaign using context data. Wählen Sie in der Dropdownliste **[!UICONTROL Benutzerdefinierte Kontextdaten]ein vorkonfiguriertes oder eines Ihrer eigenen Tags aus.** Kontextdaten werden zur Berichterstellung verwendet, wenn der Marketing-Link bereitgestellt wird.

      Folgende vorgegebenen Tags sind verfügbar:

      * **Benutzerspezifische Kontextdaten** Geben Sie den Schlüssel und den Wert an. Wenn Sie benutzerdefinierte Kontextdaten hinzufügen, müssen Sie eine Verarbeitungsregel erstellen. Weitere Informationen finden Sie unter Übersicht über [Verarbeitungsregeln](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

      * **Source**
Specify the original referrer, such as "newsletter" or "homepage."

      * **Medium** Geben Sie das Marketingmedium wie "Banner"oder "E-Mail"an.

      * **Inhalt** Geben Sie den Namen oder die ID der Anzeige mit dem Link an.

      * **Begriff** Geben Sie bezahlte Begriffe oder andere Suchbegriffe für die Anzeige an.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Geben Sie Informationen in folgende Felder ein:

   * **(Erforderlich)** Geben Sie in der **[!UICONTROL Fallback-URL]** die URL an, zu der Benutzer weitergeleitet werden, wenn ein Ziel nicht zugeordnet werden kann (z. B. wenn sich der Benutzer auf einem Desktop oder einer anderen Plattform befindet, die keiner Zielregel entspricht).
   * Wählen Sie unter **[!UICONTROL Optionen für Marketinglinks]** die Option **[!UICONTROL Zwischenräume]** oder **Universelle bzw. Anwendungslinks[!UICONTROL aus]**.

      Weitere Informationen finden Sie unter [Zwischenräume](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) oder universelle [Apple-Links und Android-App-Links](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

   * **(Conditional)** If **[!UICONTROL Universal or App Links]** is selected, in **[!UICONTROL Custom Path]**, users can define the URL path after the domain with any query parameter. Weitere Informationen finden Sie unter [Apple Universal Links und Android App Links](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. Click **[!UICONTROL Edit Deep Link Interstitial]** and configure the link.

   (**Optional**) When there are multiple destinations, users can be routed depending on whether they have a mobile app installed. Wenn die App installiert ist, wird eine Zwischenraum-Landingpage angezeigt.

   Weitere Informationen finden Sie unter [Interstitials](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. Click **[!UICONTROL Save]** and click **[!UICONTROL Next]**.
1. Konfigurieren Sie auf der Seite Ziel den Link.

   1. Click the **[!UICONTROL Decision]** icon (![decision icon](assets/icon_decision.png)) and select one of the following decision locations:

      * **[!UICONTROL Entscheidung hinzufügen]**
      * **[!UICONTROL Pfad hinzufügen]**
   1. If you selected **[!UICONTROL Add Decision]**, select one of the following decision types:

      * **[!UICONTROL Betriebssystem]**

         Zu den unterstützten Betriebssystemen zählen u. a. iOS, Android und AMX.

      * **[!UICONTROL Gerätetyp]**

         Gerätetypen beinhalten Geräte, wie z. B. Desktops, E-Reader, Spielekonsolen, Mobiltelefone und Set-Top-Boxen.
   1. Click the **[!UICONTROL Destination]** icon ( ![square icon](assets/icon_square.png) ) and select one of the following destination types:

      * **[!UICONTROL App Store]**
      * **[!UICONTROL Web-Link]**
      * **[!UICONTROL App-Deep-Link]**
      * **[!UICONTROL Hybrid-Link]**
      >[!TIP]
      >
      >When you use the **[!UICONTROL Web Link]** destination type with a link to the app store, acquisition is not tracked. Verwenden Sie zum Verfolgen von Akquisen den Zieltyp **[!UICONTROL App Store].**

      Weitere Informationen finden Sie unter [Erstellen eines neuen Link-Ziels](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md).




1. Klicken Sie zum Speichern des Marketing-Links auf ![Links](assets/icon_elipses.png) und dann auf **[!UICONTROL Speichern]**.
