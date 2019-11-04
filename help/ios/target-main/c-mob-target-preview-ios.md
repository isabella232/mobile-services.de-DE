---
description: Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.
seo-description: Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.
seo-title: Target-Vorschau auf iOS
title: Target-Vorschau auf iOS
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Target-Vorschau auf iOS{#target-preview-on-ios}

Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.

Weitere Informationen über die Einrichtung und Verwendung der Target-Vorschau finden Sie unter [Mobile Target-Vorschau](https://docs.adobe.com/content/help/de-DE/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>Um die Target-Vorschau verwenden zu können, benötigen Sie SDK-Version 4.14.0 oder höher.

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
