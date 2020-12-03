---
description: Wenden Sie sich an einen Adobe-Support-Mitarbeiter, um mit der Verwendung der Experience Cloud-Gerätekooperation zu beginnen.
seo-description: Wenden Sie sich an einen Adobe-Support-Mitarbeiter, um mit der Verwendung der Experience Cloud-Gerätekooperation zu beginnen.
seo-title: Experience Cloud-Gerätekooperation
title: Experience Cloud-Gerätekooperation
uuid: 434a6f8f-ec24-439d-95f0-a246b384b3b5
translation-type: tm+mt
source-git-commit: 86ba045b44bf6553e80727c0d61ccdd9a552d16c
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 100%

---


# Experience Cloud-Gerätekooperation {#experience-cloud-device-co-op}

Wenden Sie sich an einen Adobe-Support-Mitarbeiter, um mit der Verwendung der Experience Cloud-Gerätekooperation zu beginnen.

Führen Sie die folgenden Schritte für die iOS-SDK in Experience Cloud aus, um Ihre mobilen Apps für die Experience Cloud-Gerätekooperation zu aktivieren.

>[!IMPORTANT]
>
>Für diese Funktion ist die iOS-SDK-Version 4.8.5 oder höher erforderlich.

Ab SDK-Version 4.16.1 können Mitglieder der Gerätekooperation per Opt-out ihre Mobilgerätedaten aus der Experience Cloud-Gerätekooperation abwählen. Weitere Informationen finden Sie unter [ADBMobile JSON Config](/help/ios/configuration/json-config/json-config.md) und in der `visitorAPI.js` Methode für [isCoopSafe](https://docs.adobe.com/content/help/de-DE/id-service/using/id-service-api/configurations/coopsafe.html).

1. Adobe Mobile-SDK implementieren.

   Weitere Informationen finden Sie unter [Grundlegende Implementierung und Lebenszyklus](/help/ios/getting-started/dev-qs.md).
1. Aktivieren Sie Ihre Experience Cloud ID.

   Weitere Informationen finden Sie unter [Experience Cloud ID](/help/ios/marketing-cloud/mcvid.md).
1. Übergeben Sie authentifizierte Identitäten, wie z. B. CRM-IDs oder gehashte E-Mails, mithilfe einer der hierin enthaltenen Synchronisierungsmethoden.

   Weitere Informationen finden Sie unter [Identity-Dienst für Adobe Experience Platform](/help/ios/marketing-cloud/mc-methods.md).

## `coopUnsafe`-Markierung

Im Folgenden finden Sie weitere Informationen zur `coopUnsafe`-Markierung:

* Mindestens SDK-Version 4.16.1
* Die boolesche Eigenschaft des Objekts `marketingCloud`, das, wenn auf `true` festgelegt, dazu führt, dass das Gerät aus der Experience Cloud-Gerätekooperation ausgeschlossen wird.
* Der Standardwert ist `false`.
* Diese Einstellung wird **nur** für Kunden verwendet, die an der Gerätekooperation teilnehmen.

Bei Mitgliedern mit Gerätekooperation, für die dieser Wert `true` sein muss, müssen Sie sich an das Kooperationsteam wenden, um eine Sperrlisten-Markierung auf Ihrem Gerätekooperationskonto zu verlangen. Es gibt keinen Self-Service-Pfad zum Aktivieren dieser Kennzeichnungen.

Beachten Sie die folgenden Informationen:

* Wenn `coopUnsafe` auf `true` festgelegt ist, wird `coop_unsafe=1` immer an Audience Manager und Besucher-ID-Treffer angehängt.
* Wenn Sie die serverseitige Weiterleitung von Analytics an Audience Manager aktivieren, sehen Sie auch `coop_unsafe=1` in den Analytics-Treffern.


