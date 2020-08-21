---
description: Im Folgenden finden Sie die Liste der Adobe Target-Methoden, die durch die Android-Bibliothek bereitgestellt werden.
keywords: android;library;mobile;sdk
seo-description: Im Folgenden finden Sie die Liste der Adobe Target-Methoden, die durch die Android-Bibliothek bereitgestellt werden.
seo-title: Target-Methoden für Android
solution: Marketing Cloud,Analytics
title: Target-Methoden für Android
topic: Developer and implementation
uuid: 8e9808b2-ba80-4646-ba05-8e62d4fde065
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 100%

---


# Target-Methoden für Android{#target-methods}

Im Folgenden finden Sie die Liste der Adobe Target-Methoden, die durch die Android-Bibliothek bereitgestellt werden.

Das SDK unterstützt zurzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target, Audience Manager und Identity-Dienst für Adobe Experience Platform. Methoden erhalten je nach Lösung unterschiedliche Präfixe, z. B. `target` bei Experience Cloud ID-Methoden.

>[!TIP]
>
>[Lebenszyklusmetriken](/help/android/metrics.md) werden als Parameter jeder mbox-Load gesendet.

## Class reference: TargetLocationRequest {#section_A8CC898922164E819EC730DC92A6742B}

**Eigenschaften:**

```java
public String name; 
public String defaultContent; 
public HashMap<String, Object> parameters;
```

**Zeichenfolgenkonstanten**

>[!TIP]
>
>Die folgenden Konstanten helfen Ihnen beim Festlegen von Schlüsseln für benutzerdefinierte Parameter.

```java
public static final String TARGET_PARAMETER_ORDER_ID   = "orderId"; 
public static final String TARGET_PARAMETER_ORDER_TOTAL         = "orderTotal"; 
public static final String TARGET_PARAMETER_PRODUCT_PURCHASE_ID = "productPurchasedId"; 
public static final String TARGET_PARAMETER_CATEGORY_ID         = "categoryId"; 
public static final String TARGET_PARAMETER_MBOX_3RDPARTY_ID    = "mbox3rdPartyId"; 
public static final String TARGET_PARAMETER_MBOX_PAGE_VALUE     = "mboxPageValue"; 
public static final String TARGET_PARAMETER_MBOX_PC             = "mboxPC"; // pcId in cookie 
public static final String TARGET_PARAMETER_MBOX_SESSION_ID     = "mboxSession"; // sessionId in cookie 
public static final String TARGET_PARAMETER_MBOX_HOST           = "mboxHost";
```

