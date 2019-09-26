---
description: Im Folgenden finden Sie eine Liste der Audience Manager-Methoden, die durch die Android-Bibliothek bereitgestellt werden.
keywords: android;library;mobile;sdk
seo-description: Im Folgenden finden Sie eine Liste der Audience Manager-Methoden, die durch die Android-Bibliothek bereitgestellt werden.
seo-title: Audience Manager-Methoden
solution: Marketing Cloud,Analytics
title: Audience Manager methods
topic: Entwickler und Implementierung
uuid: 2f6e4664-1306-41d4-9fa7-e3a99f1df4ab
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Audience Manager methods{#audience-manager-methods}

Im Folgenden finden Sie eine Liste der Audience Manager-Methoden, die durch die Android-Bibliothek bereitgestellt werden.

Das SDK unterstützt derzeit mehrere Adobe Experience Cloud-Lösungen, darunter Analytics, Target, Audience Manager und den Identitätsdienst für Adobe Experience Platform. Methods are prefixed according to the solution. For example, Experience Cloud ID methods are prefixed with `audience manager`.

Wenn Audience Manager in Ihrer JSON-Datei konfiguriert ist, wird ein Signal mit Lebenszyklusmetriken mit Ihrem Lebenszyklustreffer gesendet.

* **getVisitorProfile**

   Gibt das Besucherprofil zurück, das zuletzt erfasst wurde, und gibt `null` zurück, wenn kein Signal gesendet wurde. Das Besucherprofil wird in `SharedPreferences` gespeichert und steht so bei jedem Start der App zur Verfügung.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static HashMap<String, Object> getVisitorProfile(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      HashMap<String, Object> visitorProfile = AudienceManager.getVisitorProfile(); 
      ```

* **getDpid**

   Gibt die aktuelle DPID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void getDpid(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      String dpid = AudienceManager.getDpid(); 
      ```

* **getDpuuid**

   Gibt die aktuelle DPUUID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void getDpuuid(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      String dpuuid = AudienceManager.getDpuuid(); 
      ```

* **setDpidAndDpuuid**

   Setzt die DPID und DPUUID-Werte, die mit jedem Signal gesendet werden.

   Wenn der an diese Methode übergebene DPUUID-Wert Zeichen enthält, die nicht URL-sicher sind, müssen Kunden den Parameter kodieren, bevor er an das SDK übergeben wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void setDpidAndDpuuid(String dpid, String dpuuid); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      AudienceManager.setDpidAndDpuuid("myDpid", "myDpuuid"); 
      ```

* **signalWithData**

   Sendet dem Zielgruppen-Management ein Signal mit Eigenschaften und ruft die passenden Segmente ab, die in einem Block-Rückruf zurückgegeben werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void signalWithData(Map<String, Object> data, AudienceManagerCallback<Map<String, Object>> callback);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      HashMap Traits = new HashMap<String, Object>();
      aamTraits.put("trait", "b");
      AudienceManager.signalWithData(aamTraits, new AudienceManager.AudienceManagerCallback<Map<String, Object>> () {
        @Override
         public void call(Map<String, Object> item) { 
              // segments come back here normally found in the segs object of your json 
         }
      });
      ```
