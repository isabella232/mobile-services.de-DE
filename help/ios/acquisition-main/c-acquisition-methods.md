---
description: 'Die folgenden Akquisemethoden werden von der iOS-Bibliothek bereitgestellt '
seo-description: 'Die folgenden Akquisemethoden werden von der iOS-Bibliothek bereitgestellt '
seo-title: Akquisemethoden
solution: Experience Cloud,Analytics
title: Akquisemethoden
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Akquisemethoden {#acquisition-methods}

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


