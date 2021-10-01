---
description: 'Die folgenden Akquisemethoden werden von der iOS-Bibliothek bereitgestellt '
solution: Experience Cloud,Analytics
title: Akquisemethoden
uuid: 6f88de57-793d-4d33-9a54-f6714289fd2c
exl-id: dd2721ae-b9a6-48b9-bc92-8e12ee551929
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 100%

---

# Akquisemethoden  {#acquisition-methods}

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
