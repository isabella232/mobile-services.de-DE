---
description: Wenden Sie sich an einen Adobe-Support-Mitarbeiter, um mit der Verwendung der Experience Cloud-Gerätekooperation zu beginnen.
seo-description: Wenden Sie sich an einen Adobe-Support-Mitarbeiter, um mit der Verwendung der Experience Cloud-Gerätekooperation zu beginnen.
seo-title: Experience Cloud-Gerätekooperation
title: Experience Cloud-Gerätekooperation
uuid: 7bb8a19c-4b80-4911-879d-f9941baa3b62
translation-type: tm+mt
source-git-commit: 86ba045b44bf6553e80727c0d61ccdd9a552d16c
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 90%

---


# Experience Cloud-Gerätekooperation {#experience-cloud-device-co-op}

Wenden Sie sich an einen Adobe-Support-Mitarbeiter, um mit der Verwendung der Experience Cloud-Gerätekooperation zu beginnen.

Um Ihre mobilen Apps für die Experience Cloud-Gerätekooperation zu aktivieren, führen Sie die folgenden Schritte für die Experience Cloud-Android-SDK aus:

>[!IMPORTANT]
>
>Für diese Funktion ist die Android-SDK-Version 4.8.3 oder höher erforderlich.

Ab SDK-Version 4.16.1 können Mitglieder der Gerätekooperation per Opt-out ihre Mobilgerätedaten aus der Experience Cloud-Gerätekooperation abwählen. Weitere Informationen finden Sie unter [ADBMobile JSON Config](/help/android/configuration/json-config/json-config.md) und in der `visitorAPI.js` Methode für [isCoopSafe](https://docs.adobe.com/content/help/de-DE/id-service/using/id-service-api/configurations/coopsafe.html).

1. Adobe Mobile-SDK implementieren.

   Weitere Informationen finden Sie unter [Grundlegende Implementierung und Lebenszyklus](/help/android/getting-started/dev-qs.md).
1. Aktivieren Sie Ihre Experience Cloud ID.

   Weitere Informationen finden Sie unter [Experience Cloud ID-Konfiguration](/help/android/c-marketing-cloud/mcvid.md).
1. Geben Sie authentifizierte IDs, beispielsweise CRM-IDs oder E-Mails mit Hash, mithilfe einer der Synchronisierungsmethoden weiter.

   Weitere Informationen finden Sie unter [Identity-Dienst für Adobe Experience Platform](/help/android/c-marketing-cloud/mc-methods.md).

## `coopUnsafe`-Markierung

Hier sind einige zusätzliche Informationen über die `coopUnsafe`-Markierung:

* Mindestens SDK-Version 4.16.1
* Die boolesche Eigenschaft des Objekts `marketingCloud`, das, wenn auf `true` festgelegt, dazu führt, dass das Gerät aus der Experience Cloud-Gerätekooperation ausgeschlossen wird.
* Der Standardwert ist `false`.
* Diese Einstellung wird **nur** für Kunden verwendet, die an der Gerätekooperation teilnehmen.

For Device Co-op members who require this value set to `true`, you need to work with the Co-op team to request a blocklist flag on your Device Co-op account. Es gibt keinen Self-Service-Pfad zum Aktivieren dieser Kennzeichnungen.

Beachten Sie die folgenden Informationen:

* Wenn `coopUnsafe` auf `true` festgelegt ist, wird `coop_unsafe=1` immer an Audience Manager und Besucher-ID-Treffer angehängt.
* Wenn Sie die serverseitige Weiterleitung von Analytics an Audience Manager aktivieren, sehen Sie auch `coop_unsafe=1` Analytics-Treffer.