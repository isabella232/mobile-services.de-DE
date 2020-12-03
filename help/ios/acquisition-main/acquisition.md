---
description: In Adobe Mobile Services können Akquise-Links mit eindeutigen Trackingcodes generiert werden. Wenn ein Benutzer eine App aus dem Apple App Store herunterlädt und ausführt, nachdem er auf den generierten Link geklickt hat, sammelt der SDK die Akquise-Daten automatisch und sendet sie an Adobe Mobile Services.
seo-description: In Adobe Mobile Services können Akquise-Links mit eindeutigen Trackingcodes generiert werden. Wenn ein Benutzer eine App aus dem Apple App Store herunterlädt und ausführt, nachdem er auf den generierten Link geklickt hat, sammelt der SDK die Akquise-Daten automatisch und sendet sie an Adobe Mobile Services.
seo-title: App-Akquise
solution: Experience Cloud,Analytics
title: App-Akquise
topic: Developer and implementation
uuid: 5fece619-e4b8-4d06-9250-dcb66fa32ce0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 100%

---


# App-Akquise {#mobile-app-acquisition}

In Adobe Mobile Services können Akquise-Links mit eindeutigen Trackingcodes generiert werden. Wenn ein Benutzer eine App aus dem Apple App Store herunterlädt und ausführt, nachdem er auf den generierten Link geklickt hat, sammelt der SDK die Akquise-Daten automatisch und sendet sie an Adobe Mobile Services.

Um „Akquise“ zu nutzen, ist SDK-Version 4.1 oder höher **erforderlich**.

Akquise-Links müssen in Adobe Mobile Services erstellt werden. Weitere Informationen finden Sie in [Akquise](/help/using/acquisition-main/acquisition-main.md).

Die Informationen in diesem Abschnitt ermöglichen es dem SDK, Akquise-Daten von einem Akquise-Link zu senden.

## App-Akquise verfolgen {#section_CEA30C652AC8470784B8054E299B80FA}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zum Projekt hinzufügen* im Abschnitt [Grundlegende Implementierung und Lebenszyklus](/help/ios/getting-started/dev-qs.md).
1. Importieren Sie die Bibliothek:

   ```objective-c
   #import "ADBMobile.h"
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

   Die Einstellungen für `acquisition` werden von Adobe Mobile Services generiert und sollten nicht geändert werden. Weitere Informationen zum Herunterladen einer angepassten `ADBMobileConfig.json`-Datei mit vorkonfigurierten Einstellungen für `acquisition` finden Sie unter [Vorbereitung](/help/ios/getting-started/requirements.md).

Sobald diese Einstellungen aktiviert wurden, werden die Akquisedaten automatisch beim ersten Aufrufen des Lebenszyklus gesendet, nachdem die App das erste Mal gestartet wurde.

>[!CAUTION]
>
>`referrerTimeout` muss auf einen Wert größer als 0 festgelegt werden, um die App-Akquise zu aktivieren.

## iOS-Apps für universelle Links aktivieren

Wenn Sie universelle Links in Ihrer App verwenden, fügen Sie Ihre Domäne für Adobe-Marketinglinks der Liste der zugeordneten Domänen für Ihre App hinzu.

Fügen Sie Ihre Domäne für Adobe-Marketinglinks der Liste der zugeordneten Domänen für Ihre App in Xcode hinzu:

1. Gehen Sie zu Ihrem Projektziel und klicken Sie auf die Registerkarte **[!UICONTROL Funktionen]**.
2. Scrollen Sie nach unten zum Abschnitt **[!UICONTROL Zugeordnete Domänen]** und aktivieren Sie ihn.
3. Fügen Sie der Liste **[!UICONTROL Domänen]** einen Eintrag für Ihre Domäne für Marketinglinks von Ihrer Marketinglink-URL hinzu.

Ihr Eintrag wird ungefähr so aussehen: `applinks:5848561889a02a6996aea62b.c00.adobe.com`.