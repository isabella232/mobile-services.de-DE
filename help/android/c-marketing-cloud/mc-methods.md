---
description: Im Folgenden finden Sie die Methoden des Experience Cloud ID-Dienstes, die von der Android-Bibliothek bereitgestellt werden.
keywords: android;library;mobile;sdk
seo-description: Im Folgenden finden Sie die Methoden des Experience Cloud ID-Dienstes, die von der Android-Bibliothek bereitgestellt werden.
seo-title: Identity-Dienst-Methoden für Adobe Experience Platform
solution: Marketing Cloud,Analytics
title: Identity-Dienst-Methoden für Adobe Experience Platform
topic: Developer and implementation
uuid: c5107a7e-273b-4f71-8738-4c603479b24c
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 100%

---


# Identity-Dienst-Methoden für Adobe Experience Platform {#experience-cloud-id-service-methods}

Im Folgenden finden Sie die Methoden des Experience Cloud ID-Dienstes, die von der Android-Bibliothek bereitgestellt werden.

Das SDK unterstützt zurzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target, Audience Manager und Identity-Dienst für Adobe Experience Platform.

Methoden erhalten je nach Lösung unterschiedliche Präfixe, z. B. `visitor` bei Experience Cloud ID-Methoden. Weitere Informationen finden Sie unter [Experience Cloud ID-Konfiguration](/help/android/c-marketing-cloud/mcvid.md).

* **public static String appendToURL(final String URL)**

   Hängt die Adobe-Besucherdaten an eine URL-Zeichenfolge zur Verwendung mit der Adobe-JavaScript-Bibliothek an. Für diese Methode benötigen Sie SDK 4.12 oder höher. Weitere Informationen finden Sie unter [Hilfefunktion zum Anhängen der Besucher-ID](https://docs.adobe.com/content/help/de-DE/id-service/using/id-service-api/methods/appendvisitorid.html).

   >[!IMPORTANT]
   >
   >Diese Methode kann einen blockierenden Netzwerkaufruf verursachen. Rufen Sie diese Methode nicht in zeitkritischen Threads auf.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static String appendToURL(final String URL) 
      ```

      Eine erforderliche URL-Zeichenfolge, an die die Besucherinformationen angehängt werden.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      String urlSample = "https://example.com";`
              String urlWithAdobeVisitorInfo = Visitor.appendToURL(urlSample);
      
              Intent(Intent.ACTION_VIEW);
              i.setData(Uri.parse(urlWithAdobeVisitorInfo));
              startActivity(i);
      ```

* **getMarketingCloudId**

   Ruft die Experience Cloud ID vom Besucher-ID-Dienst ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static String getMarketingCloudId(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      String = Visitor.getMarketingCloudId();
      ```

      >[!IMPORTANT]
      >
      >Diese Methode kann zu einem blockierenden Netzwerkaufruf führen und sollte **NICHT** über einen UI-Thread aufgerufen werden.

* **syncIdentifiers**

   Mit der Experience Cloud-ID können Sie zusätzliche Kunden-IDs festlegen, die jedem Besucher zugeordnet werden können. Die Besucher-API akzeptiert mehrere Kunden-IDs für denselben Besucher sowie eine Kundentypkennung, die den Umfang der einzelnen Kunden-IDs abgrenzt. Diese Methode entspricht `setCustomerIDs` in der JavaScript-Bibliothek.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void syncIdentifiers(Map<String, String> identifiers); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Map<String,String> identifiers = new HashMap<String, String>();
      identifiers.put("idType", "idValue");
      Visitor.syncIdentifiers(identifiers);
      ```

* **syncIdentifier**

   Synchronisiert den bereitgestellten ID-Typ und -Wert mit dem Besucher-ID-Dienst.

   Übergeben Sie `authenticationState` als einen der folgenden Werte:

   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void syncIdentifier(final String identifierType, final String identifier, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Visitor.syncIdentifier("myIdType", "valueForUser", VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT);
      ```

* **syncIdentifiers**

   Synchronisiert die bereitgestellten IDs mit dem ID-Service.

   Übergeben Sie `authenticationState` als einen der folgenden Werte:
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED`
   * `VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT`

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void syncIdentifiers(final Map<String String> identifiers, final VisitorID.VisitorIDAuthenticationState authenticationState);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Map<String, String> identifiers = new HashMap<String, String>();
          identifiers.put("myIdType", "valueForUser"); Visitor.syncIdentifiers(identifiers,
      VisitorID.VisitorIDAuthenticationState.VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED); 
      ```

* **getIdentifiers**

   Ruft eine Liste schreibgeschützter `ADBVisitorID`-Objekte ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static List<VisitorID> getIdentifiers(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      List<VisitorID> myVisitorIDs = Visitor.getIdentifiers(); 
      ```

* **getUrlVariablesAsync**

   Diese in Version 4.16.0 eingeführte Methode gibt eine entsprechend geformte Zeichenfolge zurück, die URL-Variablen des Besucher-ID-Dienst enthält. Weitere Informationen zur Verwendung dieser Methode finden Sie unter [Identity-Dienst-Methoden für Adobe Experience Platform](/help/android/reference/hybrid-app.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void getUrlVariablesAsync(final VisitorCallback callback);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      final String urlString = https://www.mydomain.com/index.php; 
      Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
        @Override 
        public void call(String urlVariables) { 
            final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
            ...
        } 
      });
      ```

## Öffentliche Methoden {#section_8AC744B431A3438C9B45629CA3EA0F51}

```java
public class VisitorID { 
    public final String idOrigin; 
    public final String idType; 
    public final String id; 
    public VisitorIDAuthenticationState authenticationState; 
 
    public enum VisitorIDAuthenticationState { 
         VISITOR_ID_AUTHENTICATION_STATE_UNKNOWN(0), 
         VISITOR_ID_AUTHENTICATION_STATE_AUTHENTICATED(1), 
         VISITOR_ID_AUTHENTICATION_STATE_LOGGED_OUT(2); 
    } 
}
```
