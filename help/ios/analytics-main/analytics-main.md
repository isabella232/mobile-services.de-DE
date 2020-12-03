---
description: Diese Informationen helfen Ihnen bei der Verwendung des iOS SDK mit Adobe Analytics.
seo-description: Diese Informationen helfen Ihnen bei der Verwendung des iOS SDK mit Adobe Analytics.
seo-title: Übersicht über Analytics
solution: Experience Cloud,Analytics
title: Übersicht über Analytics
topic: Developer and implementation
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
translation-type: tm+mt
source-git-commit: bc11c1e7a4a11657ee89c40ddcbd37377ce50bb5
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 100%

---


# Übersicht über Analytics {#analytics}

Die Informationen in diesem Abschnitt helfen Ihnen beim Verwenden des iOS-SDK mit Adobe Analytics.

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie [hier](https://aep-sdks.gitbook.io/docs/), um unsere aktuelle Dokumentation abzurufen.

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDK können über [Experience Platform Launch](https://www.adobe.com/de/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.

## Analytics-Tracking-IDs generieren

In den SDK werden Identifikatoren verwendet, um Anwender zu verfolgen, und hier ist die Hierarchie der Identifikatoren:

1. Benutzerspezifische Besucher-ID (VID)
1. Analytics-Tracking-ID (AID)
1. Experience Cloud ID (MID)

>[!TIP]
>
>Das korrekte Akronym für Experience Cloud ID lautet ECID. Obwohl die SDK immer noch MID verwenden, ist dies der alte Name.

Die AID, die manchmal auch als Tracking Identifier bezeichnet wird, wird vom SDK generiert, wenn die App nicht für die Verwendung eines MID konfiguriert ist. Der Wert bleibt zwischen den Starts und den App-Upgrades in `NSUserDefaults` erhalten. Wenn der Anwender die App von seinem Gerät löscht und dann die App anschließend erneut installiert oder wenn der App-Entwickler `NSUserDefaults` löscht, wird vom SDK eine neue Kennung generiert. Dieser Vorgang führt zu einem neuen Benutzer in der Analytics-Berichterstellung.

Für Benutzer in einer App, die die Unterstützung für Identity Service (MID) einführt, werden vorhandene AID-Werte mit Analytics-Treffern gesendet, und der Analytics-Treffer enthält eine AID und eine MID. Für neue Benutzer in einer App mit Unterstützung für Identity Service enthalten die Analytics-Anfragen nur eine MID. Weitere Informationen zur Identifizierung von Besuchern finden Sie unter [Besucher-Kennung](https://docs.adobe.com/content/help/de-DE/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-calculate.html).
