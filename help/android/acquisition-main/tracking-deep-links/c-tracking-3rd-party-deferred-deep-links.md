---
description: Verwenden Sie das Android SDK zum Implementieren der Nachverfolgung von verzögerten Deep-Links von Drittanbietern.
seo-description: Verwenden Sie das Android SDK zum Implementieren der Nachverfolgung von verzögerten Deep-Links von Drittanbietern.
seo-title: Verfolgen von verzögerten Deep-Links von Drittanbietern
title: Verfolgen von verzögerten Deep-Links von Drittanbietern
uuid: 4c798e47-7988-4a06-a191-6c4d05f6ee61
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 84%

---


# Verzögerte Drittanbieter-Deep-Links verfolgen{#tracking-third-party-deferred-deep-links}

Verwenden Sie das Android SDK zum Implementieren der Nachverfolgung von verzögerten Deep-Links von Drittanbietern.

## Deep-Links für das Classic Adobe Mobile SDK {#section_D114FA1EB9664EAA82E036A990694B26}

Das Adobe Mobile SDK unterstützt derzeit ein Deep Linking, bei dem erwartet wird, dass der App-Entwickler die `collectLifecycleData` SDK-API der Deep-Link-Aktivität verwendet. Das SDK fügt die Deep-Link-Daten aus den Deep-Link-URL-Parametern hinzu. Weitere Informationen zur Funktionsweise von Deep Linking im Adobe Mobile SDK finden Sie unter [Verfolgen von Deep-Links](/help/android/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Facebook-Deep-Links {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

Ersteller von Werbeanzeigen können eine Werbeanzeige auf Facebook als Deep-Link erstellen. Wenn Benutzer auf die Anzeige klicken, werden sie direkt zu den Informationen weitergeleitet, an denen sie in der App interessiert sind. Der Deep-Link ist **keine** Fingerprinting-URL. Während der Werbekonfiguration ist jedoch eine Option zur Bereitstellung einer Drittanbieter-Deep-Link-URL verfügbar. Von einem App-Entwickler, der die Adobe Mobile-SDK und Services verwendet, wird erwartet, dass er die für Adobe Mobile Services konfigurierte Fingerprinter-URL in dieses Feld eingibt. Wenn alles ordnungsgemäß eingerichtet ist, übergibt das Facebook-SDK diese URL an die Anwendung, wenn die App installiert oder gestartet wird.

## Einrichten der SDK {#section_834CD3109175432B8173ECB6EA7DE315}

Als Vorbereitung der Hinzufügung der Deep Linking-Unterstützung von Facebook im Adobe Mobile SDK führt der App-Entwickler die folgenden Aufgaben aus:

* Erste Schritte mit dem Android-SDK

   Weitere Informationen finden Sie unter [Erste Schritte mit dem Android-SDK](https://developers.facebook.com/docs/android/getting-started).

* Deep-Linking einrichten

   Weitere Informationen finden Sie unter [Deep-Linking-Setup](https://developers.facebook.com/docs/app-ads/deep-linking#os).

Wenn die App ordnungsgemäß eingerichtet ist, sollte die `trackAdobeDeepLink()`-API die Erfassung der Deep-Link-Informationen aus der Facebook-Akquise-Kampagne aktivieren und an Adobe Mobile Service senden. Wenn der Installationstreffer beim ersten Start nicht an Adobe Mobile Service gesendet wurde, werden diese Informationen zum Lebenszyklustreffer hinzugefügt. Andernfalls wird sie als Deep-Link-Treffer der Adobe gesendet.

>[!TIP]
>
>Stellen Sie sicher, dass die Deep-Link-URL über einen Schlüssel mit dem Namen `a.deeplink.id` verfügt. Wenn die URL den Deep Link ID-Parameter nicht enthält, werden die URL-Parameter nicht an die Kontextdaten angehängt.

Wenn der Link einer Akquise zugeordnet werden kann, speichert das Adobe Mobile SDK die Akquisedaten von der Facebook-Deep-Link-Adresse, über die `trackAdobeDeepLink()` () aufgerufen wurde. Diese Daten stehen der Adobe Mobile SDK in zukünftigen Starts zur Verfügung. Wenn ein Rückruf registriert wurde, wird der Rückruf bei der Adobe auch verwendet, um die Daten an den Client zurückzusenden.

## Deep-Linking in einer Android-App aktivieren {#section_64C15E269E89424B8E3D029F88094620}

1. Registrieren Sie die Anwendung, damit sie Deep-Links verarbeiten kann.

   Weitere Informationen finden Sie unter [Zulassen, dass andere Apps Ihre Aktivität starten](https://developer.android.com/training/basics/intents/filters.html).

1. Verlinken Sie die Facebook-SDK.

   Um die Facebook-Gradle-Abhängigkeit in der App hinzuzufügen, führen Sie die Schritte unter [Erste Schritte mit dem Android-SDK](https://developers.facebook.com/docs/android/getting-started) aus.

1. Um das Facebook-SDK zu initialisieren, befolgen Sie die Anweisungen im Abschnitt *Einrichtung von Android Studio*.
1. Rufen Sie `trackAdobeDeepLink()` aus der Hauptaktivität auf.

   ```java
   @Override 
   protected void onResume() { 
      super.onResume(); 
      AppEventsLogger.activateApp(this); 
      /* 
       * Adobe Tracking - Config 
       * 
       * call collectLifecycleData() to begin collecting lifecycle data 
       * must be in the onResume() of every activity in your app 
       */ 
      Config.collectLifecycleData(this);
   
      AppLinkData.fetchDeferredAppLinkData(this, 
            new AppLinkData.CompletionHandler() { 
               @Override 
               public void onDeferredAppLinkDataFetched(AppLinkData appLinkData) { 
                  // Process app link data 
                  if (appLinkData != null) { 
                     Config.trackAdobeDeepLink(appLinkData.getTargetUri()); 
                  } 
               } 
            } 
      ); 
   }
   ```

