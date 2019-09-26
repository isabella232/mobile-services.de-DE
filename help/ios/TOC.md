---
product: mobile-services
audience: Endanwender
user-guide-title: Mobile Services iOS-Hilfe
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Mobile Services iOS Help {#ios}

+ [iOS-SDK 4.x für Experience Cloud-Lösungen](overview.md)
+ [Versionshinweise](rel-notes.md)
+ Erste Schritte {#getting-started-ios}
   + [Getting started overview](getting-started/getting-started.md)
   + [Bevor Sie beginnen](getting-started/requirements.md)
   + [Kernimplementierung und Lebenszyklus](getting-started/dev-qs.md)
   + [Verarbeitungsregeln und Kontextdaten](getting-started/proc-rules.md)
   + [Swift integration](getting-started/swift-integration.md)
   + [Migrating to the 4.x iOS library](getting-started/migration-v3.md)
+ Konfiguration {#config-ios}
   + [Konfigurationsübersicht](configuration/configuration.md)
   + [ADBMobile JSON-Konfiguration](configuration/json-config/json-config.md)
   + [ADBMobile JSON-Konfigurationspfad überschreiben](configuration/json-config/json-config-remote.md)
   + [Stapelverarbeitung von Treffern](configuration/hit-batching.md)
   + [Konfigurationsmethoden](configuration/sdk-methods.md)
   + [App Transport Security](configuration/app-transport-security.md)
+ [Lebenszyklusmetriken](metrics.md)
+ Analytics {#analytics-ios}
   + [Analytics overview](analytics-main/analytics-main.md)
   + [App-Zustände verfolgen](analytics-main/states.md)
   + [App-Aktionen verfolgen](analytics-main/actions.md)
   + [Nachverfolgen von App-Abstürzen](analytics-main/crashes.md)
   + [Zeitgesteuerte Aktionen](analytics-main/timed-actions.md)
   + [Lebenszeitwert des Besuchers](analytics-main/lifetime-value.md)
   + Products variable {#products-variable}
      + [Produktvariable](analytics-main/products/products.md)
      + [Products variable with merchandising eVars and product-specific events](analytics-main/products/products-variable-evars-events.md)
   + [Ereignis-Serialisierung](analytics-main/event-serialization.md)
   + [Video-Analytics](analytics-main/video-qs.md)
   + Postbacks {#postbacks}
      + [Postbacks overview](analytics-main/postback/postback.md)
      + [Postback-Beispiel](analytics-main/postback/postback-example.md)
      + [PII postbacks](analytics-main/postback/c-pii-postbacks.md)
   + [Analytics methods](analytics-main/analytics-methods.md)
+ Akquise {#acquisition-ios}
   + [Acquisition overview](acquisition-main/acquisition-main.md)
   + [Akquise mobiler Apps](acquisition-main/acquisition.md)
   + [Akquise-Methoden](acquisition-main/c-acquisition-methods.md)
   + Tracking deep links {#tracking-deep-links}
      + [Tracking deep links](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Verfolgen von verzögerten Deep-Links von Drittanbietern](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deep-deferred-links.md)
   + [Testing Marketing Link acquisition](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Testing V3 acquisition](acquisition-main/t-testing-version-3-acquisition.md)
   + [Testing legacy acquisition](acquisition-main/t-testing-acquisition.md)
   + [Apple-Suchanzeigen](acquisition-main/c-apple-search-ads.md)
+ Messaging {#messaging-ios}
   + [Messaging overview](messaging-main/messaging-main.md)
   + In-App-Nachrichten {#in-app-messaging}
      + [In-App-Nachrichten](messaging-main/messaging/messaging.md)
      + [Fehlerbehebung bei In-App-Nachrichten](messaging-main/messaging/in-apps-ts.md)
   + Push messaging {#push-messaging}
      + [Push messaging](messaging-main/push-messaging/push-messaging.md)
      + [Implementieren von Push-Nachrichten mit Deep-Linking](messaging-main/push-messaging/t-mob-imp-push-deeplinking-ios-4x.md)
      + [Rich-Push-Benachrichtigungen empfangen](messaging-main/push-messaging/c-set-up-rich-push-notif-ios.md)
      + [Fehlerbehebung bei Push-Nachrichten](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Position {#location-ios}
   + [Location overview](location/location.md)
   + [Geografischer Standort und Zielpunkte](location/geo-poi.md)
   + [iBeacon-Verfolgung](location/ibeacon.md)
+ Target {#target-ios}
   + [Target overview](target-main/target-main.md)
   + [Target-Methoden](target-main/c-target-methods.md)
   + [Vorabruf-Angebotsinhalte in iOS](target-main/c-mob-target-prefetch-ios.md)
   + [Target-Vorschau auf iOS](target-main/c-mob-target-preview-ios.md)
+ Experience Cloud {#exp-cloud-ios}
   + [Experience Cloud overview](marketing-cloud/marketing-cloud.md)
   + [Experience Cloud ID](marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity Service Methods](marketing-cloud/mc-methods.md)
   + [Experience Cloud-Gerätekooperation](marketing-cloud/t-mob-mc-device-coop-ios-.md)
+ [Audience Manager methods](amm/aam-methods.md)
+ Apple TV implementation with tvOS {#apple-tv-implementation-tvos-ios}
   + [Apple TV-Implementierung mit tvOS](apple-tv-implementation-tvos/apple-tv-implementation-tvos.md)
   + [Adobe Target für TVML/TVJS](apple-tv-implementation-tvos/target-for-tvml-tvjs.md)
   + [TVJS-Methoden](apple-tv-implementation-tvos/tvjs-methods.md)
+ iOS extension implementation {#ios-ext}
   + [iOS-Erweiterungsimplementierung](ios-ext/ios-ext.md)
   + [Standalone-Erweiterung](ios-ext/c-stand-alone-extension-implementation.md)
+ [Apple Watch-Implementierung mit WatchOS 2](apple-watch-implementation-watchkit.md)
+ iOS SDK reference {#sdk-reference-ios}
   + [iOS SDK reference](reference/reference.md)
   + [App-IDs](reference/app-ids.md)
   + [Visitor tracking between an app and mobile web](reference/hybrid-app.md)
   + [iOS-Geräteversionen](reference/device-versions.md)
+ Privatsphäre und Datenschutz-Grundverordnung{#privacy-gdpr-ios}
   + [Privatsphäre und Datenschutz-Grundverordnung](c-mob-privacy-gdpr-ios/c-mob-privacy-gdpr-ios.md)
   + [Retrieving stored identifiers](c-mob-privacy-gdpr-ios/c-mob-gdpr-ret-stored-ids-ios.md)
   + [Setting the user's opt status](c-mob-privacy-gdpr-ios/privacy.md)
+ PhoneGap-Plug-in {#phonegap-ios}
   + [PhoneGap-Plug-in](phonegap/phonegap.md)
   + [PhoneGap plug-in methods](phonegap/phonegap-methods.md)
