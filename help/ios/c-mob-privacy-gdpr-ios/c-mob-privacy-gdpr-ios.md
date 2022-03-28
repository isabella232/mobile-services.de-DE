---
description: Mobile SDK für die Experience Cloud verfügen über mit der Datenschutz-Grundverordnung (DSGVO) konforme APIs für Datenverantwortliche, die es Benutzern ermöglichen, lokal gespeicherte Identitäten abzurufen und Auswahlstatuskennzeichnungen für die Datenerfassung und -übertragung festzulegen.
title: Privatsphäre und Datenschutz-Grundverordnung
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
exl-id: 8549310d-31b8-49a3-9276-f8e9ab980a10
source-git-commit: bd55e3525488f24bc9845220f0df62706ec28f31
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 80%

---

# Privatsphäre und Datenschutz-Grundverordnung {#privacy-and-general-data-protection-regulation}

Mobile SDK für die Experience Cloud verfügen über mit der Datenschutz-Grundverordnung (DSGVO) konforme APIs für Datenverantwortliche, die es Benutzern ermöglichen, lokal gespeicherte Identitäten abzurufen und Auswahlstatuskennzeichnungen für die Datenerfassung und -übertragung festzulegen.

>[!IMPORTANT]
>
>**Nur** die mobilen SDK der Version 4.16.0 und neuer sind mit der DSGVO konform.

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie [hier](https://aep-sdks.gitbook.io/docs/), um unsere aktuelle Dokumentation abzurufen.

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über [Experience Platform Launch](https://www.adobe.com/de/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.

## Übersicht

Wenn Adobe einem Unternehmen Software und Dienstleistungen anbietet, fungiert Adobe als Datenverarbeiter für alle personenbezogenen Daten, die im Rahmen dieser Dienstleistungen verarbeitet und gespeichert werden. Als Datenverarbeiter verarbeitet Adobe personenbezogene Daten gemäß den Berechtigungen und Anweisungen Ihres Unternehmens (z. B. gemäß Ihrer Vereinbarung mit Adobe).

Als Datenverantwortlicher können Sie SDK von Adobe Mobile Services nutzen, um DSGVO-konform Abruf- und Löschanforderungen über Ihre Apps zu verarbeiten.

Für die Adobe Mobile SDK-Abschnitte Ihrer Mobil-Apps können Sie folgende Einstellungen und Verfahren nutzen:

* Nutzen Sie zum Abrufen von Daten aus SDK und für die Übermittlung der Daten an Ihre Server die Methode `getAllIdentifiersAsync`.

   Weitere Informationen finden Sie unter [Gespeicherte IDs abrufen](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md).

* Möchten Sie die Statusauswahl festlegen und im Rahmen der DSGVO gestellte Löschanfragen verarbeiten, legen Sie folgenden Status fest:

   * `privacyDefault`
   * `setPrivacyStatus`

   Weitere Informationen finden Sie unter [Auswahlstatus eines Benutzers festlegen](/help/ios/c-mob-privacy-gdpr-ios/privacy.md).

## Weitere Informationen {#section_7C7124C50D85469C8C8714533FB1A37D}

* Weitere Informationen zur DSGVO finden Sie unter [DSGVO und Ihr Unternehmen](https://www.adobe.com/de/privacy/general-data-protection-regulation.html).
