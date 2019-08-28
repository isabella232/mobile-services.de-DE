---
description: Diese Informationen helfen Ihnen beim Implementieren der iOS-Bibliothek und beim Erfassen von Lebenszyklusmetriken wie Starts, Upgrades, Sitzungen, eingebundene Benutzer usw.
seo-description: Diese Informationen helfen Ihnen beim Implementieren der iOS-Bibliothek und beim Erfassen von Lebenszyklusmetriken wie Starts, Upgrades, Sitzungen, eingebundene Benutzer usw.
seo-title: Grundlegende Implementierung und Lebenszyklus
solution: Marketing Cloud, Analytics
title: Grundlegende Implementierung und Lebenszyklus
topic: Entwickler und Implementierung
uuid: 96 d 06325-e 424-4770-8659-4 b 5431318 ee 3
translation-type: tm+mt
source-git-commit: f39c18e48dc72e0ed8e8e35d962a1ae028055b87

---


# Core implementation and lifecycle {#core-implementation-and-lifecycle}

Diese Informationen helfen Ihnen beim Implementieren der iOS-Bibliothek und beim Erfassen von Lebenszyklusmetriken wie Starts, Upgrades, Sitzungen, eingebundene Benutzer usw.

## SDK herunterladen {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>To download the SDKs, you **must** use iOS 6 or later.

**Voraussetzung**

Bevor Sie das SDK herunterladen, führen Sie die Schritte unter *Erstellen einer Report Suite* in der [Core-Implementierung und im Lebenszyklus](/help/ios/getting-started/requirements.md) durch, um eine Entwicklungs-Report Suite einzurichten und eine vorab ausgefüllte Version der Konfigurationsdatei herunterzuladen.

So laden Sie das SDK herunter:

1. Download, unzip the `[Your_App_Name_]AdobeMobileLibrary-4.*-iOS.zip` file and verify that you have the following software components:

   * `ADBMobile.h`: Hierbei handelt es sich um die Objective-C-Header-Datei, die für iOS AppMeasurement verwendet wird.
   * `ADBMobileConfig.json`: die SDK-Konfigurationsdatei, die für Ihre App angepasst ist.
   * `AdobeMobileLibrary.a`, eine Bitcode-fähige Fat Binary, die die Bibliotheksbuilds für ios-Geräte (armv 7, armv 7 s, arm 64) und Simulatoren (i 386, x 86_ 64) enthält.

      Diese Fat Binary sollte verknüpft werden, wenn das Ziel für eine iOS-App vorgesehen ist.

   * `AdobeMobileLibrary_Extension.a`: Hierbei handelt es sich um eine Bitcode-fähige Fat Binary, die die Bibliotheks-Builds für iOS-Geräte (armv7, armv7s, arm64) und Simulatoren (i386, x86_64) enthält.

      Diese Fat Binary sollte verknüpft werden, wenn das Ziel für eine iOS-Erweiterung vorgesehen ist.

   * `AdobeMobileLibrary_Watch.a`: Hierbei handelt es sich um eine Bitcode-fähige Fat Binary, die die Bibliotheks-Builds für Apple Watch-Geräte (armv7k) und Simulatoren (i386, x86_64) enthält.

      Diese Fat Binary sollte verknüpft werden, wenn das Ziel für eine App mit Apple Watch-Erweiterung (watchOS 2) vorgesehen ist.

   * `AdobeMobileLibrary_TV.a`: Hierbei handelt es sich um eine Bitcode-fähige Fat Binary, die die Bibliotheks-Builds für neue Apple TV-Geräte (arm64) und für den Simulator (x86_64) enthält.

      Diese Fat Binary sollte verknüpft werden, wenn das Ziel für eine Apple TV-App (tvOS) vorgesehen ist.

>[!IMPORTANT]
>
>If you download the SDK outside the Adobe Mobile services UI, the `ADBMobileConfig.json` file must be manually configured. If you are new to Analytics and the Mobile SDK, see [Before You Start](/help/ios/getting-started/requirements.md) to set up a development report suite and download a pre-populated version of the configuration file.

## Add the SDK and config file to your project {#section_93C25D893B4A4CD3B996CF3C5590C8DC}

