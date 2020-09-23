---
description: Liste der von der universellen Windows-Plattformbibliothek bereitgestellten Zielgruppen.
seo-description: Liste der von der universellen Windows-Plattformbibliothek bereitgestellten Zielgruppen.
seo-title: Target-Methoden
solution: Experience Cloud,Analytics
title: Target-Methoden
topic: Developer and implementation
uuid: 2ad5953b-7850-446a-8053-b3715b86329b
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 36%

---


# Target-Methoden {#target-methods}

Liste der von der universellen Windows-Plattformbibliothek bereitgestellten Zielgruppen.

Das SDK unterstützt derzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Zielgruppe und Audience Manager.

[Lebenszyklusmetriken](/help/universal-windows/metrics.md) werden als Parameter an jede mbox-Belastung gesendet.

>[!TIP]
>
>Wenn Sie Methoden aus winJS (JavaScript) verwenden, wird bei allen Methoden automatisch der erste Buchstabe verringert. `winmd`

## Klassenreferenz: TargetLocationRequest

## Eigenschaften

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## String-Konstanten

Anhand dieser Informationen können Sie Schlüssel für benutzerdefinierte Parameter festlegen.

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

   Sends `request` to your configured Target server and returns the string value of the offer generated in a block `callback`.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Windows::Foundation::IAsyncOperation<Platform::String ^> ^LoadRequest(TargetLocationRequest ^request);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var fADB = ADBMobile; 
       ADB.Target.loadRequest(heroBannerRequest).then(function(content){ 
          //do something with content returned from target server 
       });
      ```

* **CreateRequest (winJS: createRequest)**

   Creates a `TargetLocationRequest` object with the given parameters.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static TargetLocationRequest ^CreateRequest(Platform::String ^name, Platform::String ^defaultContent,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      var ADB = ADBMobile;
      var heroBannerRequest = ADB.Target.createRequest("heroBanner","default.png", null); 
      ```

* **CreateOrder &#x200B; ConfirmRequest (winJS: createOrder &#x200B; ConfirmRequest)**

   Creates a `TargetLocationRequest` object with the given parameters.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static TargetLocationRequest ^CreateOrderConfirmRequest(Platform::String ^name, Platform::String ^orderId,Platform::String ^orderTotal,Platform::String ^productPurchasedId,Windows::Foundation::Collections::IMap<Platform::String^,Platform::Object^> ^parameters); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      varADB = ADBMobile;
      var orderConfirm = ADB.Target.createOrderConfirmRequest("orderConfirm","order","47.88","3722",null);
      ```

* **ClearCookies (winJS: clearCookies)**

   Löscht Zielgruppen-Cookies für die Anwendung auf dem aktuellen Gerät.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static void ClearCookies();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      ADBMobile.Target.clearCookies();
      ```

* **GetPcId (winJS: getPcId)**

   Gibt das PC-ID-Cookie für das aktuelle Gerät zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      staticPlatform::String ^GetPcId();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      autopcId = ADBMobile.Target.getPcId();
      ```

* **GetSessionId (winJS: getSessionId)**

   Gibt das Sitzungs-ID-Cookie für das aktuelle Gerät zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      staticPlatform::String ^GetSessionId();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
       autosessionId=ADBMobile.Target.getSessionId(); 
      ```
