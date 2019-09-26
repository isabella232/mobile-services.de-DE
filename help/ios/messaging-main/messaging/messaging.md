---
description: Diese Informationen helfen Ihnen beim Verwenden der In-App-Nachrichten in Ihren iOS-Apps.
seo-description: Diese Informationen helfen Ihnen beim Verwenden der In-App-Nachrichten in Ihren iOS-Apps.
seo-title: In-App-Nachrichten
solution: Marketing Cloud, Analytics
title: In-App-Nachrichten
topic: Entwickler und Implementierung
uuid: 21fa6a94-bb7f-4c78-843b-a50f1974db22
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# In-App-Nachrichten {#in-app-messaging}

Diese Informationen helfen Ihnen beim Verwenden der In-App-Nachrichten in Ihren iOS-Apps.

Zum Verwenden von In-App-Nachrichten **müssen** Sie über die SDK-Version 4.2 oder höher verfügen.

Hinweise:

* Nachrichten und Regeln, die definieren, wann Nachrichten angezeigt werden, werden in Adobe Mobile Services erstellt. Weitere Informationen finden Sie unter [In-App-Nachrichten erstellen](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md).
* Die in diesem Abschnitt beschriebenen Aktualisierungen müssen mit dem SDK vorgenommen werden, um In-App-Nachrichten anzuzeigen.

   >[!TIP]
   >
   >Sie können diese Schritte auch dann ausführen, wenn keine Meldungen definiert sind. Nachdem Sie Nachrichten definiert haben, werden sie dynamisch an Ihre App gesendet und ohne App Store-Aktualisierung angezeigt.

## Enabling in-app messages {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   For more information, see Add the SDK and Config File to your Project in Core Implementation and Lifecycle.**[](/help/ios/getting-started/requirements.md)

1. Importieren Sie die Bibliothek:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required settings for In-App messaging.
1. Damit In-App-Nachrichten beim Start dynamisch aktualisiert werden, muss das Objekt `remotes` vorhanden und entsprechend konfiguriert sein:

   ```js
   “messages”: [ 
       { 
           “messageId”: “de45c43c-37bf-441f-8cbd-cc3ba3469ebe”, 
           “template”: “fullscreen”, 
           “showOffline”: false, 
           “showRule”: “always”, 
           “endDate”: 2524730400, 
           “startDate”: 0, 
           “audiences”: [], 
           “triggers”: [], 
           “payload”: { // contents change depending on template 
               “html”: “<html>html code goes here</html>” 
           }, 
       }, 
       … 
   ] 
   “remotes” : { 
       “analytics.poi”: “https://assets.adobedtm.com/…/yourfile.json”, 
       “messages”: “https://assets.adobedtm.com/…/yourfile.json” 
   }
   ```

   >[!TIP]
   >
   >`messages` oder `remotes` ist erforderlich.

   If these objects are not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. For more information, see Core Implementation and Lifecycle.[](/help/ios/getting-started/requirements.md)

## Tracking in-app messages {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Mobile Services SDKs für iOS lassen sich folgende Metriken Ihrer In-App-Nachrichten verfolgen:

* Für In-App-Vollbild- und -Warnnachrichten:

   * **[!UICONTROL Impressionen]**: wenn der Benutzer eine In-App-Nachricht auslöst.
   * **[!UICONTROL Click throughs]**: when the user pushes the **[!UICONTROL Click-through]** button.
   * **[!UICONTROL Abbrüche]**: wenn der Benutzer die Schaltfläche **[!UICONTROL Abbrechen]** drückt.

* Für benutzerdefinierte Vollbild-In-App-Nachrichten muss der HTML-Inhalt der Nachricht den richtigen Code enthalten, um die SDK-Verfolgung über die Nutzung folgender Schaltflächen informieren zu können:

   * **[!UICONTROL Click-through (redirect) example tracking:]**`adbinapp://confirm/?url=https://www.yoursite.com`
   * **[!UICONTROL Cancel]** (close) example tracking: `adbinapp://cancel`

* Für lokale (Remote-)Nachrichten:

   * **[!UICONTROL Impressionen]**: Benutzer löst die Nachricht aus.
   * **[!UICONTROL Öffnet]**: Benutzer öffnet die App über die Nachricht.
   Hier ein Beispiel für die Einbettung einer offenen Verfolgung:

   ```objective-c
   - (BOOL) application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
     // handle local notification click-throughs for iOS 10 and older 
     NSDictionary *localNotificationDictionary = launchOptions[UIApplicationLaunchOptionsLocalNotificationKey]; 
     if ([localNotificationDictionary isKindOfClass:[NSDictionary class]]) { 
          [ADBMobile trackLocalNotificationClickThrough:localNotificationDictionary]; 
     } 
   } 
   - (void) application:(UIApplication *)application didReceiveLocalNotification:(UILocalNotification *)notification { 
      [ADBMobile trackLocalNotificationClickThrough:notification.userInfo]; 
   }
   ```

## Local fallback image {#section_DEACC1CE549B4573B556A44A52409941}

Beim Erstellen einer Vollbildnachricht in Adobe Mobile Services können Sie optional ein Ausweichbild angeben. Wenn Ihre Nachricht das gewünschte Bild nicht aus dem Web abrufen kann, versucht das SDK, das Bild mit demselben Namen aus Ihrem Anwendungspaket zu laden. Dadurch können Sie Ihre Nachricht in ihrer ursprünglichen Form anzeigen, selbst wenn der Benutzer offline ist oder der Zugriff auf das vorbestimmte Bild nicht möglich ist.

Der Asset-Name des Ausweichbilds wird angegeben, wenn die Nachricht in Adobe Mobile Services konfiguriert wird.

>[!IMPORTANT]
>
>Sie müssen sicherstellen, dass die angegebene Ressource verfügbar ist.

