---
description: Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.
seo-description: Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.
seo-title: Target-Vorschau auf iOS
title: Target-Vorschau auf iOS
uuid: d 92867 a 4-0569-4732-a 928-28 f 9 e 2 f 8 b 21 e
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Target-Vorschau auf iOS{#target-preview-on-ios}

Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.

For more information on how to set up and use Target Preview, see [Target Mobile Preview](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>Um die Target-Vorschau zu verwenden, benötigen Sie SDK 4.14.0 oder höher.

## Target-Vorschaumethode

* **setPreviewRestartDeeplink**

   Legt einen App-Deeplink fest, der bei im Vorschaumodus angewandten Vorschauauswahlen ausgelöst wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@" myapp://myhost"]; 
      ```
