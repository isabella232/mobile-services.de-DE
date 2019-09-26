---
description: Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, um mit dem Einsatz der Experience Cloud-Gerätekooperation zu beginnen.
seo-description: Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, um mit dem Einsatz der Experience Cloud-Gerätekooperation zu beginnen.
seo-title: Experience Cloud-Gerätekooperation
title: Experience Cloud-Gerätekooperation
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud-Gerätekooperation {#experience-cloud-device-co-op}

Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, um mit dem Einsatz der Experience Cloud-Gerätekooperation zu beginnen.

Um Ihre mobilen Apps für die Experience Cloud-Gerätekooperation zu aktivieren, führen Sie die folgenden Schritte für die Experience Cloud-Android-SDKs aus:

>[!IMPORTANT]
>
>Für diese Funktion ist Android SDK Version 4.8.3 oder höher erforderlich.

Ab SDK-Version 4.16.1 können Teilnehmer an der Gerätekooperation die Daten ihres Mobilgeräts aus der Experience Cloud-Gerätekooperation ausschließen. Weitere Informationen finden Sie unter [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md) und die Methode `visitorAPI.js` für [isCoopSafe](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-coopsafe.html)

1. Adobe Mobile-SDK implementieren.

   For more information, see Core Implementation and Lifecycle.[](/help/android/getting-started/dev-qs.md)
1. Aktivieren Sie Ihre Experience Cloud ID.

   For more information, see [Experience Cloud ID Configuration](/help/android/c-marketing-cloud/mcvid.md).
1. Geben Sie authentifizierte IDs, beispielsweise CRM-IDs oder E-Mails mit Hash, mithilfe einer der Synchronisierungsmethoden weiter.

   For more information, see Adobe Experience Platform Identity Service Methods.[](/help/android/c-marketing-cloud/mc-methods.md)

## `coopUnsafe` flag

Hier sind einige zusätzliche Informationen über die `coopUnsafe`-Markierung:

* Mindestens SDK-Version 4.16.1
* The Boolean property of the `marketingCloud` object that, when set to `true`, causes the device to be opted-out of the Experience Cloud's Device Co-Op.
* Der Standardwert ist `false`.
* Diese Einstellung wird **nur** für Kunden verwendet, die an der Gerätekooperation teilnehmen.

Bei Mitgliedern mit Gerätekooperation, für die dieser Wert `true` sein muss, müssen Sie sich an das Kooperationsteam wenden, um eine Blacklist-Markierung auf Ihrem Gerätekooperationskonto zu verlangen. Es gibt keinen Self-Service-Pfad zum Aktivieren dieser Kennzeichnungen.

Beachten Sie die folgenden Informationen:

* When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
* If you enable Analytics server-side forwarding to Audience Manager, you will also see `coop_unsafe=1` Analytics hits.