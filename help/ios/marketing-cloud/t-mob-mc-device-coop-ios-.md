---
description: Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, um mit dem Einsatz der Experience Cloud-Gerätekooperation zu beginnen.
seo-description: Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, um mit dem Einsatz der Experience Cloud-Gerätekooperation zu beginnen.
seo-title: Experience Cloud-Gerätekooperation
title: Experience Cloud-Gerätekooperation
uuid: 434a6f8f-ec24-439d-95f0-a246b384b3b5
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Experience Cloud-Gerätekooperation {#experience-cloud-device-co-op}

Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, um mit dem Einsatz der Experience Cloud-Gerätekooperation zu beginnen.

Führen Sie die folgenden Schritte für die iOS-SDKs in Experience Cloud aus, um Ihre mobilen Apps für die Experience Cloud-Gerätekooperation zu aktivieren.

>[!IMPORTANT]
>
>Für diese Funktion ist iOS SDK Version 4.8.5 oder höher erforderlich.

Ab SDK-Version 4.16.1 können Teilnehmer an der Gerätekooperation die Daten ihres Mobilgeräts aus der Experience Cloud-Gerätekooperation ausschließen. Weitere Informationen finden Sie unter [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md) und die Methode `visitorAPI.js` für [isCoopSafe](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-coopsafe.html)

1. Adobe Mobile-SDK implementieren.

   Weitere Informationen finden Sie unter [Kernimplementierung und Lebenszyklus](/help/ios/getting-started/dev-qs.md).
1. Aktivieren Sie Ihre Experience Cloud ID.

   For more information, see [Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).
1. Übergeben Sie authentifizierte Identitäten, wie z. B. CRM-IDs oder gehashte E-Mails, mithilfe einer der hierin enthaltenen Synchronisierungsmethoden.

   Weitere Informationen finden Sie unter [Identitätsdienstmethoden](/help/ios/marketing-cloud/mc-methods.md)für Adobe Experience Platform.

## `coopUnsafe` Kennzeichen

Here is some additional information on the `coopUnsafe` flag:

* Mindestens SDK-Version 4.16.1
* The Boolean property of the `marketingCloud` object that, when set to `true`, causes the device to be opted-out of the Experience Cloud's Device Co-Op.
* Der Standardwert ist `false`.
* Diese Einstellung wird **nur** für Kunden verwendet, die an der Gerätekooperation teilnehmen.

Bei Mitgliedern mit Gerätekooperation, für die dieser Wert `true` sein muss, müssen Sie sich an das Kooperationsteam wenden, um eine Blacklist-Markierung auf Ihrem Gerätekooperationskonto zu verlangen. Es gibt keinen Self-Service-Pfad zum Aktivieren dieser Kennzeichnungen.

Beachten Sie die folgenden Informationen:

* When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
* Wenn Sie die serverseitige Weiterleitung von Analytics an Audience Manager aktivieren, sehen Sie auch `coop_unsafe=1` in den Analytics-Treffern.


