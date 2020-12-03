---
description: In Adobe Analytics können Sie Rollen auf der Startseite der Admin Tools verwalten.
seo-description: In Adobe Analytics können Sie Rollen auf der Startseite der Admin Tools verwalten.
seo-title: Rollen und Berechtigungen
title: Rollen und Berechtigungen
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
translation-type: tm+mt
source-git-commit: c7cac006340e01d0fd1f6afe3419e6fd17294a98
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 58%

---


# Rollen und Berechtigungen{#roles-and-permissions}

In Adobe Analytics können Sie Rollen auf der Startseite der Admin Tools verwalten.

## Übersicht {#section_91B8192891E14E5285718C8118912500}

Die folgenden Rollen können Berechtigungen in der Mobile Services-Benutzeroberfläche verwalten:

### Analytics-Admin

Ein Analytics-Administrator verwaltet Benutzergruppen und weist Berechtigungen zu, von denen einer der Administrator für die mobile App ist. Der Experience Cloud-Administrator verknüpft Ihr Adobe ID mit Ihrem Adobe Analytics-Konto, sodass Sie sich über Ihr Adobe ID bei der Mobile Services-Benutzeroberfläche anmelden können. Weitere Informationen zum Experience Cloud-Administrator finden Sie unter [Administration – Benutzerverwaltung und häufig gestellte Fragen](https://docs.adobe.com/content/help/de-DE/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!TIP]
>
>Ein bestehender Analytics-Administrator kann einem beliebigen Benutzer die Analytics-Admin-Rolle zuweisen.

Weitere Informationen zu dieser Rolle finden Sie unter folgenden Themen:

* [Übersicht über die Benutzerverwaltung](https://docs.adobe.com/content/help/de-DE/analytics/admin/user-product-management/user-management/users.html)

* [Änderungen an Berechtigungen für Benutzer und Gruppen](https://docs.adobe.com/content/help/de-DE/analytics/admin/user-product-management/user-management/permissions-changes.html)

### Mobile App Admin

Dieser Rolle beschreibt den Administrator für die Mobile Services-Benutzeroberfläche.

>[!IMPORTANT]
>
>Für einige Funktionen, wie z. B. Push-Nachrichten, muss der Analytics-Administrator das Kontrollkästchen **[!UICONTROL Segmenterstellung]** unter „Benutzerverwaltung“ aktivieren.

## Zugriff verwalten {#section_E6939C2695AA4A0DBF432D50B2670920}

Im Folgenden finden Sie einige zusätzliche Informationen zu Zugriffsoptionen in der Mobile Services-Benutzeroberfläche:

### Apps und Report Suites

Alle Mobile Service-Apps sind an Report Suites gebunden. Wenn Benutzer keinen Zugriff auf eine Report Suite haben, haben sie keinen Zugriff auf die zugehörige App dieser Report Suite.

### Mobile Services- und Analytics-Funktionen

Wenn Ihr Unternehmen für den Zugriff auf eine Funktion in der Benutzeroberfläche, wie z. B Push-Nachrichten, nicht über einen Analytics-Vertrag verfügt, kann kein Benutzer in Ihrem Unternehmen auf diese Funktion zugreifen – unabhängig von der Berechtigungsebene.

## Rollen und Berechtigungen {#section_20AA029D5B8C413C8659777E79B11620}

Im Folgenden finden Sie die Rollen in der Mobile Services-Benutzeroberfläche, einschließlich relevanter Berechtigungen:

### Analytics-Admin

* Alle Benutzer- und Mobile App Admin-Berechtigungen
* App mit neuer Report Suite erstellen
* App aus Mobile Services löschen

   >[!IMPORTANT]
   >
   >Obwohl die App in der Mobile Services-Benutzeroberfläche gelöscht wurde, ist die Report Suite weiterhin in Analytics vorhanden.

* App-Einstellungen verwalten

   * Lebenszyklus-Berichte aktivieren
   * Location Berichte aktivieren
   * Variablen und Metriken erstellen/aktualisieren/löschen

### Mobile App Admin

* Alle Benutzerberechtigungen
* App mit vorhandener Report Suite erstellen
* App-Einstellungen verwalten

   * Mobile SDK-Optionen der App konfigurieren
   * Benutzeroberflächeneinstellungen der App konfigurieren
   * Verknüpfte App Store-Apps konfigurieren
   * Optionen für universellen Link der App konfigurieren
   * Konfigurieren von Push-Diensten-Zertifikaten und API-Schlüsseln
   * Postbacks erstellen/aktualisieren/aktivieren/deaktivieren/Duplikat/archivieren/löschen
   * Link-Ziele erstellen/aktualisieren/archivieren/löschen

* Marketing-Links erstellen/aktualisieren/archivieren
* Erstellen/Importieren/Ändern/Löschen von Legacy-Akquise-Links
* Konfiguration &quot;Orte (Zielpunkte) erstellen/importieren/aktualisieren/löschen&quot;
* Push-Nachrichten erstellen/aktualisieren/senden/planen/Abbrechen/Duplikat/Archivieren/Löschen
* In-App-Nachrichten erstellen/aktualisieren/aktivieren/deaktivieren/Duplikat/archivieren/löschen

Weitere Informationen zu Gruppen und Benutzern finden Sie unter:

* [Benutzergruppeneinstellungen](https://docs.adobe.com/content/help/de-DE/analytics/admin/user-product-management/user-groups/groups.html)
* [Einen Benutzer zu einer Gruppe hinzufügen](https://docs.adobe.com/content/help/de-DE/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Mobile Services-Benutzer

Diese Rolle hat nur Ansichten und kann in der Mobile Services-Benutzeroberfläche Feedback geben.

* Feedback zur Mobile Services-Benutzeroberfläche
* Ansicht-Apps

   >[!IMPORTANT]
   >
   >Benutzer können nur die Report Suites anzeigen, auf die sie in Adobe Analytics zugreifen können.

* Ansicht-App-Einstellungen

   * App-SDK-Konfiguration herunterladen
   * Ansicht aller UI- und SDK-Einstellungen
   * Konfiguration von Ansichten und Metriken
   * Ansicht Postbacks
   * Link-Ziele für Ansichten

* Berichte anzeigen und ausführen
* Marketinglinks anzeigen
* Legacy-Akquise-Links anzeigen und exportieren
* Konfiguration von Ansichten- und Exportplätzen (Zielpunkte)
* Push-Nachrichten für Ansichten
* In-App-Nachrichten für Ansichten
