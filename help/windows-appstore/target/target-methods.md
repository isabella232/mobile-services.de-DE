---
description: Liste der Target-Methoden, die von der Windows 8.1 Universal App Store-Bibliothek bereitgestellt werden.
solution: Experience Cloud Services,Analytics
title: Target-Methoden
topic-fix: Developer and implementation
uuid: 8c35b31c-c70b-4dba-8759-173342a301e9
exl-id: 2db9f594-01e7-4ca8-a90e-9d12278350d0
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 43%

---

# Target-Methoden {#target-methods}

Liste der Target-Methoden, die von der Windows 8.1 Universal App Store-Bibliothek bereitgestellt werden.

Das SDK unterstützt derzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target und Audience Manager. Methoden erhalten je nach Lösung unterschiedliche Präfixe. Analytics-Methoden wird das Präfix &quot;Target&quot;vorangestellt.

[Lebenszyklusmetriken](/help/windows-appstore/metrics.md) werden als Parameter jeder mbox-Load gesendet.

>[!TIP]
>
>Wann Sie konsumieren `winmd` -Methoden aus winJS (JavaScript), haben alle Methoden automatisch ihren ersten Buchstaben in Kleinbuchstaben.

## Class reference: TargetLocationRequest

### Eigenschaften

```
property Platform::String ^name; 
property Platform::String ^defaultContent; 
property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^> ^parameters;
```

## Zeichenfolgenkonstanten

Diese Informationen helfen Ihnen beim Festlegen von Schlüsseln für benutzerdefinierte Parameter.

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

   Sendungen `request` auf Ihren konfigurierten Target-Server verweist und den Zeichenfolgenwert des in einem Block generierten Angebots zurückgibt. `callback`.

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

   Erstellt eine `TargetLocationRequest` -Objekt mit den angegebenen Parametern.

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

   Erstellt eine `TargetLocationRequest` -Objekt mit den angegebenen Parametern.

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

   Gibt das PC-ID-Cookie für das aktuelle Gerät zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Platform::String ^GetPcId();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      auto pcId = ADBMobile.Target.getPcId(); 
      ```

* **GetSessionId (winJS: getSessionId)**

   Gibt das Sitzungs-ID-Cookie für das aktuelle Gerät zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```csharp
      static Platform::String ^GetSessionId(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```js
      auto sessionId = ADBMobile.Target.getSessionId(); 
      ```
