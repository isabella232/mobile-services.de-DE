---
description: Mobile SDKs für die Experience Cloud verfügen über mit die Datenschutz-Grundverordnung (DSGVO) konforme APIs für Datenverantwortliche, die es Benutzern ermöglichen, lokal gespeicherte Identitäten abzurufen und Auswahlstatuskennzeichnungen für die Datenerfassung und -übertragung festzulegen.
seo-description: Mobile SDKs für die Experience Cloud verfügen über mit die Datenschutz-Grundverordnung (DSGVO) konforme APIs für Datenverantwortliche, die es Benutzern ermöglichen, lokal gespeicherte Identitäten abzurufen und Auswahlstatuskennzeichnungen für die Datenerfassung und -übertragung festzulegen.
seo-title: Privatsphäre und Datenschutz-Grundverordnung
title: Privatsphäre und Datenschutz-Grundverordnung
uuid: 69 bb 82 de -1993-440 c-a 1 b 0-8 d 37919 b 48 b 6
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Privatsphäre und Datenschutz-Grundverordnung {#privacy-and-general-data-protection-regulation}

Mobile SDKs für die Experience Cloud verfügen über mit die Datenschutz-Grundverordnung (DSGVO) konforme APIs für Datenverantwortliche, die es Benutzern ermöglichen, lokal gespeicherte Identitäten abzurufen und Auswahlstatuskennzeichnungen für die Datenerfassung und -übertragung festzulegen.

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

Wenn Adobe einem Unternehmen Software und Dienstleistungen bereitstellt, tritt Adobe als Datenverarbeiter für alle personenbezogenen Daten auf, die im Rahmen dieser Dienstleistungen gespeichert und verarbeitet werden. Als Datenverarbeiter verarbeitet Adobe personenbezogene Daten in Einklang mit den unserem Unternehmen gewährten Befugnissen und den uns erteilten Anweisungen (Informationen hierzu finden Sie beispielsweise in Ihrer mit Adobe getroffenen Vereinbarung).

Als Datenverantwortlicher können Sie SDKs von Adobe Mobile Services nutzen, um DSGVO-konform Abruf- und Löschanforderungen über Ihre Apps zu verarbeiten.

## Neue Adobe Experience Cloud SDK-Version

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* Gehen Sie zu Launch, um zu beginnen.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Weitere Informationen finden Sie unter [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).


Für die Adobe Mobile SDK-Abschnitte Ihrer Mobil-Apps können Sie folgende Einstellungen und Verfahren nutzen:

* Nutzen Sie zum Abrufen von Daten aus SDKs und für die Übermittlung der Daten an Ihre Server die Methode `getAllIdentifiersAsync`.

   Weitere Informationen finden Sie unter [Abrufen gespeicherter Ids](/help/ios/c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md).

* Möchten Sie die Statusauswahl festlegen und im Rahmen der DSGVO gestellte Löschanfragen verarbeiten, legen Sie folgenden Status fest:

   * `privacyDefault`
   * `setPrivacyStatus`
   Weitere Informationen finden Sie unter [Einstellen des Ausschlussstatus des Benutzers](/help/ios/c-mob-privacy-gdpr-ios/privacy.md).

## Weitere Informationen {#section_7C7124C50D85469C8C8714533FB1A37D}

* Weitere Informationen zur DSGVO finden Sie in unserem Artikel über die [DSGVO und Ihr Unternehmen](https://www.adobe.com/privacy/general-data-protection-regulation.html).
* Die Dokumentation zur DSGVO API finden Sie auf der Seite [Datenschutz-Grundverordnung API](https://adobe.io/apis/cloudplatform/gdpr.html).

