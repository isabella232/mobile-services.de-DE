---
description: Das Android-SDK 4.x für Experience Cloud-Lösungen ermöglicht Ihnen die Messung nativer Android-Anwendungen, die Bereitstellung gezielter Inhalte in Ihrer App und die Erfassung und Nutzung von Zielgruppendaten über Zielgruppen-Management.
keywords: android; library; mobile; sdk
seo-description: Das Android-SDK 4.x für Experience Cloud-Lösungen ermöglicht Ihnen die Messung nativer Android-Anwendungen, die Bereitstellung gezielter Inhalte in Ihrer App und die Erfassung und Nutzung von Zielgruppendaten über Zielgruppen-Management.
seo-title: Android-SDK 4.x für Experience Cloud-Lösungen
solution: Marketing Cloud, Analytics
title: Android-SDK 4.x für Experience Cloud-Lösungen
topic: Entwickler und Implementierung
uuid: 56 f 1 ff 41-0365-41 dd-bdde -245 c 823 dff 7
translation-type: tm+mt
source-git-commit: 3b744229b3fc288363be74c3c4adcd71ecc4fad4

---


# Android SDK 4.x for Experience Cloud solutions{#android-sdk-x-for-experience-cloud-solutions}

Das Android-SDK 4.x für Experience Cloud-Lösungen ermöglicht Ihnen die Messung nativer Android-Anwendungen, die Bereitstellung gezielter Inhalte in Ihrer App und die Erfassung und Nutzung von Zielgruppendaten über Zielgruppen-Management.

>[!IMPORTANT]
>
>Die Adobe Analytics Mobile Marketing Add-on SKU ist erforderlich, um Mobile Services-Zugriff auf Akquise, Deep-Linking, Geolocation und mobile Messaging-Funktionen zu ermöglichen. Weitere Informationen erhalten Sie von Ihrem Adobe-Kundenbetreuer.

## Neue Adobe Experience Cloud SDK-Version

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

>[!IMPORTANT]
>
>Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* Gehen Sie zu [Launch](https://launch.adobe.com/), um zu beginnen.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Weitere Informationen finden Sie unter [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

>[!IMPORTANT]
>
>Obwohl Sie Funktionen in der Benutzeroberfläche konfigurieren können, funktionieren diese Funktionen erst, wenn Sie die generierte Konfigurationsdatei herunterladen und diese Datei dem SDK hinzufügen. Informationen zum Herunterladen und Konfigurieren der sdks finden Sie unter [Core-Implementierung und Lebenszyklus](/help/android/getting-started/dev-qs.md).

Die SDKs unterstützen die folgenden Android-Versionen:

* Version 4.6.0 oder früher unterstützt Android 2.2 (API 8) – Android 5.1.1 (API 22)
* Version 4.6.1 oder später unterstützt Android 2.3 (API 9) oder später

Berücksichtigen Sie Folgendes:

* Ab Version 4.2 werden Treffer mithilfe der HTTP-POST-Methode gesendet.

   Dies wirkt sich nicht auf die erfassten oder gemeldeten Daten aus. Sie müssen jedoch einen Paket-Analyzer verwenden, der die Überprüfung von POST-Daten unterstützt, um Treffer anzuzeigen.

* If you are upgrading from a previous version, see the [4.x Migration Guide](/help/android/getting-started/migration-v3.md).

## Adobe Mobile user documentation {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services bietet eine Benutzeroberfläche, die mobile Marketingfunktionen für mobile Anwendungen aus der gesamten Adobe Experience Cloud kombiniert. Weitere Informationen zur Benutzeroberfläche sowie die Benutzerdokumentation finden Sie unter [Adobe Mobile Services](https://marketing.adobe.com/resources/help/en_US/mobile/).

## Versionshinweise {#section_F8181DC052D44DD2A99AB40A41F6792C}

Neueste Informationen zu Experience Cloud-Versionen finden Sie unter [Experience Cloud-Versionshinweise](https://marketing.adobe.com/resources/help/en_US/whatsnew/).

## Bloodhound verwenden

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. Seit dem 1. Mai 2017 wurde keine Verbesserung mehr vorgenommen und es wird kein zusätzlicher Engineering- oder Adobe Expert Care-Support mehr angeboten.
