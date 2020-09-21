---
product: mobile-services
audience: end-user
user-guide-title: Handbuch zu Mobile Services iOS
breadcrumb-title: iOS Guide
translation-type: tm+mt
source-git-commit: 18ef20df0a32741685e35cee98a1adf4a1b823a1
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 97%

---


# Mobile Services iOS Guide {#ios}

+ [iOS-SDK 4.x für Experience Cloud-Lösungen](overview.md)
+ [Versionshinweise](rel-notes.md)
+ Erste Schritte {#getting-started-ios}
   + [Übersicht über die ersten Schritte](getting-started/getting-started.md)
   + [Vorbereitung](getting-started/requirements.md)
   + [Grundlegende Implementierung und Lebenszyklus](getting-started/dev-qs.md)
   + [Verarbeitungsregeln und Kontextdaten](getting-started/proc-rules.md)
   + [Swift-Integration](getting-started/swift-integration.md)
   + [Zur iOS-Bibliothek der Version 4.x migrieren](getting-started/migration-v3.md)
+ Konfiguration {#config-ios}
   + [Konfigurationsübersicht](configuration/configuration.md)
   + [ADBMobile JSON-Konfiguration](configuration/json-config/json-config.md)
   + [ADBMobile JSON-Konfigurationspfad überschreiben](configuration/json-config/json-config-remote.md)
   + [Stapelverarbeitung von Treffern](configuration/hit-batching.md)
   + [Konfigurationsmethoden](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [Lebenszyklusmetriken](metrics.md)
+ Analytics {#analytics-ios}
   + [Übersicht über Analytics](analytics-main/analytics-main.md)
   + [App-Zustände verfolgen](analytics-main/states.md)
   + [App-Aktionen verfolgen](analytics-main/actions.md)
   + [Nachverfolgen von App-Abstürzen](analytics-main/crashes.md)
   + [Zeitgesteuerte Aktionen](analytics-main/timed-actions.md)
   + [Besucherlebenszeitwert](analytics-main/lifetime-value.md)
   + Variable „products“ {#products-variable}
      + [Variable „products“](analytics-main/products/products.md)
      + [Variable „products“ mit Merchandising-eVars und produktspezifischen Ereignissen](analytics-main/products/products-variable-evars-events.md)
   + [Ereignis-Serialisierung](analytics-main/event-serialization.md)
   + [Video-Analytics](analytics-main/video-qs.md)
   + Postbacks {#postbacks}
      + [Übersicht über Postbacks](analytics-main/postback/postback.md)
      + [Postback-Beispiel](analytics-main/postback/postback-example.md)
      + [PII-Postbacks](analytics-main/postback/c-pii-postbacks.md)
   + [Analytics-Methoden](analytics-main/analytics-methods.md)
+ Akquise {#acquisition-ios}
   + [Übersicht über die Akquise](acquisition-main/acquisition-main.md)
   + [App-Akquise](acquisition-main/acquisition.md)
   + [Akquisemethoden](acquisition-main/c-acquisition-methods.md)
   + Deep-Links verfolgen {#tracking-deep-links}
      + [Deep-Links verfolgen](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Verzögerte Drittanbieter-Deep-Links verfolgen](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [Marketinglink-Akquise testen](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [V3-Akquise testen](acquisition-main/t-testing-version-3-acquisition.md)
   + [Testen der Legacy-Akquise](acquisition-main/t-testing-acquisition.md)
   + [Apple-Suchanzeigen](acquisition-main/c-apple-search-ads.md)
+ Messaging {#messaging-ios}
   + [Übersicht über Messaging](messaging-main/messaging-main.md)
   + In-App-Nachrichten {#in-app-messaging}
      + [In-App-Nachrichten](messaging-main/messaging/messaging.md)
      + [Fehlerbehebung von In-App-Nachrichten](messaging-main/messaging/in-apps-ts.md)
   + Push-Nachrichten {#push-messaging}
      + [Push-Nachrichten](messaging-main/push-messaging/push-messaging.md)
      + [Push-Nachrichten mit Deep-Links implementieren](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [Rich-Push-Benachrichtigungen empfangen](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [Fehlerbehebung für Push-Nachrichten](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Ort {#location-ios}
   + [Übersicht über die Funktion „Standort“](location/location.md)
   + [Geostandort und Zielpunkte](location/geo-poi.md)
   + [iBeacon-Verfolgung](location/ibeacon.md)
+ Target {#target-ios}
   + [Übersicht über Target](target-main/target-main.md)
   + [Target-Methoden](target-main/c-target-methods.md)
   + [Vorabruf-Angebotsinhalte in iOS](target-main/c-mob-target-prefetch-ios.md)
   + [Target-Vorschau auf iOS](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Übersicht über Experience Cloud](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Identity-Dienst-Methoden für Adobe Experience Platform](marketing-cloud/mc-methods.md)
   + [Experience Cloud-Gerätekooperation](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Audience Manager-Methoden](amm/aam-methods.md)
+ Apple TV-Implementierungen mit tvOS {#apple-tv-implementation-tvos-ios}
   + [Apple TV-Implementierungen mit tvOS](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [Adobe Target für TVML/TVJS](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [TVJS-Methoden](apple-tv-implementation-tvos/tvjs-methods.md)
+ Implementierung der iOS-Erweiterung {#ios-ext}
   + [Implementierung der iOS-Erweiterung](ios-ext/ios-ext.md)
   + [Implementierung einer eigenständigen Erweiterung](ios-ext/c-stand-alone-extension-implementation.md)
+ [Apple Watch-Implementierungen mit WatchOS 2](apple-watch-implementation-watchkit.md)
+ iOS-SDK-Referenz {#sdk-reference-ios}
   + [iOS-SDK-Referenz](reference/reference.md)
   + [App-IDs](reference/app-ids.md)
   + [Besucher zwischen einer App und dem mobilen Internet verfolgen](reference/hybrid-app.md)
   + [iOS-Geräteversionen](reference/device-versions.md)
+ Privatsphäre und Datenschutz-Grundverordnung{#privacy-gdpr-ios}
   + [Privatsphäre und Datenschutz-Grundverordnung](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [Gespeicherte IDs abrufen](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [Auswahlstatus eines Benutzers festlegen](c-mob-privacy-gdpr-ios/privacy.md)
+ PhoneGap-Plug-in {#phonegap-ios}
   + [PhoneGap-Plug-in](phonegap/phonegap.md)
   + [PhoneGap-Plug-in-Methoden](phonegap/phonegap-methods.md)
