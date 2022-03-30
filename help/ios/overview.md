---
description: Mithilfe von iOS SDK 4.x für Experience Cloud-Lösungen können Sie native Apple iPhone- und iPad-Anwendungen messen, zielgruppenorientierte Inhalte in Ihren Apps bereitstellen und Zielgruppendaten über Audience Manager nutzen und erfassen.
solution: Experience Cloud Services,Analytics
title: iOS SDK 4.x für Experience Cloud-Lösungen
topic-fix: Developer and implementation
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
exl-id: d4dbddf7-c8be-4936-adfb-2f7aa07a0dd4
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 100%

---

# iOS SDK 4.x für Experience Cloud-Lösungen{#ios-sdk-x-for-experience-cloud-solutions}

Mithilfe von iOS SDK 4.x für Experience Cloud-Lösungen können Sie native Apple iPhone- und iPad-Anwendungen messen, zielgruppenorientierte Inhalte in Ihren Apps bereitstellen und Zielgruppendaten über Audience Manager nutzen und erfassen.

>[!IMPORTANT]
>
>Ab Version 4.21.0 verfügt das SDK für iOS über eine erforderliche Mindestversion von Xcode 12. Wenn Sie Cocoapods verwenden, um Abhängigkeiten in Ihrer Applikation zu verwalten, erfordert das Adobe-SDK die Cocoapods-Version 1.10.0 oder höher.

Wenn Sie Version 4.21.0 oder höher verwenden, lesen Sie die Dokumentation und beachten Sie die folgenden Änderungen:

* Jedes Mal, wenn eine Binärbibliotheksdatei erwähnt wird, sollte stattdessen deren XCFramework-Ersatz verwendet werden:
   * `AdobeMobileLibrary.a` > `AdobeMobile.xcframework`
   * `AdobeMobileLibrary_Extension.a` > `AdobeMobileExtension.xcframework`
   * `AdobeMobileLibrary_Watch.a` > `AdobeMobileWatch.xcframework`
   * `AdobeMobileLibrary_TV.a` > `AdobeMobileTV.xcframework`
* Wenn Sie die Adobe XCFrameworks manuell zu Ihrem Projekt hinzufügen, stellen Sie sicher, dass sie nicht eingebettet sind.

>[!IMPORTANT]
>
>Die SKU des Adobe Analytics Mobile Marketing-Add-Ons ist erforderlich, um Mobile Services den Zugriff auf Funktionen für mobile Akquise, Deep-Linking, Geolocation und mobiles Messaging zu ermöglichen. Weitere Informationen erhalten Sie bei Ihrem Adobe CSM.

>[!IMPORTANT]
>
>Das iOS-SDK 4.x für Experience Cloud-Lösungen unterstützt jetzt [iOS 13 und Xcode 11](https://developer.apple.com/ios/). Um eine nahtlose Kompatibilität sicherzustellen, verwenden Sie die aktuellen Versionen der iOS-SDK der Version 4.x. Weitere Informationen zur aktuellen Version finden Sie in den [Versionshinweisen](/help/ios/rel-notes.md).

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie [hier](https://aep-sdks.gitbook.io/docs/), um unsere aktuelle Dokumentation abzurufen.

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über [Experience Platform Launch](https://www.adobe.com/de/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.

Beachten Sie Folgendes:

* iOS 8 oder neuer wird unterstützt.

   Für iOS 11 oder höher **müssen** Sie SDK-Version 4.13.8 oder höher haben.

* In Version 4.2 dieses SDK und höher werden nun alle Treffer mithilfe von „HTTP POST“ gesendet.

   Dies hat keine Auswirkung auf die erfassten oder gemeldeten Daten. Sie müssen jedoch eine Paketanalyse durchführen, die das Untersuchen von POST-Daten zum Anzeigen von Treffern unterstützt.

* Lesen Sie beim Upgrade aus einer vorherigen Version (2.x oder 3.x) das [Handbuch für die Migration auf 4.x](/help/ios/getting-started/migration-v3.md).

## Adobe Mobile-Benutzerdokumentation {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services bietet eine neue Benutzeroberfläche, auf der mobile Marketing-Funktionen für mobile Anwendungen aus der gesamten Adobe Experience Cloud kombiniert werden. Anfänglich stellt der Mobile-Service die nahtlose Integration der App-Analyse- und zielgruppenorientierten Funktionen aus den Lösungen Adobe Analytics, Adobe Audience Manager, Adobe Target und dem Identity-Dienst für Adobe Experience Platform bereit.

Lesen Sie [Adobe Mobile Services](/help/using/home.md), um weitere Informationen zur Mobile Services-Benutzeroberfläche zu erhalten und um die Benutzerdokumentation zu lesen.

## Bloodhound verwenden

>[!IMPORTANT]
>
>Am **30. April 2017** wurde die Entwicklung von Adobe Bloodhound eingestellt. Seit dem 1. Mai 2017 wurde keine Verbesserung mehr vorgenommen und es wird kein zusätzlicher Engineering- oder Adobe Expert Care-Support mehr angeboten.
