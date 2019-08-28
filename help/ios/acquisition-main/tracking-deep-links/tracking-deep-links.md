---
description: Mit diesen Informationen können Sie Deep-Links und verzögerte Deep-Links in Ihren mobilen Apps verfolgen, indem Sie das Adobe Mobile iOS-SDK verwenden.
seo-description: Mit diesen Informationen können Sie Deep-Links und verzögerte Deep-Links in Ihren mobilen Apps verfolgen, indem Sie das Adobe Mobile iOS-SDK verwenden.
seo-title: Verfolgen von Deep Links
solution: Marketing Cloud, Analytics
title: Verfolgen von Deep Links
uuid: 08 dc 2820-7 fd 3-419 f-ac 2 d-dcf 12532578 a
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Tracking deep links{#tracking-deep-links}

Mit diesen Informationen können Sie Deep-Links und verzögerte Deep-Links in Ihren mobilen Apps verfolgen, indem Sie das Adobe Mobile iOS-SDK verwenden.

Weitere Informationen dahingehend, wie Marketingexperten Deep-Links in ihren Anwendungen verwenden, finden Sie im Thema zur [Akquise](/help/ios/acquisition-main/acquisition.md) in der Dokumentation zu Mobile Services.

## Verfolgen von Deep Links

1. Fügen Sie das SDK zu Ihrem Projekt hinzu und implementieren Sie Lebenszyklusmetriken.

   Weitere Informationen finden Sie unter *Fügen Sie das SDK und die Config-Datei zu Ihrem Projekt* in [Core-Implementierung und Lebenszyklus hinzu](/help/ios/getting-started/dev-qs.md).
1. Registrieren Sie die Anwendung, um zwischen Interapp Communications und universelle Links zu verarbeiten.

   Weitere Informationen finden Sie unter [Interapp Communications](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW10) oder [Unterstützung universeller Links.](https://developer.apple.com/library/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html)

1. Verfolgen Sie den Deep-Link in openURL.

   Im Folgenden finden Sie einen Beispielpfad-Deep-Link:

   ```objective-c
   - (BOOL)application:(UIApplication *)application handleOpenURL:(NSURL *)url { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
       return YES; 
   } 
   - (BOOL)application:(UIApplication *)app openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options { 
       [ADBMobile trackAdobeDeepLink:url]; 
       /* 
        Handle deep link 
        */ 
   
       return YES; 
   }
   ```

The Adobe Mobile SDK can parse key and value pairs of data appended to any deep or Universal Link, provided that the link contains a key with a `a.deeplink.id` label and a corresponding non-null and user generated value. Alle Schlüssel-Wert-Paare von Daten, die an den Link angehängt sind, werden analysiert, an einen Lebenszyklustreffer angehängt und an Adobe Analytics gesendet, sofern der Link das Schlüssel-Wert-Paar `a.deeplink.id` enthält.

Sie können auch einen oder mehrere der folgenden reservierten Schlüssel (mit benutzergenerierten Werten) dem Deep- oder universellen Link anhängen:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Bei diesen Schlüsseln handelt es sich um vorab zugeordnete Variablen für das Reporting in Adobe Analytics. Weitere Informationen zu Zuordnungs- und Verarbeitungsregeln finden Sie unter [Verarbeitungsregeln und Kontextdaten](/help/ios/getting-started/proc-rules.md).

### Verfolgen verzögerter Deep-Links

1. Registrieren Sie Adobe-Daten-Callback.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
   }];
   ```

1. Handle `ADBMobileDataEventDeepLink` innerhalb `AdobeDataCallback`.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
       if (event == ADBMobileDataEventDeepLink) { 
           [self handleDeepLink:adobeData[ADBConfigKeyCallbackDeepLink]]; 
       } 
   }];
   ```

## Deep link public information {#section_44600E9AA68D4A53AA0C14BD86CC5284}

### Methoden

```objective-c
/** 
 * @brief Tracks a Adobe Deep Link click-through 
 * @param url The URL resource received from UIApplication delegate method. 
 * @note Adobe Link data will be appended to the lifecycle call if it is a launch event, otherwise an extra call will be sent. 
 */ 
+ (void) trackAdobeDeepLink:(nullable NSURL *)url;
```

#### Konstanten

```objective-c
/* 
 * Used within ADBMobileDataCallback 
 * Key for deep link URL. 
 */ 
FOUNDATION_EXPORT NSString *const __nonnull ADBConfigKeyCallbackDeepLink;
```

