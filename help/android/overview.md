---
description: Das Android-SDK 4.x für Experience Cloud-Lösungen ermöglicht Ihnen die Messung nativer Android-Anwendungen, die Bereitstellung gezielter Inhalte in Ihrer App und die Erfassung und Nutzung von Zielgruppendaten über Zielgruppen-Management.
keywords: android;library;mobile;sdk
seo-description: Das Android-SDK 4.x für Experience Cloud-Lösungen ermöglicht Ihnen die Messung nativer Android-Anwendungen, die Bereitstellung gezielter Inhalte in Ihrer App und die Erfassung und Nutzung von Zielgruppendaten über Zielgruppen-Management.
seo-title: Android-SDK 4.x für Experience Cloud-Lösungen
solution: Marketing Cloud,Analytics
title: Android-SDK 4.x für Experience Cloud-Lösungen
topic: Developer and implementation
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
translation-type: tm+mt
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa

---


# Android-SDK 4.x für Experience Cloud-Lösungen{#android-sdk-x-for-experience-cloud-solutions}

Das Android-SDK 4.x für Experience Cloud-Lösungen ermöglicht Ihnen die Messung nativer Android-Anwendungen, die Bereitstellung gezielter Inhalte in Ihrer App und die Erfassung und Nutzung von Zielgruppendaten über Zielgruppen-Management.

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie [hier](https://aep-sdks.gitbook.io/docs/), um unsere aktuelle Dokumentation abzurufen.

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDK können über [Experience Platform Launch](https://www.adobe.com/de/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.

>[!IMPORTANT]
>
>Die SKU des Adobe Analytics Mobile Marketing-Add-Ons ist erforderlich, um Mobile Services den Zugriff auf Funktionen für mobile Akquise, Deep-Linking, Geolocation und mobiles Messaging zu ermöglichen. Weitere Informationen erhalten Sie bei Ihrem Adobe CSM.

>[!IMPORTANT]
>
>Sie können zwar Funktionen in der Benutzeroberfläche konfigurieren, jedoch sind diese Funktionen nur verfügbar, wenn Sie die generierte Konfigurationsdatei herunterladen und zum SDK hinzufügen. Informationen zum Herunterladen und Konfigurieren der SDK finden Sie unter [Grundlegende Implementierung und Lebenszyklus](/help/android/getting-started/dev-qs.md).

Die SDK unterstützen die folgenden Android-Versionen:

* Version 4.6.0 oder früher unterstützt Android 2.2 (API 8) - Android 5.1.1 (API 22)
* Version 4.6.1 oder höher unterstützt Android 2.3(API 9) oder höher

Beachten Sie Folgendes:

* In Version 4.2 und höher werden alle Treffer jetzt mit HTTP POST gesendet.

   Dies hat keine Auswirkung auf die erfassten oder gemeldeten Daten. Sie müssen jedoch eine Paketanalyse durchführen, die das Untersuchen von POST-Daten zum Anzeigen von Treffern unterstützt.

* Lesen Sie beim Upgrade aus einer vorherigen Version das [Handbuch für die Migration auf 4.x](/help/android/getting-started/migration-v3.md).

## Adobe Mobile-Benutzerdokumentation {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services bietet eine Benutzeroberfläche, die mobile Marketingfunktionen für mobile Anwendungen aus der gesamten Adobe Experience Cloud kombiniert. Lesen Sie [Adobe Mobile Services](https://docs.adobe.com/content/help/de-DE/mobile-services/using/home.html), um weitere Informationen zur Mobile Services-Benutzeroberfläche zu erhalten und um die Benutzerdokumentation zu lesen.

## Versionshinweise {#section_F8181DC052D44DD2A99AB40A41F6792C}

Neueste Informationen zu Experience Cloud-Versionen finden Sie unter [Experience Cloud-Versionshinweise](https://docs.adobe.com/content/help/de-DE/release-notes/experience-cloud/current.html).

## Bloodhound verwenden

>[!IMPORTANT]
>
>Am **30. April 2017** wurde die Entwicklung von Adobe Bloodhound eingestellt. Seit dem 1. Mai 2017 wurde keine Verbesserung mehr vorgenommen und es wird kein zusätzlicher Engineering- oder Adobe Expert Care-Support mehr angeboten.
