---
description: In Adobe Mobile Services können Akquise-Links mit eindeutigen Trackingcodes generiert werden. Wenn ein Benutzer eine App vom Appstore herunterlädt und ausführt, nachdem er auf den generierten Link geklickt hat, erfasst das SDK automatisch die Akquisedaten und sendet sie an Adobe Mobile Services.
keywords: android;library;mobile;sdk
seo-description: In Adobe Mobile Services können Akquise-Links mit eindeutigen Trackingcodes generiert werden. Wenn ein Benutzer eine App vom Appstore herunterlädt und ausführt, nachdem er auf den generierten Link geklickt hat, erfasst das SDK automatisch die Akquisedaten und sendet sie an Adobe Mobile Services.
seo-title: Mobile App – Akquise
solution: Marketing Cloud,Analytics
title: Mobile App – Akquise
topic: Developer and implementation
uuid: 4d32eae9-e856-4e40-8a29-2b5bccd106e0
translation-type: tm+mt
source-git-commit: 8a25259732a916f977f733cd22971b1d847aae5f

---


# App-Akquise {#mobile-app-acquisition}

In Adobe Mobile Services können Akquise-Links mit eindeutigen Trackingcodes generiert werden. Wenn ein Benutzer eine App vom Appstore herunterlädt und ausführt, nachdem er auf den generierten Link geklickt hat, erfasst das SDK automatisch die Akquisedaten und sendet sie an Adobe Mobile Services.

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDK können über [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.

>[!IMPORTANT]
>
>Um die Akquise zu nutzen, ist SDK-Version 4.1 oder höher **erforderlich**.

Akquise-Links müssen in Adobe Mobile Services generiert werden. Weitere Informationen finden Sie in [Akquise](/help/using/acquisition-main/acquisition-main.md).

**In SDK-Versionen 4.18.0 und höher**:

Ab dem 1. März 2020 stellt Google den Übertragungsmechanismus install_referrer bereit. Weitere Informationen finden Sie [noch unter InstallBroadcast verwenden? Wechseln Sie bis zum 1. März 2020](https://android-developers.googleblog.com/2019/11/still-using-installbroadcast-switch-to.html)zur Play Referrer-API. Um weiterhin Informationen zu verweisenden Stellen im Google Play Store zu sammeln, aktualisieren Sie Ihre Anwendung auf SDK Version 4.18.0 oder höher.

Mit dieser Einstellung müssen Sie anstelle der Erstellung einer `BroadcastReceiver`URL die URL der verweisenden Stelle für die Installation von einer neuen Google-API erfassen und die resultierende URL an das SDK übergeben.

1. Fügen Sie das Google Play Install Referrer-Paket zu den Abhängigkeiten Ihrer Datei hinzu:

   `implementation 'com.android.installreferrer:installreferrer:1.1'`

1. Um die Referrer-URL aus der Install Referrer-API abzurufen, führen Sie die Schritte unter [Abrufen der Installationsreferrer](https://developer.android.com/google/play/installreferrer/library#install-referrer)durch.

1. URL der verweisenden Stelle an das SDK übergeben:

   `Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);`

>[!IMPORTANT]
>
>Um unnötige API-Aufrufe in Ihrer App zu vermeiden, empfiehlt Google, die API nur einmal unmittelbar nach der Installation aufzurufen.

Informationen zur optimalen Verwendung der Referrer-APIs für die Google Play-Installation in Ihrer App finden Sie in der Google-Dokumentation. Hier ein Beispiel für die Verwendung des Adobe SDK mit den Referrer-APIs für die Google Play-Installation:

```java
void handleGooglePlayReferrer() {
    // Google recommends only calling this API the first time you need it:
    // https://developer.android.com/google/play/installreferrer/library#install-referrer

    // Store a boolean in SharedPreferences to ensure we only call it once.
    final SharedPreferences prefs = getSharedPreferences("acquisition", 0);
    if (prefs != null) {
        if (prefs.getBoolean("referrerHasBeenProcessed", false)) {
            return;
        }
    }

    final InstallReferrerClient referrerClient = InstallReferrerClient.newBuilder(getApplicationContext()).build();
    referrerClient.startConnection(new InstallReferrerStateListener() {
        private boolean complete = false;

        @Override
        public void onInstallReferrerSetupFinished(int responseCode) {
            switch (responseCode) {
                case InstallReferrerClient.InstallReferrerResponse.OK:
                    // connection is established
                    complete();
                    try {
                        final ReferrerDetails details = referrerClient.getInstallReferrer();                        

                        // pass the install referrer url to the SDK
                        Analytics.processGooglePlayInstallReferrerUrl(details.getInstallReferrer());

                    } catch (final RemoteException ex) {
                        Log.w("Acquisition - RemoteException while retrieving referrer information (%s)", ex.getLocalizedMessage() == null ? "unknown" : ex.getLocalizedMessage());
                    } finally {
                        referrerClient.endConnection();
                    }
                    break;
                case InstallReferrerClient.InstallReferrerResponse.FEATURE_NOT_SUPPORTED:
                case InstallReferrerClient.InstallReferrerResponse.SERVICE_UNAVAILABLE:
                default:
                    // API not available in the Play Store app - nothing to do here
                    complete();
                    referrerClient.endConnection();
                    break;
            }
        }

        @Override
        public void onInstallReferrerServiceDisconnected() {
            if (!complete) {
                // something went wrong trying to get a connection, try again
                referrerClient.startConnection(this);
            }
        }

        void complete() {
            complete = true;
            SharedPreferences.Editor editor = getSharedPreferences("acquisition", 0).edit();
            editor.putBoolean("referrerHasBeenProcessed", true);
            editor.apply();
        }
    });
}
```

**In SDK-Versionen 4.13.1 und höher**:

Wenn Sie die in Adobe Mobile Services generierten Akquise-Links nicht verwenden können, können die Akquise-Daten mithilfe von Google Play Acquisition dennoch von dem SDK erfasst und gesendet werden.

So erfassen Sie Akquise-Daten aus einer standardmäßigen Google Play Acquisition-Kampagne:

* Verwenden Sie die standardmäßige Google Play Store-Akquisemethode.

   Benutzerdefinierte Akquise-Daten können mit den standardmäßigen Google Play Acquisition-Wertepaaren verwendet werden.

* Wenn der Benutzer eine App als Ergebnis der Google Play Store-Akquise herunterlädt und ausführt, werden die Daten vom Referrer erfasst und an Adobe Mobile Services gesendet.

   * Die Daten werden gespeichert und stehen in der `AdobeDataCallback`-Instanz zur Verfügung, die zuvor mit dem SDK registriert wurde.

      Weitere Informationen finden Sie unter [Konfigurationsmethoden](/help/android/configuration/methods.md).

   * Es wird der Ereignistyp `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` oder `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` verwendet.

   * Benutzerdefinierte Schlüssel, die Teil der Akquise-Daten aus Google Play waren, erhalten den Namensraum „`a.acquisition.custom.`“.

Wenn Sie Akquise-Links verwenden, die in Adobe Mobile Services generiert wurden, fügen Sie benutzerdefinierte Kundendaten zum Akquise-Link hinzu, indem Sie folgende Aufgaben ausführen:

1. Setzen Sie der Akquise-Variablen das Präfix „`adb`“ voran.

   Wenn das SDK beim ersten Start die Akquise-Daten von Adobe Mobile Services erhält, werden die Daten gespeichert und stehen in der `AdobeDataCallback` Instanz zur Verfügung, die zuvor mit dem SDK registriert wurde. Weitere Informationen finden Sie unter [Konfigurationsmethoden](/help/android/configuration/methods.md).

1. Es wird der Ereignistyp `MobileDataEvent.MOBILE_EVENT_ACQUISITION_INSTALL` oder `MobileDataEvent.MOBILE_EVENT_ACQUISITION_LAUNCH` verwendet.

1. Den benutzerspezifischen Datenschlüsseln wird das Präfix `a.acquisition.custom.` vorangestellt.

>[!TIP]
>
>Wenn Sie Daten an mehrere Report Suites senden, verwenden Sie Akquise-Daten aus der App, die der ersten Report Suite in Ihrer Liste der Report Suite-IDs zugewiesen ist.

Die Updates in diesem Abschnitt ermöglichen es dem SDK, Akquise-Daten von einem Akquise-Link zu senden.

## Mobile Akquise verfolgen {#section_CEA30C652AC8470784B8054E299B80FA}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zu Ihrem IntelliJ IDEA- oder Eclipse-Projekt hinzufügen* in [Grundlegende Implementierung und Lebenszyklus](/help/android/getting-started/dev-qs.md).

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

1. Stellen Sie sicher, dass die Datei `ADBMobileConfig.json` die erforderlichen Akquise-Einstellungen enthält:

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
   >Wenn Sie Daten an mehrere Report Suites senden, verwenden Sie die Akquise-Einstellungen (Akquise-Server und AppId) aus der App, die der ersten Report Suite in Ihrer Liste der Report Suite-IDs zugewiesen ist.

   Die Einstellungen für `acquisition` werden von Adobe Mobile Services generiert und sollten nicht geändert werden. Weitere Informationen zum Herunterladen einer angepassten `ADBMobileConfig.json`-Datei mit vorkonfigurierten Einstellungen für `acquisition` finden Sie unter [Vorbereitung](/help/android/getting-started/requirements.md).

Wenn diese Einstellungen aktiviert sind, werden nach dem ersten Start der App automatisch Akquise-Daten mit dem ersten Lebenszyklusaufruf gesendet.

>[!CAUTION]
>
>`referrerTimeout` muss auf einen Wert größer als 0 festgelegt werden, um die App-Akquise zu aktivieren.
