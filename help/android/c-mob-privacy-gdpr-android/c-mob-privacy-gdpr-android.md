---
description: Mobile SDK für die Experience Cloud verfügen über mit der Datenschutz-Grundverordnung (DSGVO) konforme APIs für Datenverantwortliche, die es Benutzern ermöglichen, lokal gespeicherte Identitäten abzurufen und Auswahlstatuskennzeichnungen für die Datenerfassung und -übertragung festzulegen.
seo-description: Mobile SDK für die Experience Cloud verfügen über mit der Datenschutz-Grundverordnung (DSGVO) konforme APIs für Datenverantwortliche, die es Benutzern ermöglichen, lokal gespeicherte Identitäten abzurufen und Auswahlstatuskennzeichnungen für die Datenerfassung und -übertragung festzulegen.
seo-title: Übersicht über Privatsphäre und Datenschutz-Grundverordnung
title: Übersicht über Privatsphäre und Datenschutz-Grundverordnung
uuid: 56d6f155-efec-4b3f-a972-a63155729167
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 84%

---


# Übersicht über Privatsphäre und Datenschutz-Grundverordnung {#privacy-and-general-data-protection-regulation}

Mobile SDK für die Experience Cloud verfügen über mit der Datenschutz-Grundverordnung (DSGVO) konforme APIs für Datenverantwortliche, die es Benutzern ermöglichen, lokal gespeicherte Identitäten abzurufen und Auswahlstatuskennzeichnungen für die Datenerfassung und -übertragung festzulegen.

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie [hier](https://aep-sdks.gitbook.io/docs/), um unsere aktuelle Dokumentation abzurufen.

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDK können über [Experience Platform Launch](https://www.adobe.com/de/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.

## Übersicht

>[!IMPORTANT]
>
>**Nur** die mobilen SDK der Version 4.16.0 und neuer sind mit der DSGVO konform.

Wenn Adobe einem Unternehmen Software und Dienstleistungen anbietet, fungiert Adobe als Datenverarbeiter für alle personenbezogenen Daten, die sie im Rahmen der Bereitstellung dieser Dienste verarbeitet und speichert. Als Datenverarbeiter verarbeitet Adobe personenbezogene Daten gemäß den Vorgaben und Anweisungen Ihrer Firma (z. B. gemäß Ihrer Vereinbarung mit der Adobe).

Als Datenverantwortlicher können Sie SDK von Adobe Mobile Services nutzen, um DSGVO-konform Abruf- und Löschanforderungen über Ihre Apps zu verarbeiten.

Für die Adobe Mobile SDK-Abschnitte Ihrer Mobil-Apps können Sie folgende Einstellungen und Verfahren nutzen:

* Nutzen Sie zum Abrufen von Daten aus SDK und für die Übermittlung der Daten an Ihre Server die Methode `getAllIdentifiersAsync`.

   Weitere Informationen finden Sie unter [Gespeicherte IDs abrufen](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md).

* Möchten Sie die Statusauswahl festlegen und im Rahmen der DSGVO gestellte Löschanfragen verarbeiten, legen Sie folgenden Status fest:

   * `privacyDefault`
   * `setPrivacyStatus`
   Weitere Informationen finden Sie unter [Auswahlstatus eines Benutzers festlegen](/help/android/c-mob-privacy-gdpr-android/privacy.md).