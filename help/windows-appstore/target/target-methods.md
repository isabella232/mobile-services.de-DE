---
description: Liste der von der Windows 8.1 Universal App Store-Bibliothek bereitgestellten Target-Methoden.
seo-description: Liste der von der Windows 8.1 Universal App Store-Bibliothek bereitgestellten Target-Methoden.
seo-title: Target-Methoden
solution: Marketing Cloud, Analytics
title: Target-Methoden
topic: Entwickler und Implementierung
uuid: 8c35b31c-c70b-4dba-8759-173342a301e9
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Target-Methoden {#target-methods}

Liste der von der Windows 8.1 Universal App Store-Bibliothek bereitgestellten Target-Methoden.

Das SDK unterstützt zurzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target und Audience Manager. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Analysemethoden ist „Target“ als Präfix vorangestellt.

[Lebenszyklusmetriken](/help/windows-appstore/metrics.md) werden als Parameter jeder mbox-Load gesendet.

>[!TIP]
>
>When you consume `winmd` methods from winJS (JavaScript), all methods automatically have their first letter lowercased.

## Klassenreferenz: TargetLocationRequest

### Eigenschaften

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## String constants

This information helps you set keys for custom parameters.

```
static property Platform::String ^TARGET_PARAMETER_ORDER_ID { 
  Platform::String ^get() { return L"orderId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_ORDER_TOTAL { 
  Platform::String ^get() { return L"orderTotal"; } 
} 
static property Platform::String ^TARGET_PARAMETER_PRODUCT_PURCHASE_ID { 
  Platform::String ^get() { return L"productPurchasedId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_CATEGORY_ID { 
  Platform::String ^get() { return L"categoryId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_3RDPARTY_ID { 
  Platform::String ^get() { return L"mbox3rdPartyId"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PAGE_VALUE { 
  Platform::String ^get() { return L"mboxPageValue"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_PC { 
  Platform::String ^get() { return L"mboxPC"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_SESSION_ID { 
  Platform::String ^get() { return L"mboxSession"; } 
} 
static property Platform::String ^TARGET_PARAMETER_MBOX_HOST { 
  Platform::String ^get() { return L"mboxHost"; } 
}
```

* **LoadRequest (winJS: loadRequest)**

   Sendet `request` an Ihren konfigurierten Target-Server und gibt den Zeichenfolgenwert des in einem Block-`callback` generierten Angebots zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile; 
      ADB.Target.loadRequest(heroBannerRequest).then(function(content) { 
      // do something with content returned from target server 
      });
      ```

* **CreateRequest (winJS: createRequest)**

   Erstellt ein `TargetLocationRequest`-Objekt mit den angegebenen Parametern.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile; 
      var heroBannerRequest = ADB.Target.createRequest("heroBanner", "default.png", null); 
      ```

* **CreateOrder &#x200B; ConfirmRequest (winJS: createOrder &#x200B; ConfirmRequest)**

   Erstellt ein `TargetLocationRequest`-Objekt mit den angegebenen Parametern.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId, Platform::String ^orderTotal, Platform::String ^productPurchasedId, Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object> ^parameters); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile; 
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm", "order", "47.88", "3722", null); 
      ```

* **ClearCookies (winJS: clearCookies)**

   Löscht Target-Cookies für die Anwendung auf dem aktuellen Gerät.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void ClearCookies(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **GetPcId (winJS: getPcId)**

   Gibt das PC-ID-Cookie des aktuellen Geräts zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **GetSessionId (winJS: getSessionId)**

   Gibt das Sitzungs-ID-Cookie des aktuellen Geräts zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```

