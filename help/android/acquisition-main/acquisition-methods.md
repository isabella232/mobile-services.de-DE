---
description: 'Die folgenden Akquise-Methoden werden von der Android-Bibliothek bereitgestellt '
keywords: android;library;mobile;sdk
seo-description: 'Die folgenden Akquise-Methoden werden von der Android-Bibliothek bereitgestellt '
seo-title: Akquisemethoden
solution: Marketing Cloud, Analytics
title: Akquisemethoden
topic: Entwickler und Implementierung
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Acquisition methods{#acquisition-methods}

Die folgende Akquise-Methode wird von der Android-Bibliothek bereitgestellt:

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
