---
description: In Adobe Analytics können Sie Rollen auf der Startseite der Admin Tools verwalten.
title: Rollen und Berechtigungen
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: 7b26c852dd9dba67a8b5e3228c1fecadfb465dca
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 49%

---

# Rollen und Berechtigungen{#roles-and-permissions}

In Adobe Analytics können Sie Rollen auf der Startseite der Admin Tools verwalten.

## Übersicht {#section_91B8192891E14E5285718C8118912500}

Die folgenden Rollen können Berechtigungen in der Mobile Services-Benutzeroberfläche verwalten:

### Analytics-Admin

An Analytics Admin manages user groups and assigns permissions, one of which is the Mobile App Admin. The Experience Cloud Admin links your Adobe ID to your Adobe Analytics account, which allows you to log in to the Mobile Services UI by using your Adobe ID. [](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=de)

>[!TIP]
>
>Ein bestehender Analytics-Administrator kann einem beliebigen Benutzer die Analytics-Admin-Rolle zuweisen.

### Mobile App Admin

Dieser Rolle beschreibt den Administrator für die Mobile Services-Benutzeroberfläche.

>[!IMPORTANT]
>
>Für einige Funktionen, wie z. B. Push-Nachrichten, muss der Analytics-Administrator das Kontrollkästchen **[!UICONTROL Segmenterstellung]** unter „Benutzerverwaltung“ aktivieren.

## Zugriff verwalten {#section_E6939C2695AA4A0DBF432D50B2670920}

Im Folgenden finden Sie einige zusätzliche Informationen zu Zugriffsoptionen in der Mobile Services-Benutzeroberfläche:

### Apps und Report Suites

All Mobile Service apps are tied to report suites. If users do not have access to a report suite, they will not have access to that report suite&#39;s associated app.

### Mobile Services- und Analytics-Funktionen

Wenn Ihr Unternehmen für den Zugriff auf eine Funktion in der Benutzeroberfläche, wie z. B Push-Nachrichten, nicht über einen Analytics-Vertrag verfügt, kann kein Benutzer in Ihrem Unternehmen auf diese Funktion zugreifen – unabhängig von der Berechtigungsebene.

## Rollen und Berechtigungen {#section_20AA029D5B8C413C8659777E79B11620}

Im Folgenden finden Sie die Rollen in der Mobile Services-Benutzeroberfläche, einschließlich relevanter Berechtigungen:

### Analytics-Admin Berechtigungen

* Alle Benutzer- und Mobile App Admin-Berechtigungen
* Create App with new report suite
* Delete App from Mobile Services

   >[!IMPORTANT]
   >
   >Obwohl die App in der Mobile Services-Benutzeroberfläche gelöscht wurde, ist die Report Suite weiterhin in Analytics vorhanden.

* App-Einstellungen verwalten

   * Enable Lifecycle Reporting
   * Enable Location Reporting
   * Create/Update/Delete Variables and Metrics

### Mobile App Admin Berechtigungen

* All User Permissions
* Create App with existing report suite
* App-Einstellungen verwalten

   * Configure App&#39;s Mobile SDK options
   * Configure App&#39;s UI settings
   * Configure linked App Store apps
   * Configure App&#39;s Universal Link options
   * Configure Push Services certs and API keys
   * Create/Update/Activate/Deactivate/Duplicate/Archive/Delete Postbacks
   * Create/Update/Archive/Delete Link Destinations

* Create/Update/Archive Marketing Links
* Erstellen/Importieren/Ändern/Löschen von Legacy-Akquise-Links
* Create/Import/Update/Delete Places (Points of Interest) configuration
* Create/Update/Send/Schedule/Cancel/Duplicate/Archive/Delete Push Messages
* Create/Update/Activate/Deactivate/Duplicate/Archive/Delete In-App Messages

For more information about groups and users, see the following content in the Adobe Analytics documentation:

* [](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html?lang=de)
* [Einen Benutzer zu einer Gruppe hinzufügen](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

### Mobile Services-Benutzer

This role has view-only permissions and can provide feedback in the Mobile Services UI.

* Provide Feedback on Mobile Services UI
* View Apps

   >[!IMPORTANT]
   >
   >Benutzer können nur die Report Suites anzeigen, auf die sie in Adobe Analytics zugreifen können.

* View App Settings

   * Download App SDK configuration
   * View all UI and SDK settings
   * View Variables and Metrics configuration
   * View Postbacks
   * View Link Destinations

* Berichte anzeigen und ausführen
* Marketinglinks anzeigen
* Legacy-Akquise-Links anzeigen und exportieren
* View and Export Places (Points of Interest) configuration
* View Push Messages
* View In-App Messages
