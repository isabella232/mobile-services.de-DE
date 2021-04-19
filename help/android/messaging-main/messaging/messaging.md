---
description: Sie können In-App-Nachrichten senden, die von beliebigen Analysedaten oder -Ereignissen ausgelöst werden. Nach der Implementierung werden Nachrichten dynamisch an die App gesendet und benötigen keine Code-Aktualisierung.
seo-description: Sie können In-App-Nachrichten senden, die von beliebigen Analysedaten oder -Ereignissen ausgelöst werden. Nach der Implementierung werden Nachrichten dynamisch an die App gesendet und benötigen keine Code-Aktualisierung.
seo-title: In-App-Nachrichten
solution: Experience Cloud,Analytics
title: In-App-Nachrichten
topic-fix: Developer and implementation
uuid: 351ee3d2-80b9-4f2d-9696-21f274d89f5a
exl-id: ca9414d1-86e6-4bb2-a2d6-57df37df2403
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 100%

---

# In-App-Nachrichten {#in-app-messaging}

Sie können In-App-Nachrichten senden, die von beliebigen Analysedaten oder -Ereignissen ausgelöst werden. Nach der Implementierung werden Nachrichten dynamisch an die App gesendet und benötigen keine Code-Aktualisierung.

## Neue Adobe Experience Cloud SDK-Version

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie [hier](https://aep-sdks.gitbook.io/docs/), um unsere aktuelle Dokumentation abzurufen.

>[!IMPORTANT]
>
>Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDK können über [Experience Platform Launch](https://www.adobe.com/de/experience-platform/launch.html) konfiguriert werden.

* Gehen Sie zu [Launch](https://launch.adobe.com/), um zu beginnen.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.

>[!IMPORTANT]
>
> Wenn Sie die Mobile SDK für Adobe Experience Platform mit Adobe Launch verwenden, **müssen** Sie außerdem die Adobe Analytics Mobile Services-Erweiterung installieren, um die Funktionen von Adobe Mobile Services wie In-App-Nachrichten und Push-Benachrichtigungen zu verwenden. Weitere Informationen finden Sie unter [Adobe Analytics – Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). Informationen zur Verwendung von Push-Nachrichten und In-App-Nachrichten mit den Experience Cloud-SDK finden Sie unter [Push-Nachrichten einrichten](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) und [In-App-Nachrichten einrichten](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

>[!IMPORTANT]
>
>Um In-App-Nachrichten zu nutzen, ist SDK-Version 4.2 (oder höher) **erforderlich**.

Sie können die Nachrichten und die Regeln in Adobe Mobile Services erstellen, die festlegen, wann die Nachrichten angezeigt werden. Weitere Informationen finden Sie unter [In-App-Nachrichten erstellen](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md). Um In-App-Nachrichten anzuzeigen, müssen Aktualisierungen am SDK vorgenommen werden. Sie können diese Schritte selbst dann ausführen, wenn Sie noch keine Nachrichten definiert haben. Nachdem Sie Nachrichten definiert haben, werden sie dynamisch an die App bereitgestellt und ohne Update des Appstores angezeigt.

## In-App-Nachrichten aktivieren {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zu Ihrem IntelliJ IDEA- oder Eclipse-Projekt hinzufügen* in [Grundlegende Implementierung und Lebenszyklus](/help/android/getting-started/dev-qs.md).

1. Aktualisieren Sie die Datei `AndroidManifest.xml`, um die Vollbildaktivität zu deklarieren und den Nachrichten-Handler zu aktivieren:

   ```java
   <activity  
   android:name="com.adobe.mobile.MessageFullScreenActivity"  
   android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

   Wenn Sie ein modales Layout gewählt haben, wählen Sie eines der folgenden Designs für die Nachricht aus:

   * `Theme.Translucent.NoTitleBar.Fullscreen`
   * `Theme.Translucent.NoTitleBar`
   * `Theme.Translucent`

   Beispiel:

   ```java
   <activity 
   android:name="com.adobe.mobile.MessageFullScreenActivity" 
   android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
   android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
   <receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
   ```

1. Importieren Sie die Bibliothek:

   ```java
   import com.adobe.mobile.*;
   ```

1. Übergeben Sie jedem `collectLifecycleData`-Aufruf `this`, um eine Referenz für Ihre aktuelle Aktivität bereitzustellen:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
   }
   ```

1. Überprüfen Sie, ob die Datei `ADBMobileConfig.json` die erforderlichen Einstellungen für In-App-Nachrichten enthält.

   >[!IMPORTANT]
   >
   >`messages` oder `remotes` ist erforderlich.

   Damit In-App-Nachrichten beim Start dynamisch aktualisiert werden können, muss das Objekt `remotes` vorhanden und ordnungsgemäß konfiguriert sein:

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

   Wenn dieses Objekt nicht konfiguriert ist, laden Sie die aktualisierte Datei `ADBMobileConfig.json` über Adobe Mobile Services herunter. Weitere Informationen finden Sie unter [Bevor Sie beginnen](/help/android/getting-started/requirements.md).

## In-App-Nachrichten verfolgen {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Mithilfe der mobilen SDK für Android lassen sich folgende Metriken Ihrer In-App-Nachrichten verfolgen:

* Für In-App-Nachrichten im Vollbild- und Warnhinweisstil:

   * **Impressionen**: Benutzer löst eine In-App-Nachricht aus.
   * **Clickthrough**: Benutzer betätigt **[!UICONTROL Clickthrough]**.
   * **Abbrechen**: Benutzer betätigt **[!UICONTROL Abbrechen]**.

* Für benutzerdefinierte Vollbild-In-App-Nachrichten muss der HTML-Inhalt der Nachricht den richtigen Code enthalten, um die SDK-Verfolgung über die Nutzung folgender Schaltflächen informieren zu können:

   * **Clickthrough** (Umleitung) der Beispielverfolgung:

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * **Abbrechen** (Schließen) der Beispielverfolgung:

      `adbinapp://cancel`

## Lokales Ausweichbild {#section_DEACC1CE549B4573B556A44A52409941}

Beim Erstellen einer Vollbildnachricht können Sie optional ein Ausweichbild angeben. Wenn Ihre Nachricht nicht in der Lage ist, das gewünschte Bild aus dem Internet abzurufen, versucht das SDK, das Bild mit demselben Namen aus dem Assets-Ordner Ihrer App zu laden. Auf diese Weise können Sie Ihre Nachricht in ihrer ursprünglichen Form anzeigen, auch wenn der Benutzer offline ist oder das vorgegebene Bild nicht erreichbar ist.

>[!IMPORTANT]
>
>Der Assetname des Ausweichbilds wird beim Konfigurieren der Nachricht in Adobe Mobile Services angegeben, und Sie müssen sicherstellen, dass die angegebene Ressource verfügbar ist.

## Benachrichtigungssymbole konfigurieren {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

Folgende Methoden ermöglichen es Ihnen, kleine und große Symbole zu konfigurieren. Die kleinen Symbole werden daraufhin in der Benachrichtigungsleiste angezeigt, während die großen im Benachrichtigungsfenster zum Einsatz kommen.

* **Config.setSmallIconResourceId(int resourceId)**

   Legt das kleine Symbol fest, das für die vom SDK erstellten Benachrichtigungen verwendet wird. Dieses Symbol wird in der Statusleiste angezeigt und ist das sekundäre Bild, das angezeigt wird, wenn der Benutzer die vollständige Benachrichtigung in der Mitteilungszentrale öffnet.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Hier finden Sie das Code-Beispiel für diese Methode:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   Legt das große Symbol fest, das für die vom SDK erstellten Benachrichtigungen verwendet wird. Dieses Symbol wird als primäres Bild angezeigt, wenn der Benutzer die vollständige Benachrichtigung in der Mitteilungszentrale öffnet.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```
