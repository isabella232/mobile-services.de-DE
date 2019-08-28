---
description: Verwenden Sie das Android SDK zum Implementieren der Nachverfolgung von verzögerten Deep-Links von Drittanbietern.
seo-description: Verwenden Sie das Android SDK zum Implementieren der Nachverfolgung von verzögerten Deep-Links von Drittanbietern.
seo-title: Verfolgen verzögerter Drittanbieter-Deep-Links
title: Verfolgen verzögerter Drittanbieter-Deep-Links
uuid: 4 c 798 e 47-7988-4 a 06-a 191-6 c 4 d 05 f 6 ee 61
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Tracking third-party deferred deep links{#tracking-third-party-deferred-deep-links}

Verwenden Sie das Android SDK zum Implementieren der Nachverfolgung von verzögerten Deep-Links von Drittanbietern.

## Classic Adobe Mobile SDK deep linking {#section_D114FA1EB9664EAA82E036A990694B26}

Das Adobe Mobile SDK unterstützt derzeit ein Deep Linking, bei dem erwartet wird, dass der App-Entwickler die `collectLifecycleData` SDK-API der Deep-Link-Aktivität verwendet. Das SDK fügt die Deep-Link-Daten aus den Deep-Link-URL-Parametern hinzu. Weitere Informationen zur Funktionsweise von Deep Linking im Adobe Mobile SDK finden Sie unter [Verfolgen von Deep-Links](/help/android/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Facebook deep linking {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

Ersteller von Werbeanzeigen können eine Werbeanzeige auf Facebook als Deep-Link erstellen. Wenn Anwender auf diese Werbeanzeige klicken, werden sie direkt zu der Information weitergeleitet, an der sie in der App interessiert waren. Der Deep-Link ist **keine** Fingerprinting-URL. Während der Werbekonfiguration ist jedoch eine Option verfügbar, um eine Drittanbieter-Deep-Link-URL bereitzustellen. Von einem App-Entwickler, der die Adobe Mobile-SDKs und Services verwendet, wird erwartet, dass er die für Adobe Mobile Services konfigurierte Fingerprinter-URL in dieses Feld eingibt. Wenn alles ordnungsgemäß eingerichtet ist, übergibt das Facebook-SDK diese URL an die Anwendung, wenn die App installiert oder gestartet wird.

## Einrichten der SDKs {#section_834CD3109175432B8173ECB6EA7DE315}

Als Vorbereitung der Hinzufügung der Deep Linking-Unterstützung von Facebook im Adobe Mobile SDK führt der App-Entwickler die folgenden Aufgaben aus:

* Erste Schritte mit dem Android SDK

   For more information, see [Getting Started Android SDK](https://developers.facebook.com/docs/android/getting-started) .

* Deep-Linking einrichten

   Weitere Informationen finden Sie unter [Deep-Linking-Einrichtung](https://developers.facebook.com/docs/app-ads/deep-linking#os).

If the application is set up correctly, the `trackAdobeDeepLink()` API should enable collecting the deep link information from the Facebook acquisition campaign and send it to Adobe Mobile Service. Wenn der Installationstreffer nicht beim ersten Start an Adobe Mobile Service gesendet wurde, werden diese Informationen dem Lifecycle-Treffer hinzugefügt. Andernfalls wird sie als Adobe-Deep-Link-Treffer gesendet.

>[!TIP]
>
>Ensure that the deep link URL has a key called `a.deeplink.id`. Wenn die URL den Deep Link ID-Parameter nicht enthält, werden die URL-Parameter nicht an die Kontextdaten angehängt.

Wenn der Link einer Akquise zugeordnet werden kann, speichert das Adobe Mobile SDK die Akquisedaten von der Facebook-Deep-Link-Adresse, über die `trackAdobeDeepLink()`  () aufgerufen wurde. Diese Daten stehen dem Adobe Mobile SDK bei zukünftigen Starts zur Verfügung. Falls ein Rückruf registriert wurde, wird auch der Adobe-Rückruf verwendet, um die Daten zurück an den Client zu senden.

## Enable deep linking in an Android application {#section_64C15E269E89424B8E3D029F88094620}

1. Registrieren Sie die Anwendung, damit sie Deep-Links verarbeiten kann.

   Weitere Informationen finden Sie unter [Zulassen, dass andere Apps Ihre Aktivität starten](https://developer.android.com/training/basics/intents/filters.html).

1. Verlinken Sie die Facebook-SDKs.

   Um die Facebook-Gradle-Abhängigkeit in der App hinzuzufügen, führen Sie die Schritte unter [Erste Schritte mit dem Android-SDK](https://developers.facebook.com/docs/android/getting-started) aus.

1. Um das Facebook-SDK zu initialisieren, befolgen Sie die Anweisungen im Abschnitt *Einrichtung von Android Studio*.
1. Call `trackAdobeDeepLink()` from the main activity.

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

