---
description: In Adobe Mobile Services können Akquise-Links mit eindeutigen Trackingcodes generiert werden. Wenn ein Benutzer eine App aus dem App Store herunterlädt und ausführt, nachdem er auf den generierten Link geklickt hat, erfasst und sendet das SDK die Akquise-Daten automatisch und sendet sie an Adobe Mobile Services.
keywords: android;library;mobile;sdk
seo-description: In Adobe Mobile Services können Akquise-Links mit eindeutigen Trackingcodes generiert werden. Wenn ein Benutzer eine App aus dem App Store herunterlädt und ausführt, nachdem er auf den generierten Link geklickt hat, erfasst und sendet das SDK die Akquise-Daten automatisch und sendet sie an Adobe Mobile Services.
seo-title: Mobile App – Akquise
solution: Marketing Cloud, Analytics
title: Mobile App – Akquise
topic: Entwickler und Implementierung
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Mobile app acquisition {#mobile-app-acquisition}

In Adobe Mobile Services können Akquise-Links mit eindeutigen Trackingcodes generiert werden. When a user downloads and runs an app from the App store after clicking on the generated link, the SDK automatically collects and sends the acquisition data to Adobe Mobile services.

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.

>[!IMPORTANT]
>
>Um die Akquise zu nutzen, ist SDK-Version 4.1 oder höher **erforderlich**.

Akquise-Links müssen in Adobe Mobile Services generiert werden. For more information, see [Acquisition](/help/using/acquisition-main/acquisition-main.md).

**In SDK-Versionen 4.13.1 und höher**:

Wenn Sie die in Adobe Mobile Services generierten Akquise-Links nicht verwenden können, können die Akquise-Daten mithilfe von Google Play Acquisition dennoch von dem SDK erfasst und gesendet werden.

So erfassen Sie Akquise-Daten aus einer standardmäßigen Google Play Acquisition-Kampagne:

* Verwenden Sie die standardmäßige Google Play Store-Methode.

   Benutzerdefinierte Akquise-Daten können mit den standardmäßigen Google Play Acquisition-Wertepaaren verwendet werden.

* Wenn der Benutzer eine App als Ergebnis der Google Play Store-Akquise herunterlädt und ausführt, werden die Daten vom Referrer erfasst und an Adobe Mobile Services gesendet.

   * The data is stored and available in the `AdobeDataCallback` instance that was registered earlier with the SDK.

      Weitere Informationen finden Sie unter [Konfigurationsmethoden](/help/android/configuration/methods.md).

   * Es wird der Ereignistyp `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` oder der `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` Ereignistyp verwendet.

   * Benutzerdefinierte Schlüssel, die Teil der Akquise-Daten aus Google Play waren, erhalten den Namensraum „`a.acquisition.custom.`“.

Wenn Sie Akquise-Links verwenden, die in Adobe Mobile Services generiert wurden, fügen Sie benutzerdefinierte Kundendaten zum Akquise-Link hinzu, indem Sie folgende Aufgaben ausführen:

1. Setzen Sie der Akquise-Variablen das Präfix „`adb`“ voran.

   When the SDK receives the acquisition data from Adobe Mobile Services (on first launch), that data will be stored and also available in the `AdobeDataCallback` instance registered earlier with the SDK, as mentioned in [Configuration Methods](/help/android/configuration/methods.md).

1. Der Ereignistyp `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` oder der `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` Ereignistyp wird verwendet.

1. The custom data keys are prefixed with "`a.acquisition.custom.`"

>[!TIP]
>
>Wenn Sie Daten an mehrere Report Suites senden, verwenden Sie die Akquise-Daten der App, die mit der ersten Report Suite in Ihrer Liste der Report Suite-IDs verknüpft ist.

Die Updates in diesem Abschnitt ermöglichen es dem SDK, Akquise-Daten von einem Akquise-Link zu senden.

## Tracking mobile acquisition {#section_CEA30C652AC8470784B8054E299B80FA}

1. Add the library [to your project and implement lifecycle.

   Weitere Informationen finden Sie unter *SDK- und Konfigurationsdatei zu Ihrer IntelliJ-IDEA- oder Eclipse-Projekt* in der [Core-Implementierung und im Lebenszyklus](/help/android/getting-started/dev-qs.md)hinzufügen.

1. Importieren Sie die Bibliothek:

   ```java
   import com.adobe.mobile.*;
   ```

1. Implementieren Sie den `BroadcastReceiver` für den Referrer:

   ```java
   package com.your.package.name;  // replace with your app package name 
   
   import android.content.BroadcastReceiver; 
   import android.content.Context; 
   import android.content.Intent; 
   
   public class GPBroadcastReceiver extends BroadcastReceiver { 
     @Override 
     public void onReceive(Context c, Intent i) { 
      com.adobe.mobile.Analytics.processReferrer(c, i); 
     } 
   }
   ```

1. Aktualisieren Sie `AndroidManifest.xml`, um den `BroadcastReceiver` zu aktivieren, der im vorherigen Schritt erstellt wurde:

   ```xml
   <receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true"> 
    <intent-filter> 
     <action android:name="com.android.vending.INSTALL_REFERRER" /> 
    </intent-filter> 
   </receiver>
   ```

1. Verify that the `ADBMobileConfig.json` file contains the required acquisition settings:

   ```xml
   "acquisition": { 
      "server": "c00.adobe.com", 
      "appid": "0652024f-adcd-49f9-9bd7-2552a4565d2f" 
   }, 
   "analytics": { 
     "referrerTimeout": 5, 
     ...
   ```

   >[!IMPORTANT]
   >
   >Wenn Sie Daten an mehrere Report Suites senden, verwenden Sie Akquise-Einstellungen (Akquise-Server und AppID) aus der App, die der ersten Report Suite in Ihrer Liste der Report Suite-IDs zugewiesen ist.

   The `acquisition` settings are generated by Adobe Mobile services and should not be changed. For more information about how to download a customized `ADBMobileConfig.json` file with the `acquisition` settings pre-configured, see [Before You Start](/help/android/getting-started/requirements.md).

Wenn diese Einstellungen aktiviert sind, werden nach dem ersten Start der App automatisch Akquise-Daten mit dem ersten Lebenszyklusaufruf gesendet.

>[!CAUTION]
>
>`referrerTimeout`  muss auf einen höheren Wert als 0 festgelegt werden, um die App-Akquise zu aktivieren.
