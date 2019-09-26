---
description: Mobile SDKs für die Experience Cloud verfügen über mit die Datenschutz-Grundverordnung (DSGVO) konforme APIs für Datenverantwortliche, die es Benutzern ermöglichen, lokal gespeicherte Identitäten abzurufen und Auswahlstatuskennzeichnungen für die Datenerfassung und -übertragung festzulegen.
seo-description: Mobile SDKs für die Experience Cloud verfügen über mit die Datenschutz-Grundverordnung (DSGVO) konforme APIs für Datenverantwortliche, die es Benutzern ermöglichen, lokal gespeicherte Identitäten abzurufen und Auswahlstatuskennzeichnungen für die Datenerfassung und -übertragung festzulegen.
seo-title: Privatsphäre und Datenschutz-Grundverordnung
title: Privatsphäre und Datenschutz-Grundverordnung
uuid: 69bb82de-1993-440c-a1b0-8d37919b48b6
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Privatsphäre und Datenschutz-Grundverordnung {#privacy-and-general-data-protection-regulation}

Mobile SDKs für die Experience Cloud verfügen über mit die Datenschutz-Grundverordnung (DSGVO) konforme APIs für Datenverantwortliche, die es Benutzern ermöglichen, lokal gespeicherte Identitäten abzurufen und Auswahlstatuskennzeichnungen für die Datenerfassung und -übertragung festzulegen.

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

## New Adobe Experience Platform Mobile SDK Release

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* To get started, go to Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.

## Übersicht

Wenn Adobe einem Unternehmen Software und Dienstleistungen bereitstellt, tritt Adobe als Datenverarbeiter für alle personenbezogenen Daten auf, die im Rahmen dieser Dienstleistungen gespeichert und verarbeitet werden. Als Datenverarbeiter verarbeitet Adobe personenbezogene Daten in Einklang mit den unserem Unternehmen gewährten Befugnissen und den uns erteilten Anweisungen (Informationen hierzu finden Sie beispielsweise in Ihrer mit Adobe getroffenen Vereinbarung).

Als Datenverantwortlicher können Sie SDKs von Adobe Mobile Services nutzen, um DSGVO-konform Abruf- und Löschanforderungen über Ihre Apps zu verarbeiten.

Für die Adobe Mobile SDK-Abschnitte Ihrer Mobil-Apps können Sie folgende Einstellungen und Verfahren nutzen:

* Nutzen Sie zum Abrufen von Daten aus SDKs und für die Übermittlung der Daten an Ihre Server die Methode `getAllIdentifiersAsync`.

   For more information, see Retrieving Stored Identifiers.[](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)

* Möchten Sie die Statusauswahl festlegen und im Rahmen der DSGVO gestellte Löschanfragen verarbeiten, legen Sie folgenden Status fest:

   * `privacyDefault`
   * `setPrivacyStatus`
   For more information, see Setting the User's Opt Status.[](/help/ios/c-mob-privacy-gdpr-ios/privacy.md)

## Weitere Informationen {#section_7C7124C50D85469C8C8714533FB1A37D}

* Weitere Informationen zur DSGVO finden Sie in unserem Artikel über die [DSGVO und Ihr Unternehmen](https://www.adobe.com/privacy/general-data-protection-regulation.html).
* Die Dokumentation zur DSGVO API finden Sie auf der Seite [Datenschutz-Grundverordnung API](https://adobe.io/apis/cloudplatform/gdpr.html).

