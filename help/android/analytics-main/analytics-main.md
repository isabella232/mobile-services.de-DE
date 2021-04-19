---
description: Diese Informationen helfen Ihnen bei der Verwendung des Android SDK mit Adobe Analytics.
keywords: Android;Bibliothek;Mobile;SDK
seo-description: Diese Informationen helfen Ihnen bei der Verwendung des Android-SDK mit Adobe Analytics.
seo-title: Übersicht über Analytics
solution: Experience Cloud,Analytics
title: Übersicht über Analytics
topic-fix: Developer and implementation
uuid: cc9fa1d9-bc48-4d03-854a-f7b263580a91
exl-id: ed9f55e6-f3ab-4c1e-9a2f-1ee67a7b4c03
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 100%

---

# Übersicht über Analytics {#analytics}

Die Informationen in diesem Abschnitt helfen Ihnen beim Verwenden des Android-SDK mit Adobe Analytics.

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

Die AID, die manchmal auch als Tracking Identifier bezeichnet wird, wird vom SDK generiert, wenn die App nicht für die Verwendung eines MID konfiguriert ist. Der Wert bleibt zwischen den Starts und den App-Upgrades in `SharedPreferences` erhalten. Wenn der Anwender die App von seinem Gerät löscht und anschließend die App erneut installiert oder wenn der App-Entwickler SharedPreferences löscht, wird vom SDK eine neue Kennung generiert. Dieser Vorgang führt zu einem neuen Benutzer in der Analytics-Berichterstellung.

Für Benutzer in einer App, die die Unterstützung für Identity Service (MID) einführt, werden vorhandene AID-Werte mit Analytics-Treffern gesendet, und der Analytics-Treffer enthält eine AID und eine MID. Für neue Benutzer in einer App mit Unterstützung für Identity Service enthalten die Analytics-Anfragen nur eine MID. Weitere Informationen zur Identifizierung von Besuchern finden Sie unter [Besucher-Kennung](https://docs.adobe.com/content/help/de-DE/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-calculate.html).