1. Starten Sie die XCode IDE und öffnen Sie die App.
1. Ziehen Sie im Projektnavigator den Ordner `AdobeMobileLibrary` und legen Sie ihn unter Ihrem Projekt ab.
1. Stellen Sie Folgendes sicher:

   * Das Kontrollkästchen **[!UICONTROL Elemente kopieren, sofern erforderlich]ist aktiviert.**
   * **[!UICONTROL Gruppen erstellen]** ist ausgewählt.
   * Keines der Kontrollkästchen im Abschnitt **[!UICONTROL Zu Zielen hinzufügen]ist ausgewählt.**
   ![](assets/step_3.png)

1. Klicken Sie auf **[!UICONTROL Fertigstellen]**.
1. In **[!UICONTROL Project Navigator]**, select **[!UICONTROL`ADBMobileConfig.json`]**.
1. In **[!UICONTROL File Inspector]**, add the JSON file to any targets in your project that will use the Adobe SDK.

   ![](assets/step_4.png)

1. In **[!UICONTROL Project Navigator]**, complete the following steps:

   1. Klicken Sie auf Ihre App.
   1. Wählen Sie auf der Registerkarte **[!UICONTROL Allgemein]** Ihre Ziele aus und verknüpfen Sie die erforderlichen Frameworks und Bibliotheken in den Abschnitten **[!UICONTROL Verknüpfte Frameworks]und** Bibliotheken **.**
   * **iOS-App-Ziele**
      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary.a`
   * **iOS-Erweiterungsziel**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Extension.a`
   * **Apple Watch-Ziel (watchOS 2)**

      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_Watch.a`
   * **Apple TV-(tvOS-)Ziel**

      * `SystemConfiguration.framework`
      * `libsqlite3.0.tbd`
      * `AdobeMobileLibrary\_TV.a`
   >[!CAUTION]
   >
   > Linking more than one `AdobeMobileLibrary*.a` file in the same target will result in unexpected behavior or the inability to build.

1. Bestätigen Sie, dass Ihre App ohne Fehler erstellt wird.

## Implement lifecycle metrics {#section_532702562A7A43809407C9A2CBA80E1E}

>[!IMPORTANT]
>
>iOS will send lifecycle information with or without calling `collectlifecycledata`, and `collectlifecycledata` is only a way to initiate lifecycle earlier in the application's launch sequence.

After you enable lifecycle, each time your app is launched, one hit is sent to measure launches, upgrades, sessions, engaged users, and other [Lifecycle Metrics](/help/ios/metrics.md).

Fügen Sie einen `collectLifecycleData`/ `collectLifecycleDataWithAdditionalData` Aufruf in `application:didFinishLaunchingWithOptions`hinzu:

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
 [ADBMobile collectLifecycleData]; 
    return YES; 
}
```

### Zusätzliche Daten mit Lebenszyklusaufrufen einbeziehen

Verwenden Sie `collectLifecycleDataWithAdditionalData`, um zusätzliche Daten mit Lebenszyklusmetrikdaten einzubeziehen:

>[!IMPORTANT]
>
>Any data that is passed to the SDK through `collectLifecycleDataWithAdditionalData:` is persisted in `NSUserDefaults` by the SDK. Das SDK entfernt die Werte im Parameter `NSDictionary`, die nicht vom Typ `NSString` oder `NSNumber` sind.

```objective-c
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions { 
    NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
    [contextData setObject:@"Game" forKey:@"myapp.category"]; 
    [ADBMobile collectLifecycleDataWithAdditionalData:contextData]; 
    return YES; 
}
```

Zusätzliche Kontextdatenwerte, die mit `collectLifecycleDataWithAdditionalData` gesendet werden, müssen benutzerdefinierten Variablen in Adobe Mobile Services zugeordnet sein:

![](assets/map-variable-lifecycle.png)

Andere Lebenszyklusmetriken werden automatisch erfasst. Weitere Informationen finden Sie unter  [Lebenszyklusmetriken](/help/ios/metrics.md).

## Nächste Schritte {#section_A24DC703359D4B5C8F493D6421306FD3}

Führen Sie die folgenden Aufgaben durch:

* [App-Zustände verfolgen](/help/ios/analytics-main/states.md)
* [App-Aktionen verfolgen](/help/ios/analytics-main/actions.md)
