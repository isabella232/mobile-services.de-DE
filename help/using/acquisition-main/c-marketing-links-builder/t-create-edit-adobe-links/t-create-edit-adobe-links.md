---
description: Sie können Marketinglinks erstellen oder bearbeiten, um Deep-Links zu Ihrer App oder Ihrer Website bereitzustellen.
keywords: mobile
seo-description: Sie können Marketinglinks erstellen oder bearbeiten, um Deep-Links zu Ihrer App oder Ihrer Website bereitzustellen.
seo-title: Marketinglinks erstellen oder bearbeiten
solution: Experience Cloud,Analytics
title: Marketinglinks erstellen oder bearbeiten
topic: Metrics
uuid: 305a8265-38de-4d19-8c79-b3912f5aae7c
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 100%

---


# Marketinglinks erstellen oder bearbeiten {#create-or-edit-marketing-links}

Sie können Marketinglinks erstellen oder bearbeiten, um Deep-Links zu Ihrer App oder Ihrer Website bereitzustellen. Weitere Informationen finden Sie in [Universelle Links (Apple) und App-Links (Android)](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. Erweitern Sie im linken Navigationsbereich Ihrer App den Bereich **[!UICONTROL Akquise]** und klicken Sie auf **[!UICONTROL Marketing Link Builder]**.
1. Führen Sie eine der folgenden Aufgaben aus:

   * Klicken Sie zum Erstellen eines Marketinglinks auf **[!UICONTROL Neu erstellen]**.
   * Klicken Sie zum Bearbeiten eines Links in der Spalte **[!UICONTROL Titel]** auf den Namen des entsprechenden Links.

1. Geben Sie Informationen in folgende Felder ein:

   * **[!UICONTROL Name des Marketinglinks]**:

      (**Pflichtfeld**) Geben Sie einen beschreibenden Namen für den Marketinglink an. Der Name wird auf der Seite Marketing-Links der Benutzeroberfläche von Adobe Mobile Services angezeigt. Ein beschreibender Name hilft Ihnen und anderen in Ihrer Organisation schnell einen bestimmten Link zu finden und seinen Zweck nachzuvollziehen.

   * **[!UICONTROL Eindeutiger Trackingcode]**:

      (**Pflichtfeld**) Geben Sie den gewünschten Trackingcode an oder klicken Sie auf ( ![Symbol „Generieren“](assets/icon_generate.png) ), um einen neuen Trackingcode zu erstellen. Sie können Berichte anzeigen, in denen die Verwendung des Trackingcodes detailliert dargestellt wird.

   * **[!UICONTROL Verfolgungskontextdaten hinzufügen]**:

      (**Optional**) Klicken Sie auf das **[!UICONTROL +]**-Symbol und geben Sie relevante Informationen ein, um Ihre Kampagne mithilfe von Kontextdaten zu verfolgen. Wählen Sie in der Dropdown-Liste **[!UICONTROL Benutzerdefinierte Kontextdaten]** ein vorkonfiguriertes oder eines Ihrer eigenen Tags aus. Kontextdaten werden für Berichte verwendet, wenn der Marketinglink bereitgestellt wird.

      Folgende vorgegebenen Tags sind verfügbar:

      * **Benutzerdefinierte Kontextdaten**
Geben Sie den Schlüssel und den Wert an. Wenn Sie benutzerdefinierte Kontextdaten hinzufügen, müssen Sie eine Verarbeitungsregel erstellen. Weitere Informationen finden Sie unter Übersicht über [Verarbeitungsregeln](https://docs.adobe.com/content/help/de-DE/analytics/admin/admin-tools/processing-rules/processing-rules.html).

      * **Quelle**
Geben Sie die ursprünglich verweisende Stelle an, z. B. „Newsletter“ oder „Homepage“.

      * **Medium**
Geben Sie das Marketingmedium an, z. B. „Banner“ oder „E-Mail“.

      * **Inhalt**
Geben Sie den Namen oder die ID der Anzeige mit dem Link an.

      * **Begriff**
Geben Sie bezahlte Begriffe oder andere Suchbegriffe für die Anzeige an.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Geben Sie Informationen in folgende Felder ein:

   * **(Pflichtfeld)** Geben Sie in **[!UICONTROL Fallback-URL]** die URL an, zu der Benutzer weitergeleitet werden, wenn ein Ziel nicht gefunden wird (wenn sich der Benutzer z. B. an einem Desktop-PC oder auf einer anderen Plattform befindet, die mit keiner Zielregel übereinstimmt).
   * Wählen Sie unter **[!UICONTROL Optionen für Marketinglinks]** die Option **[!UICONTROL Interstitials]** oder **[!UICONTROL Universelle bzw. Anwendungslinks]** aus.

      Weitere Informationen finden Sie in [Interstitials](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md) oder in [Universelle Links (Apple) und App-Links (Android)](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

   * **(Bedingt)** Wenn **[!UICONTROL Universelle bzw. App-Links]** unter **[!UICONTROL Benutzerdefinierter Pfad]** ausgewählt wurde, können Benutzer den URL-Pfad nach der Domäne mit beliebigen Abfrageparametern definieren. Weitere Informationen finden Sie in [Universelle Links (Apple) und App-Links (Android)](/help/using/c-manage-app-settings/c-mob-confg-app/c-universal-app-links.md).

1. Klicken Sie auf **[!UICONTROL Deep-Link-Interstitial bearbeiten]** und konfigurieren Sie den Link.

   (**Optional**) Wenn mehrere Ziele vorhanden sind, können Benutzer abhängig davon weitergeleitet werden, ob sie die App installiert haben. Wenn die App installiert ist, wird eine Interstitial-Landingpage angezeigt.

   Weitere Informationen finden Sie unter [Interstitials](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/t-interstitials.md).

1. Klicken Sie auf **[!UICONTROL Speichern]** und dann auf **[!UICONTROL Weiter]**.
1. Konfigurieren Sie auf der Seite „Ziel“ den Link.

   1. Klicken Sie auf das Symbol **[!UICONTROL Entscheidung]** ( ![Entscheidungssymbol](assets/icon_decision.png) ) und wählen Sie einen der folgenden Entscheidungsorte aus:

      * **[!UICONTROL Entscheidung hinzufügen]**
      * **[!UICONTROL Pfad hinzufügen]**
   1. Wenn Sie **[!UICONTROL Entscheidung hinzufügen]** ausgewählt haben, legen Sie nun einen der folgenden Entscheidungstypen fest:

      * **[!UICONTROL Betriebssystem]**

         Zu den unterstützten Betriebssystemen zählen u. a. iOS, Android und AMX.

      * **[!UICONTROL Gerätetyp]**

         Gerätetypen beinhalten Geräte, wie z. B. Desktops, E-Reader, Spielekonsolen, Mobiltelefone und Set-Top-Boxen.
   1. Klicken Sie auf das Symbol **[!UICONTROL Ziel]** ( ![Rechteckssymbol](assets/icon_square.png) ) und wählen Sie einen der folgenden Zieltypen aus:

      * **[!UICONTROL Appstore]**
      * **[!UICONTROL Web-Link]**
      * **[!UICONTROL App-Deep-Link]**
      * **[!UICONTROL Hybrid-Link]**

      >[!TIP]
      >
      >Wenn Sie den Zieltyp **[!UICONTROL Web-Link]** mit einem Link zum Appstore verwenden, wird die Akquise nicht verfolgt. Verwenden Sie zum Verfolgen von Akquisen den Zieltyp **[!UICONTROL Appstore]**.

      Weitere Informationen finden Sie in [Neues Link-Ziel erstellen](/help/using/acquisition-main/c-manage-link-destinations/t-create-new-app-deep-link-destination.md).




1. Klicken Sie zum Speichern des Marketinglinks auf die ![drei Punkte](assets/icon_elipses.png) und dann auf **[!UICONTROL Speichern]**.
