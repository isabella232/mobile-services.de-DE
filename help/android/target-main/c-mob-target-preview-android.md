---
description: Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.
seo-description: Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.
seo-title: Target-Vorschau auf Android
title: Target-Vorschau auf Android
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
translation-type: ht
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# Target-Vorschau auf Android {#target-preview-on-android}

Mit der Target-Vorschau können Sie einfach Ende-zu-Ende-Qualitätssicherung für Target-Aktivitäten betreiben und diese Aktivitäten auf Ihrem Gerät ansehen.

Weitere Informationen über die Einrichtung und Verwendung der Target-Vorschau finden Sie unter [Mobile Target-Vorschau](https://docs.adobe.com/content/help/de-DE/target/using/implement-target/mobile-apps/target-mobile-preview.html)

>[!IMPORTANT]
>
>Um die Target-Vorschau verwenden zu können, benötigen Sie SDK-Version 4.14.0 oder höher.

* **setPreviewRestartDeeplink**

   Legt einen App-Deeplink fest, der bei im Vorschaumodus angewandten Vorschauauswahlen ausgelöst wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void setPreviewRestartDeeplink(String deeplink);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Target.setPreviewRestartDeeplink(“myapp://myhost”); 
      ```

