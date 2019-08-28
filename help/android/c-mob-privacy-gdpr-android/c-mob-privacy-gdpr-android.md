---
description: Mobile SDKs für die Experience Cloud verfügen über mit die Datenschutz-Grundverordnung (DSGVO) konforme APIs für Datenverantwortliche, die es Benutzern ermöglichen, lokal gespeicherte Identitäten abzurufen und Auswahlstatuskennzeichnungen für die Datenerfassung und -übertragung festzulegen.
seo-description: Mobile SDKs für die Experience Cloud verfügen über mit die Datenschutz-Grundverordnung (DSGVO) konforme APIs für Datenverantwortliche, die es Benutzern ermöglichen, lokal gespeicherte Identitäten abzurufen und Auswahlstatuskennzeichnungen für die Datenerfassung und -übertragung festzulegen.
seo-title: Übersicht über Datenschutz und allgemeine Datenschutzregeln
title: Übersicht über Datenschutz und allgemeine Datenschutzregeln
uuid: 56 d 6 f 155-efec -4 b 3 f-a 972-a 63155729167
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Privacy and General Data Protection Regulation overview {#privacy-and-general-data-protection-regulation}

Mobile SDKs für die Experience Cloud verfügen über mit die Datenschutz-Grundverordnung (DSGVO) konforme APIs für Datenverantwortliche, die es Benutzern ermöglichen, lokal gespeicherte Identitäten abzurufen und Auswahlstatuskennzeichnungen für die Datenerfassung und -übertragung festzulegen.

## Neue Adobe Experience Cloud SDK-Version

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

>[!IMPORTANT]
>
>Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* Gehen Sie zu [Launch](https://launch.adobe.com/), um zu beginnen.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

Wenn Adobe einem Unternehmen Software und Dienstleistungen bereitstellt, tritt Adobe als Datenverarbeiter für alle personenbezogenen Daten auf, die im Rahmen dieser Dienstleistungen gespeichert und verarbeitet werden. Als Datenverarbeiter verarbeitet Adobe personenbezogene Daten in Einklang mit den unserem Unternehmen gewährten Befugnissen und den uns erteilten Anweisungen (Informationen hierzu finden Sie beispielsweise in Ihrer mit Adobe getroffenen Vereinbarung).

Als Datenverantwortlicher können Sie SDKs von Adobe Mobile Services nutzen, um DSGVO-konform Abruf- und Löschanforderungen über Ihre Apps zu verarbeiten.

Für die Adobe Mobile SDK-Abschnitte Ihrer Mobil-Apps können Sie folgende Einstellungen und Verfahren nutzen:

* Nutzen Sie zum Abrufen von Daten aus SDKs und für die Übermittlung der Daten an Ihre Server die Methode `getAllIdentifiersAsync`.

   Weitere Informationen finden Sie unter [Abrufen gespeicherter Ids](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md).

* Möchten Sie die Statusauswahl festlegen und im Rahmen der DSGVO gestellte Löschanfragen verarbeiten, legen Sie folgenden Status fest:

   * `privacyDefault`
   * `setPrivacyStatus`
   Weitere Informationen finden Sie unter [Einstellen des Ausschlussstatus des Benutzers](/help/android/c-mob-privacy-gdpr-android/privacy.md).