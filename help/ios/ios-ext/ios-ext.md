---
description: Mithilfe der iOS-Erweiterung können Sie Nutzungsdaten aus Ihren Apple Watch-Apps (WatchOS 1), Today Widgets, Fotobearbeitungs-Widgets und anderen iOS-Erweiterungs-Apps erfassen.
seo-description: Mithilfe der iOS-Erweiterung können Sie Nutzungsdaten aus Ihren Apple Watch-Apps (WatchOS 1), Today Widgets, Fotobearbeitungs-Widgets und anderen iOS-Erweiterungs-Apps erfassen.
seo-title: Implementierung der iOS-Erweiterung
solution: Marketing Cloud,Analytics
title: Implementierung der iOS-Erweiterung
topic: Entwickler und Implementierung
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
translation-type: tm+mt
source-git-commit: 718e336b9002fe3d5282697d4302d12a89297181

---


# iOS extension implementation {#ios-extension-implementation}

Mithilfe der iOS-Erweiterung können Sie Nutzungsdaten aus Ihren Apple Watch-Apps (WatchOS 1), Today Widgets, Fotobearbeitungs-Widgets und anderen iOS-Erweiterungs-Apps erfassen.

## New Adobe Experience Platform Mobile SDK Release

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* To get started, go to Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.

## Recommendations for using the iOS SDK instead of your wrapper {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>Es wird dringend empfohlen, das iOS-SDK anstelle des Wrapper zu verwenden.

Apple bietet einen Satz APIs, über die die Watch-Anwendung mit der übergeordneten Anwendung kommuniziert, indem Anfragen an die übergeordnete Anwendung gesendet und Antworten empfangen werden. Es ist zwar möglich, Verfolgungsdaten als Wörterbuch von der Watch-Anwendung an die übergeordnete Anwendung zu senden und die übergeordnete Anwendung anschließend über eine beliebige Verfolgungsmethode zum Senden der Daten aufzufordern, jedoch gibt es bei dieser Methode Einschränkungen.

In most cases when a user is using the Watch app, the containing app is running in the background, and it is only safe to call `TrackActionInBackground`, `TrackLocation`, and `TrackBeacon`. Andere Tracking-Methoden aufzurufen würde Lebenszyklusdaten beeinträchtigen, also sollten Sie nur diese drei Methoden verwenden, um Daten von der Watch-Anwendung zu senden.

Selbst wenn diese drei Verfolgungsmethoden Ihren Anforderungen genügen, sollten Sie das iOS-SDK verwenden, da das SDK für die Watch-App alle Mobilgerät-Funktionen außer In-App-Nachrichten enthält.

## Erste Schritte {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>Vergewissern Sie sich, dass Sie über ein Projekt mit mindestens den folgenden Zielen verfügen:
>
>* ein Ziel, das in der App enthalten sein soll.
>* ein Ziel für die Erweiterung.
>



Wenn Sie in einer WatchKit-App arbeiten, sollten Sie über ein drittes Ziel verfügen. For more information on developing for Apple Watch, see [Developing for Apple Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1).

## Configure the containing app {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

Führen Sie die folgenden Schritte in Ihrem Xcode-Projekt aus:

1. Ziehen Sie den Ordner AdobeMobileLibrary in Ihr Projekt.
1. Ensure that the `ADBMobileConfig.json` file is a member of the containing app's target.
1. Erweitern Sie auf der Registerkarte **[!UICONTROL Build-Phasen]** des Ziels Ihrer übergeordneten App den Abschnitt **Binärdatei mit Bibliotheken verknüpfen]und fügen Sie die folgenden Bibliotheken hinzu:[!UICONTROL **

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open the **[!UICONTROL Capabilities]** tab of the containing app's target, enable **[!UICONTROL App Groups]**, and add a new app group (for example, `group.com.adobe.testAp`).

1. Legen Sie in Ihrem Anwendungsdelegat die App-Gruppe in `application:didFinishLaunchingWithOptions` fest, bevor Sie mit der Adobe Mobile-Bibliothek interagieren:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Bestätigen Sie, dass Ihre App ohne unerwartete Fehler erstellt wird.

## -Erweiterung konfigurieren{#section_28C994B7892340AC8D1F07AF26FF3946}

1. Ensure that the `ADBMobileConfig.json` file is a member of the extension's target.
1. Erweitern Sie auf der Registerkarte **[!UICONTROL Build-Phasen]** des Ziels Ihrer Erweiterung den Abschnitt **Binärdatei mit Bibliotheken verknüpfen]und fügen Sie die folgenden Bibliotheken hinzu:[!UICONTROL **

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Open the **[!UICONTROL Capabilities]** tab of the extension's target, enable **[!UICONTROL App Groups]**, and select the app group that you added in step 4 of *Configuring the Containing App* above.

1. In your InterfaceController, set the app group in `awakeWithContext:` before making any other interactions with the Adobe Mobile library:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Bestätigen Sie, dass Ihre App ohne unerwartete Fehler erstellt wird.

## Additional notes {#section_21497E81231549CB9F164DEECFF5BA0D}

Hinweis:

* Ein zusätzlicher Kontextdatenwert mit dem Namen `a.RunMode` wurde hinzugefügt, um anzugeben, ob die Daten aus Ihrer übergeordneten App oder Ihrer Erweiterung stammen:

   * `a.RunMode = Application`

      Dieser Wert bedeutet, dass der Treffer aus der übergeordneten App stammt.
   * `a.RunMode = Extension`

      Dieser Wert bedeutet, dass der Treffer aus der Erweiterung stammt.

* Wenn Sie über eine ältere Version des SDK ein Upgrade vornehmen, migriert Adobe beim Start der übergeordneten App automatisch alle Benutzerstandardeinstellungen und zwischengespeicherten Dateien aus dem Ordner der übergeordneten App zum freigegebenen Ordner der App-Gruppe.
* Wenn die übergeordnete App niemals gestartet wird, werden die Treffer aus der Erweiterung verworfen.
* Die Versionsnummer und Buildnummer müssen zwischen Ihrer übergeordneten App und der Erweiterungs-App identisch sein.
* Für iOS-Erweiterungs-Apps wird kein Lebenszyklusaufruf ausgelöst.

