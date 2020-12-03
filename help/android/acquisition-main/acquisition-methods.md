---
description: 'Die folgenden Akquisemethoden werden von der Android-Bibliothek bereitgestellt '
keywords: android;library;mobile;sdk
seo-description: 'Die folgenden Akquisemethoden werden von der Android-Bibliothek bereitgestellt '
seo-title: Akquisemethoden
solution: Experience Cloud,Analytics
title: Akquisemethoden
topic: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 100%

---


# Akquisemethoden {#acquisition-methods}

Die folgende Akquisemethode wird von der Android-Bibliothek bereitgestellt:

* **campaignStartForApp**

   Ermöglicht es Entwicklern, eine App-Akquisekampagne so zu starten, als hätte der Benutzer einen Link aufgerufen. Dies ist hilfreich, wenn Sie manuell Akquiselinks erstellen oder die App Store-Umleitung selbst verarbeiten möchten.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void campaignStartForApp(final String appId final Map<String Object> data); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Acquisition.campaignStartForApp("0652024f-adcd-49f9-9bd7-2552a4564d2f" new 
      HashMap<String Object (){{
           put("custom.key" "value");
      }}); 
      ```
