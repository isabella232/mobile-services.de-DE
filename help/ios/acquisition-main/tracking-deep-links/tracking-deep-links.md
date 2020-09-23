---
description: Mit diesen Informationen können Sie Deep-Links und verzögerte Deep-Links in Ihren mobilen Apps verfolgen, indem Sie das Adobe Mobile iOS-SDK verwenden.
seo-description: Mit diesen Informationen können Sie Deep-Links und verzögerte Deep-Links in Ihren mobilen Apps verfolgen, indem Sie das Adobe Mobile iOS-SDK verwenden.
seo-title: Deep-Links verfolgen
solution: Experience Cloud,Analytics
title: Deep-Links verfolgen
uuid: 08dc2820-7fd3-419f-ac2d-dcf12532578a
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 98%

---


# Deep-Links verfolgen{#tracking-deep-links}

Mit diesen Informationen können Sie Deep-Links und verzögerte Deep-Links in Ihren mobilen Apps verfolgen, indem Sie das Adobe Mobile iOS-SDK verwenden.

Weitere Informationen dahingehend, wie Marketingexperten Deep-Links in ihren Anwendungen verwenden, finden Sie im Thema zur [Akquise](/help/ios/acquisition-main/acquisition.md) in der Dokumentation zu Mobile Services.

## Deep-Links verfolgen

1. Fügen Sie das SDK zu Ihrem Projekt hinzu und implementieren Sie Lebenszyklusmetriken.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zum Projekt hinzufügen* im Abschnitt [Grundlegende Implementierung und Lebenszyklus](/help/ios/getting-started/dev-qs.md).
1. Registrieren Sie die App für die Verarbeitung von App-übergreifenden Kommunikationen oder zur Unterstützung von universellen Links.

   Weitere Informationen finden Sie unter [Inter-App-Kommunikation](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW10) oder [Unterstützung universeller Links.](https://developer.apple.com/library/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html)

1. Verfolgen Sie Deep-Link in openURL.

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

Das Adobe Mobile SDK kann Schlüssel-Wert-Paare von an Deep- oder universelle Links angehängten Daten analysieren, sofern der Link einen Schlüssel mit der Bezeichnung `a.deeplink.id`, einen entsprechenden Wert, der nicht „Null“ entspricht, sowie einen vom Benutzer generierten Wert aufweist. Alle Schlüssel-Wert-Paare von Daten, die an den Link angehängt sind, werden analysiert, an einen Lebenszyklustreffer angehängt und an Adobe Analytics gesendet, sofern der Link das Schlüssel-Wert-Paar `a.deeplink.id` enthält.

Zusätzlich können Sie auswählen, ob Sie einen oder mehrere der folgenden reservierten Schlüssel (mit benutzergenerierten Werten) an Deep- oder universelle Links anhängen möchten:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Bei diesen Schlüsseln handelt es sich um vorab zugeordnete Variablen für das Reporting in Adobe Analytics. Weitere Informationen zu Zuordnungs- und Verarbeitungsregeln finden Sie unter [Verarbeitungsregeln und Kontextdaten](/help/ios/getting-started/proc-rules.md).

### Verzögerte Deep-Links verfolgen

1. Registrieren Sie Adobe-Daten-Callback.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
   }];
   ```

1. `ADBMobileDataEventDeepLink`-Handle innerhalb `AdobeDataCallback`.

   ```objective-c
   [ADBMobile registerAdobeDataCallback:^(ADBMobileDataEvent event, NSDictionary * _Nullable adobeData) { 
       if (event == ADBMobileDataEventDeepLink) { 
           [self handleDeepLink:adobeData[ADBConfigKeyCallbackDeepLink]]; 
       } 
   }];
   ```

## Öffentliche Deep-Link-Informationen {#section_44600E9AA68D4A53AA0C14BD86CC5284}

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

