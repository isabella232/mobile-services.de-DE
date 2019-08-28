---
description: 'Die folgenden Akquisemethoden werden von der iOS-Bibliothek bereitgestellt '
seo-description: 'Die folgenden Akquisemethoden werden von der iOS-Bibliothek bereitgestellt '
seo-title: Akquisemethoden
solution: Marketing Cloud, Analytics
title: Akquisemethoden
uuid: 6 f 88 de 77-793 d -4 d 33-9 a 54-f 6714289 fd 2 c
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Acquisition methods {#acquisition-methods}

Die folgenden Akquisemethoden werden von der iOS-Bibliothek bereitgestellt:

Die folgende Methode wird unterstützt:

* **acquisitionCampaignStartForApp:data:**

   Ermöglicht es Entwicklern, eine App-Akquisekampagne so zu starten, als hätte der Benutzer einen Link aufgerufen. Dies ist hilfreich beim Erstellen von manuellen Akquise-Links und beim manuellen Verarbeiten der Umleitung zum App-Store, beispielsweise mit einer `SKStoreView`.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      + (void)acquisitionCampaignStartForApp:(NSString *) appId data:(NSDictionary *)data; 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      [ADBMobile acquisitionCampaignStartForApp:@"0652024f-adcd-49f9-9bd7-2552a4564d2f" data:@{@"custom.key":@"value"}]; 
      ```


