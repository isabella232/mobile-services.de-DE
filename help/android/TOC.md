---
product: mobile-services
audience: end-user
user-guide-title: Mobile Services - Android-Handbuch
breadcrumb-title: Android Guide
translation-type: tm+mt
source-git-commit: 18ef20df0a32741685e35cee98a1adf4a1b823a1
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 97%

---


# Mobile Services Android Guide{#android}

+ [Android-SDK 4.x für Experience Cloud-Lösungen](overview.md)
+ [Versionshinweise](rel-notes.md)
+ Erste Schritte{#getting-started-android}
   + [Erste Schritte](getting-started/getting-started.md)
   + [Vorbereitung](getting-started/requirements.md)
   + [Grundlegende Implementierung und Lebenszyklus](getting-started/dev-qs.md)
   + [Verarbeitungsregeln und Kontextdaten](getting-started/proc-rules.md)
   + [Migration zur Android 4.x-Bibliothek](getting-started/migration-v3.md)
+ Konfiguration{#configuration-android}
   + [Konfigurationsübersicht](configuration/configuration.md)
   + [ADBMobile JSON-Konfigurationsdatei](configuration/json-config/json-config.md)
   + [ADBMobile JSON-Konfigurationspfad überschreiben](configuration/json-config/json-config-remote.md)
   + [Stapelverarbeitung von Treffern](configuration/hit-batching.md)
   + [Konfigurationsmethoden](configuration/methods.md)
+ [Lebenszyklusmetriken](metrics.md)
+ Analytics{#analytics-android}
   + [Übersicht über Analytics](analytics-main/analytics-main.md)
   + [App-Zustände verfolgen](analytics-main/states.md)
   + [App-Aktionen verfolgen](analytics-main/actions.md)
   + [Nachverfolgen von App-Abstürzen](analytics-main/crashes.md)
   + [Zeitgesteuerte Aktionen](analytics-main/timed-actions.md)
   + [Besucherlebenszeitwert](analytics-main/lifetime-value.md)
   + Variable „products“{#products-variable}
      + [Variable „products“](analytics-main/products/products.md)
      + [Variable „products“ mit Merchandising-eVars und produktspezifischen Ereignissen](analytics-main/products/products-variable-evars-events.md)
   + [Ereignis-Serialisierung](analytics-main/event-serialization.md)
   + [Video-Analytics](analytics-main/video-qs.md)
   + Postbacks{#postbacks}
      + [Übersicht über Postbacks](analytics-main/postbacks/postbacks.md)
      + [Postback-Beispiel](analytics-main/postbacks/postback-example.md)
      + [Postbacks personenbezogener Daten](analytics-main/postbacks/c-pii-postbacks.md)
   + [Analytics-Methoden](analytics-main/analytics-methods.md)
+ Akquise{#acquisition-android}
   + [Übersicht über die Akquise](acquisition-main/acquisition-main-android.md)
   + [App-Akquise](acquisition-main/acquisition.md)
   + [Akquisemethoden](acquisition-main/acquisition-methods.md)
   + Deep-Links verfolgen{#tracking-deep-links}
      + [Deep-Links verfolgen](acquisition-main/tracking-deep-links/tracking-deep-links.md)
      + [Verzögerte Drittanbieter-Deep-Links verfolgen](acquisition-main/tracking-deep-links/c-tracking-3rd-party-deferred-deep-links.md)
   + [Marketinglink-Akquise testen](acquisition-main/t-testing-marketing-link-acquisition.md)
   + [V3-Akquise testen](acquisition-main/t-testing-version-3-acquisition.md)
   + [Testen der Legacy-Akquise](acquisition-main/t-testing-acquisition.md)
   + [Fehlerbehebung beim Akquisetest](acquisition-main/troubleshoot-acquisition-testing.md)
+ Messaging{#messaging-android}
   + [Übersicht über Messaging](messaging-main/messaging-main-android.md)
   + In-App-Nachrichten{#inapp-messaging}
      + [In-App-Nachrichten](messaging-main/messaging/messaging.md)
      + [Fehlerbehebung bei In-App-Nachrichten](messaging-main/messaging/in-apps-ts.md)
   + Push-Nachrichten{#push-messaging}
      + [Push-Nachrichten](messaging-main/push-messaging/push-messaging.md)
      + [Push-Nachrichten mit Deep-Links implementieren](messaging-main/push-messaging/t-mob-impl-push-deeplinking-android-4x.md)
      + [Rich-Push-Benachrichtigungen empfangen](messaging-main/push-messaging/c-set-up-rich-push-notif-android.md)
      + [Fehlerbehebung bei Push-Nachrichten](messaging-main/push-messaging/c-troubleshooting-push-messaging.md)
+ Ort{#location}
   + [Übersicht über die Funktion „Standort“](location/location.md)
   + [Geostandort und Zielpunkte](location/geo-poi.md)
   + [Beacon-Verfolgung](location/beacon.md)
+ Target{#target-android}
   + [Übersicht über Target](target-main/target-main.md)
   + [Target-Konfiguration](target-main/target.md)
   + [Target-Methoden](target-main/c-target-methods.md)
   + [Vorabruf für Android-Angebotsinhalte](target-main/c-mob-target-prefetch-android.md)
   + [Target-Vorschau auf Android](target-main/c-mob-target-preview-android.md)
+ Experience Cloud{#experience-cloud-android}
   + [Übersicht über Experience Cloud](c-marketing-cloud/c-marketing-cloud.md)
   + [Experience Cloud ID-Konfiguration](c-marketing-cloud/mcvid.md)
   + [Identity-Dienst-Methoden für Adobe Experience Platform](c-marketing-cloud/mc-methods.md)
   + [Experience Cloud-Gerätekooperation](c-marketing-cloud/t-mob-mc-device-coop-android-.md)
+ Audience Manager{#audience-manager-android}
   + [Übersicht über Audience Manager](audience-manager/audience-manager.md)
   + [Audience Manager-Konfiguration](audience-manager/audiencemgmt.md)
   + [Audience Manager-Methoden](audience-manager/c-audience-manager-methods.md)
+ Wearables{#wearables-android}
   + [Übersicht über Wearables](wearables/wearables.md)
   + [Android Wearables: Erste Schritte](wearables/android-wearable.md)
   + [Android Wearables: Zusätzliche Hinweise](wearables/c-android-wearables--additional-notes.md)
+ Android-SDK-Referenz{#sdk-reference-android}
   + [Android-SDK-Referenzübersicht](/help/android/reference/reference.md)
   + [App-IDs](/help/android/reference/app-ids.md)
   + [Besucher zwischen einer App und dem mobilen Internet verfolgen](/help/android/reference/hybrid-app.md)
   + [Android-Widgets](/help/android/reference/widgets.md)
+ Privatsphäre und Datenschutz-Grundverordnung{#gdpr-privacy-android}
   + [Übersicht über Datenschutz und DSGVO](c-mob-privacy-gdpr-android/c-mob-privacy-gdpr-android.md)
   + [Gespeicherte IDs abrufen](c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md)
   + [Auswahlstatus eines Benutzers festlegen](c-mob-privacy-gdpr-android/privacy.md)
+ PhoneGap-Plug-in{#phonegap-android}
   + [Übersicht über das PhoneGap-Plug-in](phonegap/phonegap.md)
   + [PhoneGap-Plug-in-Methoden](phonegap/phonegap-methods.md)
