---
description: Mithilfe der iOS-Erweiterung können Sie Nutzungsdaten aus Ihren Apple Watch-Apps (WatchOS 1), Today Widgets, Fotobearbeitungs-Widgets und anderen iOS-Erweiterungs-Apps erfassen.
seo-description: Mithilfe der iOS-Erweiterung können Sie Nutzungsdaten aus Ihren Apple Watch-Apps (WatchOS 1), Today Widgets, Fotobearbeitungs-Widgets und anderen iOS-Erweiterungs-Apps erfassen.
seo-title: Implementierung der iOS-Erweiterung
solution: Experience Cloud,Analytics
title: Implementierung der iOS-Erweiterung
topic: Developer and implementation
uuid: 8afc03fe-403e-4643-ada1-30e403ede238
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '721'
ht-degree: 100%

---


# Implementierung der iOS-Erweiterung {#ios-extension-implementation}

Mithilfe der iOS-Erweiterung können Sie Nutzungsdaten aus Ihren Apple Watch-Apps (WatchOS 1), Today Widgets, Fotobearbeitungs-Widgets und anderen iOS-Erweiterungs-Apps erfassen.

## Neue Version des Adobe Experience Platform Mobile SDK

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie [hier](https://aep-sdks.gitbook.io/docs/), um unsere aktuelle Dokumentation abzurufen.

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDK können über [Experience Platform Launch](https://www.adobe.com/de/experience-platform/launch.html) konfiguriert werden.

* Beginnen Sie mit Adobe Experience Platform Launch.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.

## Empfehlungen für das Verwenden des iOS-SDK anstelle Ihres Wrappers {#section_97577331FD9E4FFBBE05D402C67AEE69}

>[!IMPORTANT]
>
>Wir empfehlen ausdrücklich die Verwendung des iOS SDK statt Ihres eigenen Wrappers.

Apple bietet eine Reihe von APIs, mit denen die Watch-App mit der übergeordneten App kommunizieren kann, indem Anfragen an die übergeordnete App gesendet und die Antworten empfangen werden. Obwohl Sie Tracking-Daten als Wörterbuch von der Watch-App an die übergeordnete App senden und eine beliebige Tracking-Methode für die übergeordnete App aufrufen können, um die Daten zu senden, weist diese Lösung Einschränkungen auf.

Wenn ein Benutzer die Watch-App verwendet, läuft die übergeordnete App meistens im Hintergrund und es ist nur sicher, `TrackActionInBackground`, `TrackLocation` und `TrackBeacon` aufzurufen. Andere Tracking-Methoden aufzurufen würde Lebenszyklusdaten beeinträchtigen, also sollten Sie nur diese drei Methoden verwenden, um Daten von der Watch-Anwendung zu senden.

Selbst wenn diese drei Verfolgungsmethoden Ihren Anforderungen genügen, sollten Sie das iOS-SDK verwenden, da das SDK für die Watch-App alle Mobilgerät-Funktionen außer In-App-Nachrichten enthält.

## Erste Schritte {#section_D0BE4F780C9C4CD8ADD2AD4EE0BD5FD4}

>[!IMPORTANT]
>
>Stellen Sie sicher, dass Sie ein Projekt mit mindestens den folgenden Zielen haben:
>
>* Ein Ziel, das die App enthalten soll.
>* Ein Ziel für die Erweiterung.

>



Wenn Sie an einer WatchKit-App arbeiten, sollten Sie über ein drittes Ziel verfügen. Weitere Informationen zur Entwicklung für Apple Watch finden Sie unter [Developing for Apple Watch](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/index.html#//apple_ref/doc/uid/TP40014969-CH8-SW1).

## Übergeordnete Apps konfigurieren {#section_0BAB0842E4C04A62B5E03DFC4BA77851}

Führen Sie die folgenden Schritte in Ihrem Xcode-Projekt aus:

1. Ziehen Sie den Ordner AdobeMobileLibrary in Ihr Projekt.
1. Stellen Sie sicher, dass die Datei `ADBMobileConfig.json` ein Mitglied des Ziels Ihrer übergeordneten App ist.
1. Erweitern Sie auf der Registerkarte **[!UICONTROL Build-Phasen]** des Ziels Ihrer übergeordneten App den Abschnitt **[!UICONTROL Binärdatei mit Bibliotheken verknüpfen]** und fügen Sie die folgenden Bibliotheken hinzu:

   * `AdobeMobileLibrary.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Öffnen Sie die Registerkarte **[!UICONTROL Funktionen]** des Ziels der übergeordneten App, aktivieren Sie **[!UICONTROL App-Gruppen]** und fügen Sie eine neue App-Gruppe hinzu (beispielsweise `group.com.adobe.testAp`).

1. Legen Sie in Ihrem Anwendungsdelegat die App-Gruppe in `application:didFinishLaunchingWithOptions` fest, bevor Sie mit der Adobe Mobile-Bibliothek interagieren:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Bestätigen Sie, dass Ihre App ohne unerwartete Fehler erstellt wird.

## Erweiterungen konfigurieren {#section_28C994B7892340AC8D1F07AF26FF3946}

1. Stellen Sie sicher, dass die Datei `ADBMobileConfig.json` ein Mitglied des Ziels der Erweiterung ist.
1. Erweitern Sie auf der Registerkarte **[!UICONTROL Build-Phasen]** des Ziels Ihrer Erweiterung den Abschnitt **[!UICONTROL Binärdatei mit Bibliotheken verknüpfen]** und fügen Sie die folgenden Bibliotheken hinzu:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.dylib`
   * `SystemConfiguration.framework`

1. Öffnen Sie die Registerkarte **[!UICONTROL Funktionen]** des Ziels der Erweiterung, aktivieren Sie **[!UICONTROL App-Gruppen]** und wählen Sie dann die App-Gruppe aus, die Sie oben in Schritt 4 *Übergeordnete Apps konfigurieren* hinzugefügt haben.

1. Legen Sie in Ihrem InterfaceController die App-Gruppe in `awakeWithContext:` fest, bevor Sie mit der Adobe Mobile-Bibliothek interagieren:

   ```objective-c
   [ADBMobile 
         setAppGroup:@"group.com.adobe.testApp"];
   ```

1. Bestätigen Sie, dass Ihre App ohne unerwartete Fehler erstellt wird.

## Weitere Hinweise {#section_21497E81231549CB9F164DEECFF5BA0D}

Hinweis:

* Ein zusätzlicher Kontextdatenwert mit dem Namen `a.RunMode` wurde hinzugefügt, um anzugeben, ob die Daten aus Ihrer übergeordneten App oder Ihrer Erweiterung stammen:

   * `a.RunMode = Application`

      Dieser Wert bedeutet, dass der Treffer aus der übergeordneten App stammt.
   * `a.RunMode = Extension`

      Dieser Wert bedeutet, dass der Treffer aus der Erweiterung stammt.

* Wenn Sie ein Upgrade von einer älteren Version des SDK durchführen, migriert Adobe beim Start der übergeordneten App automatisch alle Benutzervorgaben und zwischengespeicherten Dateien aus dem Ordner der übergeordneten App in den gemeinsamen Ordner der App-Gruppe.
* Wenn die übergeordnete App nie gestartet wird, werden Treffer aus der Erweiterung verworfen.
* Die Versionsnummer und die Build-Nummer müssen zwischen der übergeordneten App und der Erweiterung-App identisch sein.
* Für iOS-Erweiterungs-Apps wird kein Lebenszyklusaufruf ausgelöst.

