---
description: 'Die folgenden Akquise-Methoden werden von der Android-Bibliothek bereitgestellt '
keywords: Android;Bibliothek;Mobile;SDK
seo-description: 'Die folgenden Akquise-Methoden werden von der Android-Bibliothek bereitgestellt '
seo-title: Akquisemethoden
solution: Experience Cloud,Analytics
title: Akquisemethoden
topic-fix: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
exl-id: 0ce1b8fb-fd45-45de-8f97-e297e4c6529f
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '86'
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