>[!IMPORTANT]
>
>* Wenn Sie SDK **vor** Version 4.14.0 verwenden, finden Sie die Parameterbeschränkungen unter [https://developers.adobetarget.com/api/#input-parameters](https://developers.adobetarget.com/api/#input-parameters).
   >
   >
* Wenn Sie SDK der Version 4.14.0 **oder höher** verwenden, finden Sie die Parameterbeschränkungen unter [https://developers.adobetarget.com/api/#batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters).


* **loadRequest**

   Sendet eine Anfrage an den konfigurierten Target-Server und gibt die Zeichenfolge des generierten Angebots in einem Block-Rückruf zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void loadRequest(TargetLocationRequest request, TargetCallback<String> callback);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Target.loadRequest(heroBannerRequest, new Target.TargetCallback<String>() {  @Override  public void call(String item) {   // do something with item  } });
      ```

* **loadRequest**

   Sendet eine Anfrage an den konfigurierten Target-Server und gibt die Zeichenfolge des generierten Angebots in einem Block-Rückruf zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void loadRequest(final String name final String defaultContent, final Map `<String, Object>` profileParameters, 
                                     final Map `<String, Object>` orderParameters,final Map `<String Object>` mboxParameters, final TargetCallback<String> callback)
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”);
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); 
      mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters
      new TargetCallback<String>() {
          @Override
          public void call (String item) {
             Log.d(“Target Content”, item); 
          }
      });
      ```

* **loadRequest**

   Sendet eine Anfrage an den konfigurierten Target-Server und gibt die Zeichenfolge des generierten Angebots in einem TargetCallback zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void loadRequest(final String name, final String defaultContent, final Map<String, Object> profileParameters, final Map<String, Object> orderParameters, final Map<String, Object> mboxParameters, final Map<String, Object> requestLocationParameters, final TargetCallback<String> callback);
      ```

   * **Gibt Folgendes zurück:** N/A

   * **Parameter:**

      Hier finden Sie die Parameter für diese Methode:

      * **name**

         Name der/des Target-mbox/-Standorts, die/den Sie empfangen wollen.

         * **Typ:** Zeichenfolge
      * **defaultContent**

         Wert, der im Rückruf zurückgegeben wird, wenn der Target-Server nicht erreichbar ist oder der Benutzer nicht für die Kampagne infrage kommt.

         * **Typ:** Zeichenfolge
      * **profileParameters**

         Werte in diesem Wörterbuch werden in das Objekt „profileParameters“ in der Anforderung zu Target versetzt.

         * **Typ:** Karte `<String, Object>`
      * **orderParameters**

         Werte in diesem Wörterbuch werden in das Objekt „order“ in der Anforderung zu Target versetzt.

         * **Typ:** Karte `<String, Object>`
      * **mboxParameters**

         Werte in diesem Wörterbuch werden in die Anfrage an Target aufgenommen.

         * **Typ:** Karte `<String, Object>`
      * **requestLocationParameters**

         Werte in diesem Wörterbuch werden in das Objekt „requestLocation“ in der Anforderung zu Target versetzt.

         * **Typ:** Karte `<String, Object>`
      * **callback**

         Diese Methode wird mit dem Inhalt des Angebots vom Target-Server aufgerufen. Wenn der Target-Server nicht erreichbar ist oder der Nutzer nicht für die Kampagne infrage kommt, wird defaultContent zurückgegeben.

         * **Typ:** TargetCallback `<String>`
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Map `<String, Object>` profileParameters = new HashMap `<String, Object>`(); profileParameters.put(“profile-parameter-key”, “profile-parameter-value”); 
      Map `<String, Object>` orderParameters = new HashMap `<String, Object>`(); orderParameters.put(“order-parameter-key”, “order-parameter-value”); 
      Map `<String, Object>` mboxParameters = new HashMap `<String, Object>`(); mboxParameters.put(“mbox-parameter-key”, “mbox-parameter-value”); 
      Map `<String, Object>` requestLocationParameters = new HashMap `<String, Object>`(); requestLocationParameters.put(“request-location-parameter-key”, “request-location-parameter-value”); 
      
      Target.loadRequest(“mboxName”, “defaultContent”, profileParameters, orderParameters, mboxParameters, requestLocationParameters,new TargetCallback<String>() {
         @Override
         public void call (String item) { 
            Log.d(“Target Content”, item);
         } 
      });
      ```

      Weitere Informationen zu der zugrunde liegenden Target-API finden Sie unter [Bereitstellung](https://docs.adobe.com/dev/products/target/reference/delivery.html) in der Target-Entwicklerhilfe.








* **createOrder&#x200B;ConfirmRequest**

   Erstellt ein TargetLocationRequest-Objekt mit den angegebenen Parametern.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static TargetLocationRequest createOrderConfirmRequest(String name, String orderId, String orderTotal, String productPurchasedId, Map<String, Object> parameters);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      TargetLocationRequest orderConfirm = Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null);
      ```

* **createRequest**

   Erstellt ein TargetLocationRequest-Objekt mit den angegebenen Parametern.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static TargetLocationRequest createRequest(String name, String defaultContent, Map<String, Object> parameters);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      TargetLocationRequest heroBannerRequest = Target.createRequest("heroBanner", "default.png", null);
      ```

* **clearCookies**

   Löscht alle Ziel-Cookies aus der App.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void clearCookies();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Target.clearCookies();
      ```

* **getPcID**

   Gibt die pcID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static String getPcID();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Target.getPcID();
      ```

* **getSessionID**

   Gibt die Sitzungs-ID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static String getSessionID();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Target.getSessionID();
      ```

* **setThirdPartyID**

   Legt die Drittanbieter-ID fest.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static String setThirdPartyID(final String thirdPartyId);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Target.setThirdPartyID(“third-party-id”);
      ```

* **getThirdPartyID**

   Gibt die Drittanbieter-ID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static String getThirdPartyID();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      String thirdPartyId = Target.getThirdPartyID();
      ```
