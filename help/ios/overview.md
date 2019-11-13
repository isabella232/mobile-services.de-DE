---
description: Mithilfe von iOS SDK 4.x für Experience Cloud-Lösungen können Sie native Apple iPhone- und iPad-Anwendungen messen, zielgruppenorientierte Inhalte in Ihren Apps bereitstellen und Zielgruppendaten über Audience Manager nutzen und erfassen.
seo-description: Mithilfe von iOS SDK 4.x für Experience Cloud-Lösungen können Sie native Apple iPhone- und iPad-Anwendungen messen, zielgruppenorientierte Inhalte in Ihren Apps bereitstellen und Zielgruppendaten über Audience Manager nutzen und erfassen.
seo-title: iOS-SDK 4.x für Experience Cloud-Lösungen
solution: Experience Cloud,Analytics
title: iOS-SDK 4.x für Experience Cloud-Lösungen
topic: Entwickler und Implementierung
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
translation-type: ht
source-git-commit: cb4a549d889d169bdf8ab0bb997d5c95f44f073e

---


# iOS-SDK 4.x für Experience Cloud-Lösungen {#ios-sdk-x-for-experience-cloud-solutions}

Mithilfe von iOS SDK 4.x für Experience Cloud-Lösungen können Sie native Apple iPhone- und iPad-Anwendungen messen, zielgruppenorientierte Inhalte in Ihren Apps bereitstellen und Zielgruppendaten über Audience Manager nutzen und erfassen.

>[!IMPORTANT]
>
>Die SKU des Adobe Analytics Mobile Marketing-Add-Ons ist erforderlich, um Mobile Services den Zugriff auf Funktionen für mobile Akquise, Deep-Linking, Geolocation und mobiles Messaging zu ermöglichen. Weitere Informationen erhalten Sie bei Ihrem Adobe CSM.

>[!IMPORTANT]
>
>Das iOS-SDK 4.x für Experience Cloud-Lösungen unterstützt jetzt [iOS 13 und Xcode 11](https://developer.apple.com/ios/). Um eine nahtlose Kompatibilität sicherzustellen, verwenden Sie die aktuellen Versionen der iOS-SDK der Version 4.x. Weitere Informationen zur aktuellen Version finden Sie in den [Versionshinweisen](/help/ios/rel-notes.md).

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDK können über [Experience Platform Launch](https://www.adobe.com/de/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.

Beachten Sie Folgendes:

* iOS 8 oder neuer wird unterstützt.

   Für iOS 11 oder neuer **müssen** Sie über SDK-Version 4.13.8 oder neuer verfügen.

* In Version 4.2 dieses SDK und höher werden nun alle Treffer mithilfe von „HTTP POST“ gesendet.

   Dies hat keine Auswirkung auf die erfassten oder gemeldeten Daten. Sie müssen jedoch eine Paketanalyse durchführen, die das Untersuchen von POST-Daten zum Anzeigen von Treffern unterstützt.

* Lesen Sie beim Upgrade aus einer vorherigen Version (2.x oder 3.x) das [Handbuch für die Migration auf 4.x](/help/ios/getting-started/migration-v3.md).

## Adobe Mobile-Benutzerdokumentation {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services bietet eine neue Benutzeroberfläche, auf der mobile Marketingfunktionen für mobile Anwendungen aus der gesamten Adobe Experience Cloud kombiniert werden. Anfänglich stellt der Mobile-Service die nahtlose Integration der App-Analyse- und zielgruppenorientierten Funktionen aus den Lösungen Adobe Analytics, Adobe Audience Manager, Adobe Target und dem Identity-Dienst für Adobe Experience Platform bereit.

Lesen Sie [Adobe Mobile Services](/help/using/home.md), um weitere Informationen zur Mobile Services-Benutzeroberfläche zu erhalten und um die Benutzerdokumentation zu lesen.

## Bloodhound verwenden

>[!IMPORTANT]
>
>Am **30. April 2017** wurde die Entwicklung von Adobe Bloodhound eingestellt. Seit dem 1. Mai 2017 wurde keine Verbesserung mehr vorgenommen und es wird kein zusätzlicher Engineering- oder Adobe Expert Care-Support mehr angeboten.
