---
description: Verwenden Sie das iOS-SDK, um die Verfolgung verzögerter Deep-Links von Drittanbietern zu implementieren.
seo-description: Verwenden Sie das iOS-SDK, um die Verfolgung verzögerter Deep-Links von Drittanbietern zu implementieren.
seo-title: Verfolgen verzögerter Deep-Links von Drittanbietern
title: Verfolgen verzögerter Drittanbieter-Deep-Links
uuid: 5525b609-e926-44b9-b0f5-38e9dd7c9761
translation-type: tm+mt
source-git-commit: 4b5be6c51c716114e597a80d475f838e23abb1b1

---


# Tracking third-party deferred deep links {#tracking-third-party-deferred-deep-links}

Verwenden Sie das iOS-SDK, um die Verfolgung verzögerter Deep-Links von Drittanbietern zu implementieren.

## Classic Adobe Mobile SDK deep linking {#section_D114FA1EB9664EAA82E036A990694B26}

The Adobe Mobile SDK currently supports deep linking where the app developer is expected to call the `trackAdobeDeepLink` API and pass the deep linking URL, which is the fingerprinter URL that is generated in Adobe Mobile Services during configuration. Das SDK pingt den Fingerprinter zum Abrufen der Akquisedaten und hängt sie als Bestandteil des Lebenszyklus an die Kontextdaten für das Installieren/Starten von Analyseaufrufen an. Darüber hinaus hängt das SDK auch die deeplink-Daten aus den deeplink-URL-Parametern an. Weitere Informationen zu Deep-Linking finden Sie unter [Verfolgen von Deep-Links](/help/ios/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Facebook deep linking {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

Ersteller von Werbeanzeigen können eine Werbeanzeige auf Facebook als Deep-Link erstellen. Wenn Benutzer auf diese Facebook-Werbeanzeige klicken, werden sie direkt an die Information weitergeleitet, an der sie in der App interessiert waren. Der Deep-Link ist **keine** Fingerprinting-URL. Während der Werbekonfiguration ist jedoch eine Option zur Bereitstellung einer Drittanbieter-Deep-Link-URL verfügbar. Von einem App-Entwickler, der die Experience Cloud Mobile-SDKs und Services verwendet, wird erwartet, dass er die für Adobe Mobile Services konfigurierte Fingerprinter-URL in dieses Feld eingibt. Wenn alles ordnungsgemäß eingerichtet ist, übergibt das Facebook-SDK diese URL an die Anwendung, wenn die App installiert oder gestartet wird.

## Einrichten der SDKs   {#section_834CD3109175432B8173ECB6EA7DE315}

1. Einrichten des Facebook-SDK.

   Weitere Informationen finden Sie unter:

   * [Erste Schritte mit dem Facebook-SDK für iOS](https://developers.facebook.com/docs/ios/getting-started)
   * [Deep-Linking-Setup](https://developers.facebook.com/docs/app-ads/deep-linking#os)

1. Um das SDK einzurichten, rufen Sie die URL auf `trackAdobeDeepLink` und übergeben Sie sie an die SDKs:

   ```objective-c
   - (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation 
   { 
     [ADBMobile trackAdobeDeepLink:url]; 
     return YES; 
   }
   ```

   >[!TIP]
   >
   >Ensure that the deep link URL has a key with the name `a.deeplink.id`. Es werden keine URL-Parameter an die Kontextdaten angehängt, wenn der Parameter `a.deeplink.id` in der URL fehlt.

Wenn die Anwendung entsprechend der obigen Beschreibung eingerichtet ist, funktionieren die aktuelle Adobe Mobile-SDK-Version und das Anhängen der Deep-Link-Daten zum Installieren/Starten von Analyseaufrufen ordnungsgemäß.

## Enable the feature in a sample application {#section_64C15E269E89424B8E3D029F88094620}

1. Registrieren Sie ein URL-Schema.

   Stellen Sie sicher, dass Sie ein URL-Schema registriert haben, das der Deep-Link-URL entspricht.

   ```objective-c
   <key>CFBundleURLTypes</key> 
       <array> 
           <dict> 
               <key>CFBundleURLSchemes</key> 
               <array> 
                   <string>sampleapptest</string> 
               </array> 
           </dict> 
       </array>
   ```

1. Verlinken Sie die Facebook-SDKs.

   ![Facebook-Assets](assets/link-fb-sdk.jpg)

1. Bearbeiten `AppDelegate`.

   1. Importieren Sie die Header.

      ```objective-c
      /************************************************************************* 
      ADOBE SYSTEMS INCORPORATED 
      Copyright 2015 Adobe Systems Incorporated 
      All Rights Reserved. 
      NOTICE:  Adobe permits you to use, modify, and distribute this file in accordance with the 
      terms of the Adobe license agreement accompanying it.  If you have received this file from a 
      source other than Adobe, then your use, modification, or distribution of it requires the prior 
      written permission of Adobe. 
      
      **************************************************************************/ 
      
      #import "AppDelegate.h" 
      #import "GalleryViewController.h" 
      #import "SimpleTrackingController.h" 
      #import "PostbackController.h" 
      #import "InAppMessageViewController.h" 
      #import "LifetimeValueController.h" 
      #import "LocationTargetingController.h" 
      #import "MediaViewController.h" 
      #import "TimedActionController.h"
      
      // Uncomment after including the facebook sdks. 
      @import FBSDKCoreKit; 
      @import Bolts;
      ```

   1. Add the handle for deferred deep linking.

      ```objective-c
      - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
          /* 
           * Adobe Tracking - Analytics 
           * 
           * turn on debug logging for the ADBMobile SDK 
           * enable the collection of lifecycle data 
           */ 
              if (launchOptions[UIApplicationLaunchOptionsURLKey] == nil) { 
                  if (NSClassFromString(@"FBSDKAppLinkUtility") != nil) 
                  { 
                      [NSClassFromString(@"FBSDKAppLinkUtility") performSelector:@selector(fetchDeferredAppLink:) withObject:^(NSURL *url, NSError *error) { 
                          if (error) { 
                              NSLog(@"Received error while fetching deferred app link %@", error); 
                          } 
                          if (url) { 
                              [[UIApplication sharedApplication] openURL:url]; 
                          } 
                      }]; 
                  } 
          } 
          ..... 
          ..... 
          return YES; 
      }
      ```

   1. Call the `trackAdobeDeepLink` API and pass the deep link URL to the SDK.

      ```objective-c
      - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
          [self handleDeepLink:url]; 
      
          return YES; 
      }
      ```

