---
product: mobile-services
audience: Endanwender
user-guide-title: Mobile Services Android-Hilfe
translation-type: tm+mt
source-git-commit: e3bbde6c27d583ff3ee8b7e86c8e6e73595f5067

---


# Mobile Services Android-Hilfe{#android}

+ [Android-SDK 4.x für Experience Cloud-Lösungen](overview.md)
+ [Versionshinweise](rel-notes.md)
+ Erste Schritte{#getting-started-android}
   + [Erste Schritte](getting-started/getting-started.md)
   + [Before you start](getting-started/requirements.md)
   + [Kernimplementierung und Lebenszyklus](getting-started/dev-qs.md)
   + [Processing rules and context data](getting-started/proc-rules.md)
   + [Migration zur Android 4.x-Bibliothek](getting-started/migration-v3.md)
+ Konfiguration{#configuration-android}
   + [Konfigurationsübersicht](configuration/configuration.md)
   + [ADBMobile JSON-Konfigurationsdatei](configuration/json-config/json-config.md)
   + [ADBMobile JSON-Konfigurationspfad überschreiben](configuration/json-config/json-config-remote.md)
   + [Stapelverarbeitung von Treffern](configuration/hit-batching.md)
   + [Konfigurationsmethoden](configuration/methods.md)
+ [Lebenszyklusmetriken](metrics.md)
+ Analytics{#analytics-android}
   + [Überblick über Analytics](analytics-main/analytics-main.md)
   + [App-Zustände verfolgen](analytics-main/states.md)
   + [App-Aktionen verfolgen](analytics-main/actions.md)
   + [Nachverfolgen von App-Abstürzen](analytics-main/crashes.md)
   + [Timed actions](analytics-main/timed-actions.md)
   + [Lebenszeitwert des Besuchers](analytics-main/lifetime-value.md)
   + Products variable{#products-variable}
      + [Products variable](analytics-main/products/products.md)
      + [Products variable with merchandising eVars and product-specific events](analytics-main/products/products-variable-evars-events.md)
   + [Ereignis-Serialisierung](analytics-main/event-serialization.md)
   + [Video-Analytics](analytics-main/video-qs.md)
   + Postbacks{#postbacks}
      + [Übersicht über Postbacks](analytics-main/postbacks/postbacks.md)
      + [Beispiel für Postbacks](analytics-main/postbacks/postback-example.md)
      + [Postbacks personenbezogener Daten](analytics-main/postbacks/c-pii-postbacks.md)
   + [Analysemethoden](analytics-main/analytics-methods.md)
+ Akquise{#acquisition-android}
   + [Überblick über die Akquise](acquisition-main/acquisition-main-android.md)
   + [Akquise mobiler Apps](acquisition-main/acquisition.md)
   + [Akquise-Methoden](acquisition-main/acquisition-methods.md)
   + Tracking deep links{#tracking-deep-links}
      + [Tracking deep links](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Verfolgen von verzögerten Deep-Links von Drittanbietern](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [Test der Akquise von Marketing-Links](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [Prüfung der V3-Akquise](acquisition-main/t-testing-version-3-acquisition.md)
   + [Prüfung der Akquise älterer Menschen](acquisition-main/t-testing-acquisition.md)
   + [Fehlerbehebung bei Akquise-Tests](acquisition-main/troubleshoot-acquisition-testing.md)
+ Messaging{#messaging-android}
   + [Nachrichtenübersicht](messaging-main/messaging-main-android.md)
   + In-App-Nachrichten{#inapp-messaging}
      + [In-App-Nachrichten](messaging-main/messaging/messaging.md)
      + [Fehlerbehebung bei In-App-Nachrichten](messaging-main/messaging/in-apps-ts.md)
   + Push messaging{#push-messaging}
      + [Push-Nachrichten](messaging-main/push-messaging/push-messaging.md)
      + [Implementieren von Push-Nachrichten mit Deep-Linking](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [Rich-Push-Benachrichtigungen empfangen](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [Fehlerbehebung bei Push-Nachrichten](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Position{#location}
   + [Standortübersicht](location/location.md)
   + [Geografischer Standort und Zielpunkte](location/geo-poi.md)
   + [Beacon-Verfolgung](location/beacon.md)
+ Target{#target-android}
   + [Target overview](target-main/target-main.md)
   + [Zielkonfiguration](target-main/target.md)
   + [Target-Methoden](target-main/c-target-methods.md)
   + [Vorabruf für Android-Angebotsinhalte](target-main/c-mob-target-prefetch-android.md)
   + [Target-Vorschau auf Android](target-main/c-mob-target-preview-android.md)
+ Experience Cloud{#experience-cloud-android}
   + [Übersicht über Experience Cloud](c-marketing-cloud/c-marketing-cloud.md)
   + [Experience Cloud ID-Konfiguration](c-marketing-cloud/mcvid.md)
   + [Adobe Experience Platform Identity Service methods](c-marketing-cloud/mc-methods.md)
   + [Experience Cloud-Gerätekooperation](c-marketing-cloud/t-mob-mc-device-coop-android-.md)
+ Audience Manager{#audience-manager-android}
   + [Überblick über Audience Manager](audience-manager/audience-manager.md)
   + [Audience Manager configuration](audience-manager/audiencemgmt.md)
   + [Audience Manager methods](audience-manager/c-audience-manager-methods.md)
+ Wearables{#wearables-android}
   + [Übersicht über die Variablen](wearables/wearables.md)
   + [Android Wearables: Erste Schritte](wearables/android-wearable.md)
   + [Android Wearables: zusätzliche Hinweise](wearables/c-android-wearables--additional-notes.md)
+ Android SDK reference{#sdk-reference-android}
   + [Android SDK-Referenz - Übersicht](/help/android/reference/reference.md)
   + [App-IDs](/help/android/reference/app-ids.md)
   + [Visitor tracking between an app and mobile web](/help/android/reference/hybrid-app.md)
   + [Android-Widgets](/help/android/reference/widgets.md)
+ Privatsphäre und Datenschutz-Grundverordnung{#gdpr-privacy-android}
   + [Privacy and GDPR overview](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [Abrufen gespeicherter IDs](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [Festlegen des Opt-Status des Benutzers](c-mob-privacy-gdpr-android/privacy.md)
+ PhoneGap-Plug-in{#phonegap-android}
   + [Überblick über das PhoneGap-Plug-in](phonegap/phonegap.md)
   + [PhoneGap-Plug-in-Methoden](phonegap/phonegap-methods.md)
