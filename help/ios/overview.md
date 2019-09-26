---
description: Mithilfe von iOS SDK 4.x für Experience Cloud-Lösungen können Sie native Apple iPhone- und iPad-Anwendungen messen, zielgruppenorientierte Inhalte in Ihren Apps bereitstellen und Zielgruppendaten über Audience Manager nutzen und erfassen.
seo-description: Mithilfe von iOS SDK 4.x für Experience Cloud-Lösungen können Sie native Apple iPhone- und iPad-Anwendungen messen, zielgruppenorientierte Inhalte in Ihren Apps bereitstellen und Zielgruppendaten über Audience Manager nutzen und erfassen.
seo-title: iOS-SDK 4.x für Experience Cloud-Lösungen
solution: Marketing Cloud,Analytics
title: iOS-SDK 4.x für Experience Cloud-Lösungen
topic: Entwickler und Implementierung
uuid: 8b374cee-1432-460b-aac2-70623dd80a04
translation-type: tm+mt
source-git-commit: a16fe85f44d2ce852e806b2cc41fb5d40952ad6d

---


# iOS-SDK 4.x für Experience Cloud-Lösungen{#ios-sdk-x-for-experience-cloud-solutions}

Mithilfe von iOS SDK 4.x für Experience Cloud-Lösungen können Sie native Apple iPhone- und iPad-Anwendungen messen, zielgruppenorientierte Inhalte in Ihren Apps bereitstellen und Zielgruppendaten über Audience Manager nutzen und erfassen.

>[!IMPORTANT]
>
>Die Adobe Analytics Mobile Marketing Add-on-SKU ist erforderlich, um Mobile Services den Zugriff auf Funktionen für mobile Akquise, Deep-Linking, Geolocation und mobiles Messaging zu ermöglichen. For more information, contact your Adobe CSM.

>[!IMPORTANT]
>
>Das iOS-SDK 4.x für Experience Cloud-Lösungen unterstützt jetzt [iOS 13 und Xcode 11](https://developer.apple.com/ios/). Um eine nahtlose Kompatibilität sicherzustellen, verwenden Sie die neuesten Versionen der 4.x iOS SDKs. Weitere Informationen zur neuesten Version finden Sie in den [Versionshinweisen](/help/ios/rel-notes.md).

## Neue Adobe Experience Cloud SDK-Version

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* Gehen Sie zu Launch, um zu beginnen.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-App messaging, push notifications or Acquisition links. Weitere Informationen finden Sie unter [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

Berücksichtigen Sie Folgendes:

* iOS 5 oder neuer wird unterstützt

   Für iOS 11 oder neuer **müssen** Sie über SDK-Version 4.13.8 oder neuer verfügen.

* In Version 4.2 dieses SDK und höher werden nun alle Treffer mithilfe von „HTTP POST“ gesendet.

   Dies hat keine Auswirkungen auf die erfassten oder berichteten Daten. Sie müssen jedoch einen Paketanalysator verwenden, der die Überprüfung von POST-Daten unterstützt, um Treffer anzuzeigen.

* If you are upgrading from a previous version (2.x or 3.x), see the [4.x Migration Guide](/help/ios/getting-started/migration-v3.md).

## Adobe Mobile-Benutzerdokumentation {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile Services bietet eine neue Benutzeroberfläche, auf der mobile Marketingfunktionen für mobile Anwendungen aus der gesamten Adobe Experience Cloud kombiniert werden. Zunächst bietet der Mobile-Dienst eine nahtlose Integration von App-Analyse- und Targeting-Funktionen aus den Adobe Analytics-, Adobe Audience Manager- und Adobe Target-Lösungen sowie dem Identitätsdienst für Adobe Experience Platform.

Lesen Sie [Adobe Mobile Services](/help/using/home.md), um weitere Informationen zur Mobile Services-Benutzeroberfläche zu erhalten und um die Benutzerdokumentation zu lesen.

## Bloodhound verwenden

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been
sunset. Seit dem 1. Mai 2017 wurde keine Verbesserung mehr vorgenommen und es wird kein zusätzlicher Engineering- oder Adobe Expert Care-Support mehr angeboten.
