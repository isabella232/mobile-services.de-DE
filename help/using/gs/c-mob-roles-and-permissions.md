---
description: In Adobe Analytics können Sie Rollen auf der Startseite der Admin Tools verwalten.
title: Rollen und Berechtigungen
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 44%

---

# Rollen und Berechtigungen{#roles-and-permissions}

In Adobe Analytics können Sie Rollen auf der Startseite der Admin Tools verwalten.

## Übersicht {#section_91B8192891E14E5285718C8118912500}

Die folgenden Rollen können Berechtigungen in der Mobile Services-Benutzeroberfläche verwalten:

### Analytics-Admin

Ein Analytics-Administrator verwaltet Benutzergruppen und weist ihnen Berechtigungen zu, darunter auch der Mobile App-Administrator. Der Experience Cloud-Administrator verknüpft Ihre Adobe ID mit Ihrem Adobe Analytics-Konto, über das Sie sich über Ihre Adobe ID bei der Mobile Services-Benutzeroberfläche anmelden können. Weitere Informationen zum Experience Cloud-Administrator finden Sie unter [Verwalten von Experience Cloud-Benutzern und -Produkten](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html) im Handbuch zu den Komponenten der zentralen Benutzeroberfläche von Experience Cloud.

>[!TIP]
>
>Ein bestehender Analytics-Administrator kann einem beliebigen Benutzer die Analytics-Admin-Rolle zuweisen.

Weitere Informationen zu dieser Rolle finden Sie in der Adobe Analytics-Dokumentation unter folgenden Themen:

* [Übersicht über die Benutzerverwaltung](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-management/users.html)
* [Änderungen an Berechtigungen für Benutzer und Gruppen](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-management/permissions-changes.html)

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

### Analytics-Admin Berechtigungen

* Alle Benutzer- und Mobile App Admin-Berechtigungen
* App mit neuer Report Suite erstellen
* App aus Mobile Services löschen

   >[!IMPORTANT]
   >
   >Obwohl die App in der Mobile Services-Benutzeroberfläche gelöscht wurde, ist die Report Suite weiterhin in Analytics vorhanden.

* App-Einstellungen verwalten

   * Lebenszyklus-Berichte aktivieren
   * Standortberichte aktivieren
   * Variablen und Metriken erstellen/aktualisieren/löschen

### Mobile App Admin Berechtigungen

* Alle Benutzerberechtigungen
* App mit vorhandener Report Suite erstellen
* App-Einstellungen verwalten

   * Mobile SDK-Optionen der App konfigurieren
   * Benutzeroberflächeneinstellungen der App konfigurieren
   * Verknüpfte Appstore-Apps konfigurieren
   * Universelle Link-Optionen der App konfigurieren
   * Konfigurieren von Push-Dienst-Zertifikaten und API-Schlüsseln
   * Postbacks erstellen/aktualisieren/aktivieren/deaktivieren/duplizieren/archivieren/löschen
   * Link-Ziele erstellen/aktualisieren/archivieren/löschen

* Marketinglinks erstellen/aktualisieren/archivieren
* Erstellen/Importieren/Ändern/Löschen von Legacy-Akquise-Links
* Konfiguration zum Erstellen/Importieren/Aktualisieren/Löschen von Orten (POI)
* Push-Nachrichten erstellen/aktualisieren/senden/planen/abbrechen/duplizieren/archivieren/löschen
* Erstellen/Aktualisieren/Aktivieren/Deaktivieren/Duplizieren/Archivieren/Löschen von In-App-Nachrichten

Weitere Informationen zu Gruppen und Benutzern finden Sie in der Adobe Analytics-Dokumentation unter folgenden Themen:

* [Benutzergruppeneinstellungen (alt)](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-groups/groups.html)
* [Einen Benutzer zu einer Gruppe hinzufügen](https://experienceleague.adobe.com/docs/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Mobile Services-Benutzer

Diese Rolle verfügt über schreibgeschützte Berechtigungen und kann Feedback in der Mobile Services-Benutzeroberfläche bereitstellen.

* Feedback zur Mobile Services-Benutzeroberfläche bereitstellen
* Apps anzeigen

   >[!IMPORTANT]
   >
   >Benutzer können nur die Report Suites anzeigen, auf die sie in Adobe Analytics zugreifen können.

* App-Einstellungen anzeigen

   * App-SDK-Konfiguration herunterladen
   * Alle UI- und SDK-Einstellungen anzeigen
   * Anzeigen der Konfiguration von Variablen und Metriken
   * Anzeigen von Postbacks
   * Link-Ziele anzeigen

* Berichte anzeigen und ausführen
* Marketinglinks anzeigen
* Legacy-Akquise-Links anzeigen und exportieren
* Konfiguration &quot;Orte anzeigen und exportieren&quot;(POI)
* Push-Nachrichten anzeigen
* In-App-Nachrichten anzeigen
