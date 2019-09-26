---
description: Diese Informationen helfen Ihnen beim Verwenden des iOS-SDK mit Adobe Analytics.
seo-description: Diese Informationen helfen Ihnen beim Verwenden des iOS-SDK mit Adobe Analytics.
seo-title: Überblick über Analytics
solution: Marketing Cloud, Analytics
title: Überblick über Analytics
topic: Entwickler und Implementierung
uuid: 8c7fb76a-be0b-4465-8151-ece7bad11b55
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Überblick über Analytics {#analytics}

Die Informationen in diesem Abschnitt unterstützen Sie bei der Verwendung des iOS-SDK mit Adobe Analytics.

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.

## Generieren von Analytics-Verfolgungskennungen

In den SDKs werden Identifikatoren verwendet, um Anwender zu verfolgen, und hier ist die Hierarchie der Identifikatoren:

1. Benutzerdefinierte Besucherkennung (Visitor Identifier, VID)
2. Analyse-Tracking-Kennung (Analytics Tracking Identifier, AID)
3. Experience Cloud-Kennung (Experience Cloud Identifier, MID)

>[!TIP]
>
>Die korrekte Abkürzung für Experience Cloud Identifier lautet ECID. Obwohl die SDKs immer noch MID verwenden, ist dies der alte Name.
Die AID, die manchmal auch als Tracking Identifier bezeichnet wird, wird vom SDK generiert, wenn die App nicht für die Verwendung eines MID konfiguriert ist. Der Wert bleibt zwischen den Starts und den App-Upgrades in `NSUserDefaults` erhalten. Wenn der Anwender die App von seinem Gerät löscht und dann die App anschließend erneut installiert oder wenn der App-Entwickler `NSUserDefaults` löscht, wird vom SDK eine neue Kennung generiert. Dieser Prozess führt zu einem neuen Anwender im Analytics-Reporting.

Für Anwender in einer App, die Identity Service Support (MID) einführt, werden bestehende AID-Werte mit Analytics-Treffern gesendet, und der Analytics-Treffer enthält eine AID und einen MID. Für neue Anwender in einer App mit Identity Service Support enthalten die Analytics-Anfragen nur eine MID. For more information about identifying visitors, see [Identify visitors](https://docs.adobe.com/content/help/en/analytics/export/analytics-data-feed/data-feed-contents/datafeeds-visid.html).
