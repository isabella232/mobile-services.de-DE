---
description: Das Android-SDK 4.x für Experience Cloud-Lösungen ermöglicht Ihnen die Messung nativer Android-Anwendungen, die Bereitstellung gezielter Inhalte in Ihrer App und die Erfassung und Nutzung von Zielgruppendaten über Zielgruppen-Management.
keywords: android;library;mobile;sdk
seo-description: Das Android-SDK 4.x für Experience Cloud-Lösungen ermöglicht Ihnen die Messung nativer Android-Anwendungen, die Bereitstellung gezielter Inhalte in Ihrer App und die Erfassung und Nutzung von Zielgruppendaten über Zielgruppen-Management.
seo-title: Android-SDK 4.x für Experience Cloud-Lösungen
solution: Marketing Cloud, Analytics
title: Android-SDK 4.x für Experience Cloud-Lösungen
topic: Entwickler und Implementierung
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Android SDK 4.x for Experience Cloud solutions{#android-sdk-x-for-experience-cloud-solutions}

Das Android-SDK 4.x für Experience Cloud-Lösungen ermöglicht Ihnen die Messung nativer Android-Anwendungen, die Bereitstellung gezielter Inhalte in Ihrer App und die Erfassung und Nutzung von Zielgruppendaten über Zielgruppen-Management.

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.

>[!IMPORTANT]
>
>Die Adobe Analytics Mobile Marketing Add-on-SKU ist erforderlich, um Mobile Services den Zugriff auf Funktionen für mobile Akquise, Deep-Linking, Geolocation und mobiles Messaging zu ermöglichen. Weitere Informationen erhalten Sie von Ihrem Adobe-CSM.

>[!IMPORTANT]
>
>Obwohl Sie Funktionen in der Benutzeroberfläche konfigurieren können, funktionieren diese Funktionen erst, wenn Sie die generierte Konfigurationsdatei herunterladen und diese Datei zum SDK hinzufügen. Informationen zum Herunterladen und Konfigurieren der SDKs finden Sie unter [Core-Implementierung und Lebenszyklus](/help/android/getting-started/dev-qs.md).

Die SDKs unterstützen die folgenden Android-Versionen:

* Version 4.6.0 oder früher unterstützt Android 2.2 (API 8) – Android 5.1.1 (API 22)
* Version 4.6.1 oder später unterstützt Android 2.3 (API 9) oder später

Berücksichtigen Sie Folgendes:

* Ab Version 4.2 werden Treffer mithilfe der HTTP-POST-Methode gesendet.

   This has no impact on the data that is collected or reported, but you need to use a packet analyzer that supports inspecting POST data to view hits.

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
