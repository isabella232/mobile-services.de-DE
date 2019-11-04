---
description: In Adobe Analytics können Sie Rollen auf der Startseite der Admin Tools verwalten.
seo-description: In Adobe Analytics können Sie Rollen auf der Startseite der Admin Tools verwalten.
seo-title: Rollen und Berechtigungen
title: Rollen und Berechtigungen
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
translation-type: ht
source-git-commit: c7cac006340e01d0fd1f6afe3419e6fd17294a98

---


# Rollen und Berechtigungen{#roles-and-permissions}

In Adobe Analytics können Sie Rollen auf der Startseite der Admin Tools verwalten.

## Übersicht {#section_91B8192891E14E5285718C8118912500}

Die folgenden Rollen können Berechtigungen in der Mobile Services-Benutzeroberfläche verwalten:

### Analytics-Admin

Analytics-Admins verwalten Benutzergruppen und weisen Berechtigungen zu. Hierzu zählt auch der Mobile App Admin. Der Experience Cloud-Admin verknüpft Ihre Adobe ID mit Ihrem Adobe Analytics-Konto. So können Sie sich mit Ihrer Adobe ID bei der Mobile Services-Benutzeroberfläche anmelden. Weitere Informationen zum Experience Cloud-Administrator finden Sie unter [Administration – Benutzerverwaltung und häufig gestellte Fragen](https://docs.adobe.com/content/help/de-DE/core-services/interface/manage-users-and-products/admin-getting-started.html).

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

Alle Mobile Services-Apps sind mit Report Suites verbunden. Wenn Benutzer nicht auf eine Report Suite zugreifen können, können sie auch nicht auf die mit der Report Suite verbundene App zugreifen.

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
   * Standort-Berichte aktivieren
   * Erstellen/Aktualisieren/Löschen von Variablen und Metriken

### Mobile App Admin

* Alle Benutzerberechtigungen
* App mit vorhandener Report Suite erstellen
* App-Einstellungen verwalten

   * Optionen des mobilen SDK der App konfigurieren
   * UI-Einstellungen der App konfigurieren
   * Verknüpfte Appstore-Apps konfigurieren
   * Optionen für universelle Links der App konfigurieren
   * Push-Dienst-Zertifikate und API-Schlüssel konfigurieren
   * Erstellen/Ändern/Aktivieren/Deaktivieren/Duplizieren/Archivieren/Löschen von Postbacks
   * Erstellen/Ändern/Archivieren/Löschen von Link-Zielen

* Erstellen/Ändern/Archivieren von Marketinglinks
* Erstellen/Importieren/Ändern/Löschen von Legacy-Akquise-Links
* Erstellen/Importieren/Ändern/Löschen der Orte-Konfiguration (Zielpunkte)
* Erstellen/Ändern/Senden/Planen/Abbrechen/Duplizieren/Archivieren/Löschen von Push-Nachrichten
* Erstellen/Ändern/Aktivieren/Deaktivieren/Duplizieren/Archivieren/Löschen von In-App-Nachrichten

Weitere Informationen zu Gruppen und Benutzern finden Sie unter folgenden Themen:

* [Benutzergruppeneinstellungen](https://docs.adobe.com/content/help/de-DE/analytics/admin/user-product-management/user-groups/groups.html)
* [Einen Benutzer zu einer Gruppe hinzufügen](https://docs.adobe.com/content/help/de-DE/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Mobile Services-Benutzer

Diese Rolle verfügt über Leseberechtigungen und kann in der Mobile Services-Benutzeroberfläche Feedback bereitstellen.

* Feedback in der Mobile Services-Benutzeroberfläche bereitstellen
* Apps anzeigen

   >[!IMPORTANT]
   >
   >Benutzer können nur die Report Suites anzeigen, auf die sie in Adobe Analytics zugreifen können.

* App-Einstellungen anzeigen

   * App-SDK-Konfiguration herunterladen
   * Alle UI- und SDK-Einstellungen anzeigen
   * Variablen- und Metrikkonfiguration anzeigen
   * Postbacks anzeigen
   * Link-Ziele anzeigen

* Berichte anzeigen und ausführen
* Marketinglinks anzeigen
* Legacy-Akquise-Links anzeigen und exportieren
* Orte-Konfiguration (Zielpunkte) anzeigen und exportieren
* Push-Nachrichten anzeigen
* In-App-Nachrichten anzeigen
