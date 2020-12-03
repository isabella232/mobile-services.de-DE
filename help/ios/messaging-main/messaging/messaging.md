---
description: Diese Informationen helfen Ihnen beim Verwenden der In-App-Nachrichten in Ihren iOS-Apps.
seo-description: Diese Informationen helfen Ihnen beim Verwenden der In-App-Nachrichten in Ihren iOS-Apps.
seo-title: In-App-Nachrichten
solution: Experience Cloud,Analytics
title: In-App-Nachrichten
topic: Developer and implementation
uuid: 21fa6a94-bb7f-4c78-843b-a50f1974db22
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 100%

---


# In-App-Nachrichten {#in-app-messaging}

Diese Informationen helfen Ihnen beim Verwenden der In-App-Nachrichten in Ihren iOS-Apps.

Um In-App-Nachrichten zu nutzen, ist SDK-Version 4.2 (oder höher) **erforderlich**.

Beachten Sie Folgendes:

* Nachrichten und die Regeln, die definieren, wann Nachrichten angezeigt werden, werden in Adobe Mobile Services erstellt. Weitere Informationen finden Sie unter [In-App-Nachrichten erstellen](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md).
* Die in diesem Abschnitt beschriebenen Aktualisierungen müssen am SDK vorgenommen werden, um In-App-Nachrichten anzuzeigen.

   >[!TIP]
   >
   >Sie können diese Schritte selbst dann ausführen, wenn Sie keine Nachrichten definiert haben. Nachdem Sie Nachrichten definiert haben, werden sie dynamisch an die App bereitgestellt und ohne Update des Appstores angezeigt.

## In-App-Nachrichten aktivieren {#section_79F984271C3B4366B7B04F864F4FF8C2}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zum Projekt hinzufügen* im Abschnitt [Grundlegende Implementierung und Lebenszyklus](/help/ios/getting-started/requirements.md).

1. Importieren Sie die Bibliothek:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Überprüfen Sie, ob die Datei `ADBMobileConfig.json` die erforderlichen Einstellungen für In-App-Nachrichten enthält.
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

   Wenn diese Objekte nicht konfiguriert sind, sollten Sie eine aktualisierte Datei `ADBMobileConfig.json` aus Adobe Mobile Services herunterladen. Weitere Informationen finden Sie unter [Grundlegende Implementierung und Lebenszyklus](/help/ios/getting-started/requirements.md).

## In-App-Nachrichten verfolgen {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Mobile Services SDK für iOS lassen sich folgende Metriken Ihrer In-App-Nachrichten verfolgen:

* Für In-App-Nachrichten im Vollbild- und Warnhinweisstil:

   * **[!UICONTROL Impressionen]**: Benutzer löst eine In-App-Nachricht aus.
   * **[!UICONTROL Clickthrough]**: Benutzer betätigt die **[!UICONTROL Clickthrough]**-Schaltfläche.
   * **[!UICONTROL Abbrüche]**: Benutzer betätigt die **[!UICONTROL Abbrechen]**-Schaltfläche.

* Für benutzerdefinierte Vollbild-In-App-Nachrichten muss der HTML-Inhalt der Nachricht den richtigen Code enthalten, um die SDK-Verfolgung über die Nutzung folgender Schaltflächen informieren zu können:

   * **[!UICONTROL Clickthrough]** (Umleitung) der Beispielverfolgung:  `adbinapp://confirm/?url=https://www.yoursite.com`
   * **[!UICONTROL Abbrechen]** (Schließen) des Beispiel-Tracking: `adbinapp://cancel`

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

## Lokales Ausweichbild {#section_DEACC1CE549B4573B556A44A52409941}

Beim Erstellen einer Vollbildnachricht in Adobe Mobile Services können Sie optional ein Ausweichbild angeben. Wenn Ihre Nachricht nicht in der Lage ist, das gewünschte Bild aus dem Internet abzurufen, versucht das SDK, das Bild mit demselben Namen aus Ihrem App-Paket zu laden. Auf diese Weise können Sie Ihre Nachricht in ihrer ursprünglichen Form anzeigen, auch wenn der Benutzer offline ist oder das vorgegebene Bild nicht erreichbar ist.

Der Asset-Name des Ausweichbilds wird beim Konfigurieren der Nachricht in Adobe Mobile Services angegeben.

>[!IMPORTANT]
>
>Sie müssen sicherstellen, dass die angegebene Ressource verfügbar ist.

