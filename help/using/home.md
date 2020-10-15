---
description: Technische Dokumente für Adobe Mobile Services
seo-description: In diesem Handbuch werden die technische Dokumentation und die Selbsthilfe für Adobe Mobile Services vorgestellt, die Mobile Marketingfunktionen für Adobe Experience Cloud-Apps zusammenfasst, sodass Sie die Benutzerinteraktion mit den Apps verstehen und verbessern können.
seo-title: Adobe Mobile Services
solution: Experience Cloud, Analytics, Experience Cloud
title: Adobe Mobile Services
uuid: e86a77c9-4ff1-403f-a5a1-4afbdc4e6f68
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '622'
ht-degree: 100%

---


# Adobe Mobile Services {#adobe-mobile-services}

In diesem Handbuch werden die technische Dokumentation und die Selbsthilfe für Adobe Mobile Services vorgestellt, die Mobile Marketingfunktionen für Adobe Experience Cloud-Apps zusammenfasst, sodass Sie die Benutzerinteraktion mit den Apps verstehen und verbessern können.

>[!IMPORTANT]
>
>Die SKU des Adobe Analytics Mobile Marketing-Add-Ons ist erforderlich, um Mobile Services den Zugriff auf Funktionen für mobile Akquise, Deep-Linking, Geolocation und mobiles Messaging zu ermöglichen. Weitere Informationen erhalten Sie bei Ihrem Adobe CSM.

## Ankündigung der Einstellung des Supports von 4x SDKs

Am 30. September 2020 endet der Support durch die Kundenunterstützung und der Zugriff auf Foren. Kunden können aber weiterhin die SDKs der Version 4 herunterladen und verwenden. Das Adobe Experience Platform Mobile SDK (früher als v5 bezeichnet) unterstützt ausschließlich künftige Adobe Experience Cloud-Funktionen.

Weitere Informationen finden Sie in den [häufig gestellten Fragen](https://aep-sdks.gitbook.io/docs/version-4-sdk-end-of-support-faq) zur Einstellung des Supports.

Es wird empfohlen, nach Möglichkeit zum neuen Experience Platform Mobile SDK zu migrieren.

## Neue Adobe Experience Cloud SDK-Version

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie [hier](https://aep-sdks.gitbook.io/docs/), um unsere aktuelle Dokumentation abzurufen.

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDK können über [Experience Platform Launch](https://www.adobe.com/de/experience-platform/launch.html) konfiguriert werden.

* Gehen Sie zu Launch, um zu beginnen.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.

>[!IMPORTANT]
>
> Wenn Sie die Mobile SDK für Adobe Experience Platform mit Adobe Launch verwenden, **müssen** Sie außerdem die Adobe Analytics Mobile Services-Erweiterung installieren, um die Funktionen von Adobe Mobile Services wie In-App-Messaging, Push-Benachrichtigungen oder Akquise-Links zu verwenden. Weitere Informationen finden Sie unter [Adobe Analytics – Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services).

>[!IMPORTANT]
>
>Sie können zwar Funktionen in der Benutzeroberfläche konfigurieren, jedoch sind diese Funktionen nur verfügbar, wenn Sie die generierte Konfigurationsdatei herunterladen und zum SDK hinzufügen. Informationen zum Herunterladen und Konfigurieren der SDK finden Sie im Abschnitt *SDK-Dokumentation* auf dieser Seite.

Die neuesten Versionshinweise finden Sie unter [Experience Cloud-Versionshinweise](https://docs.adobe.com/content/help/de-DE/release-notes/experience-cloud/current.html).

## Häufige Themen {#section_AFFBC9EDDE5B4E4493A7C2896121A773}

Hier einige beliebte Themen in diesem Handbuch:

* [Erste Schritte](/help/using/gs/gs.md)
* [Anmelden](/help/using/gs/gs-signin.md)
* [Rollen und Berechtigungen](/help/using/gs/c-mob-roles-and-permissions.md)
* [Mobile Metriken](/help/using/gs/metrics/metrics.md)
* [Messaging](/help/using/in-app-messaging/in-app-messaging.md)
* [Akquise](/help/using/acquisition-main/acquisition-main.md)
* [Ort](/help/using/location/c-location-overview.md)
* [Häufig gestellte Fragen – Mobile Services](/help/using/faq-mobile.md)

## Entwickler

Im Folgenden finden Sie einige Links zur Unterstützung von Entwicklern:

* [Mobile SDK und Werkzeuge herunterladen](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/download-sdk.md)
* [Entwickler](https://docs.adobe.com/content/help/de-DE/analytics/implementation/home.html)

## Community-Ressourcen

Im Folgenden finden Sie einige zusätzliche Ressourcen:

* [Experience Cloud-Forum](https://forums.adobe.com/community/experience-cloud)
* [Adobe Experience Cloud-Community](https://helpx.adobe.com/de/marketing-cloud.html?promoid=KAWSE)
* [Ideenbörse](https://forums.adobe.com/community/experience-cloud/analytics-cloud/analytics)
* [Adobe-Schulungen und -Lernprogramme](https://helpx.adobe.com/de/learning.html?promoid=KAUDK)
* [Spezielle Lösungen](https://www.adobe.com/de/marketing-cloud.html)

## SDK-Dokumentation {#section_3A500233347C4305AB545E298A827CEA}

Zusätzlich zum Benutzerhandbuch können Sie die Software Development Kits (SDK) herunterladen, die ein angepasstes Paket mit einer vorausgefüllten Version der für die Adobe Mobile-Konfiguration Ihrer App erforderlichen Konfigurationsdatei enthalten.

Native Bibliotheken stehen für die folgenden Plattformen zur Verfügung:

* [Android-SDK 4.x für Experience Cloud-Lösungen](/help/android/overview.md)
* [iOS-SDK 4.x für Experience Cloud-Lösungen](/help/ios/overview.md)
* [Unity Plug-in für das iOS- und Android 4.x-SDK](/help/unity/get-started.md)
* [Xamarin-Komponenten für Experience Cloud-Lösungen mit SDK 4.x](/help/xamarin/get-started.md)
* [Universelles Windows-Plattform-SDK 4.x für Experience Cloud-Lösungen](/help/universal-windows/overview.md)
* [Windows 8.1 Universal App Store](/help/windows-appstore/overview.md)

   * [Windows Visual Studio-Erweiterungen für Experience Cloud-Lösungen mit SDK 4.x](/help/windows-appstore/extensions/win-vse-4x.md)

* [BlackBerry 10 SDK 4.x für Experience Cloud-Lösungen](/help/blackberry/overview.md)

## Webinar: Erste Schritte mit Adobe Mobile {#section_420EA66F39FE44B9B531ADF5F5465543}

Sehen Sie sich das Webinar *Erste Schritte mit Adobe Mobile* an. ([Abspielen](https://adobe.ly/PsxCFn))

[  ![](assets/webinar.png) ](https://adobe.ly/PsxCFn)
