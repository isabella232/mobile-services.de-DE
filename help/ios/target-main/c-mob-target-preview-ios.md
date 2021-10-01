---
description: Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.
title: Target-Vorschau auf iOS
uuid: d92867a4-0569-4732-a928-28f9e2f8b21e
exl-id: d5695156-59cd-42c5-b9a3-d8e0ebbb89d0
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 76%

---

# Target-Vorschau auf iOS{#target-preview-on-ios}

Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.

Weitere Informationen zum Einrichten und Verwenden der Target-Vorschau finden Sie unter [Target Mobile Preview](https://experienceleague.adobe.com/docs/target/using/implement-target/mobile-apps/target-mobile-preview.html) in der Adobe Target-Dokumentation.

>[!IMPORTANT]
>
>Um die Target-Vorschau verwenden zu können, benötigen Sie SDK-Version 4.14.0 oder höher.

## Target-Vorschaumethode

* **setPreviewRestartDeeplink**

   Legt einen App-Deeplink fest, der ausgelöst wird, wenn Vorschauauswahlen im Vorschaumodus angewendet werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
       + (void) targetPreviewRestartDeepLink:(nullable NSString *)callbackURL;
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile targetPreviewRestartDeepLink:@"myapp://myhost"]; 
      ```
