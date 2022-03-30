---
description: Sie können ein neues Link-Ziel erstellen, das Benutzer zu einem Web-Link oder zu einem Deep-Link in Ihrer App weiterleitet.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: Neues Link-Ziel erstellen
topic-fix: Metrics
uuid: 390e3dea-0221-4f97-980d-a90ca9f162fa
exl-id: 2d2f5938-1461-43e2-a375-45c18afc9d5a
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 100%

---

# Neues Link-Ziel erstellen {#create-new-link-destination}

Sie können ein neues Link-Ziel erstellen, das Benutzer zu einem Web-Link oder zu einem Deep-Link in Ihrer App weiterleitet.

1. Klicken Sie in der Mobile Services-Benutzeroberfläche auf **[!UICONTROL Apps verwalten]**.
1. Klicken Sie auf den Namen der App, damit die zugehörige Seite „App-Informationen“ angezeigt wird.
1. Klicken Sie auf **[!UICONTROL Link-Ziele verwalten]**.
1. Klicken Sie auf **[!UICONTROL Neu erstellen]**.
1. Geben Sie Informationen in folgende Felder ein:
   * **[!UICONTROL Titel]**

      Geben Sie einen beschreibenden Namen für Ihr App-Link-Ziel ein. Der Name wird nur auf der Seite Link-Ziele verwalten der Benutzeroberfläche von Adobe Mobile Services angezeigt. Ein beschreibender Name hilft Ihnen und anderen in Ihrer Organisation schnell ein bestimmtes Link-Ziel zu finden und dessen Zweck nachzuvollziehen.

   * **[!UICONTROL Link-Typ]**

      Im Folgenden finden Sie eine Liste der verfügbaren Link-Typen:

      * **[!UICONTROL App-Deep-Link]**

         Geben Sie einen URI-Schema-Deep-Link (z. B. `yourapp://section`) ein. App-Deep-Link-Ziele sind URI-Schema-Deep-Links, die Benutzer zu einem Deep-Link in Ihrer App weiterleiten. Sie können Benutzer beispielsweise direkt zu einer bestimmten Produktseite in der App eines Online-Einzelhändlers weiterleiten.

      * **[!UICONTROL Web-Link]**

         Geben Sie eine Web-HTTP- oder HTTPS-URL ein (z. B. `https://adobe.com`). Weblink-Ziele leiten Benutzer zu einer URL weiter. Sie können Benutzer beispielsweise direkt zu einer Produktseite auf der Website eines Online-Einzelhändlers weiterleiten.

      * **[!UICONTROL Hybrid-Link]**

         Geben Sie einen universellen Link (iOS) oder einen App-Link (Android) ein (z. B. `https://yourwebsite.com`). Hybrid-Links unterstützen universelle iOS-Links oder Android-App-Links.
   * **[!UICONTROL App]**
Wählen Sie eine App aus, die mit dem Link, den Sie bereitstellen möchten, verknüpft ist.

      >[!TIP]
      >
      >Diese Informationen sind nur erforderlich, wenn Sie unter **[!UICONTROL Link-Typ]** einen App-Deep-Link oder einen Hybrid-Link ausgewählt haben. Wenn die App nicht in der Auswahlliste angezeigt wird, klicken Sie auf **[!UICONTROL Neue App hinzufügen]**, um auf eine neue App aus einem Appstore zu verweisen.

   * **[!UICONTROL Link-Typ]**

      Geben Sie die tatsächliche URL für den ausgewählten Link ein. Die Beschriftung dieses Felds hängt vom ausgewählten Link-Typ ab.

   * **[!UICONTROL Hinweise]**

      Geben Sie optionale Hinweise für Ihr Ziel ein. Zusätzliche Hinweise werden nur auf der Seite Link-Ziele verwalten der Benutzeroberfläche von Adobe Mobile Services angezeigt. Zusätzliche Hinweise können Ihnen und anderen in Ihrer Organisation beim schnellen Auffinden eines bestimmten Link-Ziels helfen und erläutern ggf. dessen Zweck, die damit verbundene Kampagne oder andere wichtige Aspekte.


1. Klicken Sie auf **Speichern**.
