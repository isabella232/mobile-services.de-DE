---
description: Sie können In-App-Nachrichten bereitstellen, die durch beliebige Analytics-Daten oder -Ereignisse ausgelöst werden. Nach der Implementierung werden Nachrichten dynamisch an die App bereitgestellt und erfordern keine Code-Änderung.
seo-description: Sie können In-App-Nachrichten bereitstellen, die durch beliebige Analytics-Daten oder -Ereignisse ausgelöst werden. Nach der Implementierung werden Nachrichten dynamisch an die App bereitgestellt und erfordern keine Code-Änderung.
seo-title: In-App-Nachrichten
solution: Marketing Cloud, Analytics
title: In-App-Nachrichten
topic: Entwickler und Implementierung
uuid: 351 ee 3 d 2-80 b 9-4 f 2 d -9696-21 f 274 d 89 f 5 a
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# In-App-Nachrichten {#in-app-messaging}

Sie können In-App-Nachrichten bereitstellen, die durch beliebige Analytics-Daten oder -Ereignisse ausgelöst werden. Nach der Implementierung werden Nachrichten dynamisch an die App bereitgestellt und erfordern keine Code-Änderung.

## Neue Adobe Experience Cloud SDK-Version

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

>[!IMPORTANT]
>
>Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* Gehen Sie zu [Launch](https://launch.adobe.com/), um zu beginnen.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as in-app messaging and push notifications. Weitere Informationen finden Sie unter [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). For more information about using push messaging and in-app messaging with the Experience Cloud SDKs, see [Set up push messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) and [Set up in-app messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

>[!IMPORTANT]
>
>Um In-App-Nachrichten zu nutzen, ist SDK-Version 4.2 (oder höher) **erforderlich**.

Sie können in Adobe Mobile Services Nachrichten erstellen und Regeln festlegen, die definieren, wann Nachrichten angezeigt werden. Weitere Informationen finden Sie unter [In-App-Nachricht erstellen](/help/using/in-app-messaging/t-in-app-message/t-in-app-message.md). Um In-App-Nachrichten anzuzeigen, müssen Updates am SDK vorgenommen werden. Sie können diese Schritte ausführen, auch wenn Sie bisher keine Nachrichten definiert haben. Nachdem Sie Nachrichten definiert haben, werden sie dynamisch an die App bereitgestellt und ohne Update des App Stores angezeigt.

## Enabling in-app messaging {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Config File to your intellij IDEA oder Eclipse Project* in [Core Implementation and Lifecycle](/help/android/getting-started/dev-qs.md).

1. Update the `AndroidManifest.xml` file to declare the full screen activity and enable the Message Notification Handler:

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

1. In each `collectLifecycleData` call, pass `this` to provide a reference to your current activity:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
   }
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required settings for in-app messaging.

   >[!IMPORTANT]
   >
   >`messages``remotes` oder ist erforderlich.

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

   If this object is not configured, download an updated `ADBMobileConfig.json` file from Adobe Mobile services. Weitere Informationen finden Sie unter [Bevor Sie beginnen](/help/android/getting-started/requirements.md).

## Tracking in-app messages {#section_B85CDF6929564AAEA79338B55E5CB1E8}

Mithilfe der mobilen SDKs für Android lassen sich folgende Metriken Ihrer In-App-Nachrichten verfolgen:

* Für In-App-Vollbild- und -Warnnachrichten:

   * **Impressionen:** Benutzer löst eine In-App-Nachricht aus.
   * **Durchklickraten: wenn der Benutzer****klickt.**
   * **Abbricht**: wenn der Benutzer **[!UICONTROL auf Abbrechen klickt]**.

* Für benutzerdefinierte Vollbild-In-App-Nachrichten muss der HTML-Inhalt der Nachricht den richtigen Code enthalten, um die SDK-Verfolgung über die Nutzung folgender Schaltflächen informieren zu können:

   * **Clickthrough-Beispielverfolgung** (Umleitung):

      `adbinapp://confirm/?url=https://www.yoursite.com`
   * **Beispielverfolgung abbrechen** (schließen):

      `adbinapp://cancel`

## Local fallback image {#section_DEACC1CE549B4573B556A44A52409941}

Beim Erstellen einer Vollbildnachricht können Sie optional ein Fallback-Bild angeben. Wenn die Nachricht das ursprüngliche Bild nicht aus dem Web abrufen kann, versucht das SDK stattdessen, das Bild mit demselben Namen aus dem Ordner „assets“ Ihrer Anwendung zu laden. So können Sie die Nachricht in ihrer ursprünglichen Form anzeigen, selbst wenn der Benutzer offline oder das eigentliche Bild nicht erreichbar ist.

>[!IMPORTANT]
>
>Der Name des Ausweichbilds wird beim Konfigurieren der Nachricht in Adobe Mobile-Diensten angegeben und Sie müssen sicherstellen, dass die angegebene Ressource verfügbar ist.

## Configuring notification icons {#section_DDA28BDBCBB748BCBECF3AB50A177D48}

Folgende Methoden ermöglichen es Ihnen, kleine und große Symbole zu konfigurieren. Die kleinen Symbole werden daraufhin in der Benachrichtigungsleiste angezeigt, während die großen im Benachrichtigungsfenster zum Einsatz kommen.

* **Config.setSmallIconResourceId(int resourceId)**

   Legt das kleine Symbol fest, das für die vom SDK erstellten Benachrichtigungen verwendet wird. Dieses Symbol wird in der Statusleiste angezeigt. Es wird als sekundäres Bild angezeigt, wenn der Benutzer die vollständige Benachrichtigung im Notification Center öffnet.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void setSmallIconResourceId(final int resourceId); 
      ```

   * Hier finden Sie das Codebeispiel für diese Methode:

      ```java
      Config.setSmallIconResourceId(R.drawable.appIcon);
      ```

* **Config.setLargeIconResourceId(int resourceId)**

   Legt das große Symbol fest, das für die vom SDK erstellten Benachrichtigungen verwendet wird. Dieses Symbol ist das primäre Bild, das angezeigt wird, wenn der Benutzer die vollständige Benachrichtigung im Benachrichtigungszentrum sieht.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void setLargeIconResourceId(final int resourceId); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Config.setLargeIconResourceId(R.drawable.appIcon); 
      ```
