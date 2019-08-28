---
description: Die Vorabruffunktion von Adobe Target verwendet Android Mobile SDKs, um so wenig wie möglich Angebotsinhalt abzurufen, indem die Serverantworten im Cache abgelegt werden.
seo-description: Die Vorabruffunktion von Adobe Target verwendet Android Mobile SDKs, um so wenig wie möglich Angebotsinhalt abzurufen, indem die Serverantworten im Cache abgelegt werden.
seo-title: Vorabruf für Android-Angebotsinhalte
title: Vorabruf für Android-Angebotsinhalte
uuid: 063451 b 8-e 191-4 d 58-8 ed 8-1723 e 310 ad 1 a
translation-type: tm+mt
source-git-commit: fa7375ac8a1345d81748bcf635791c46d3943fed

---


# Vorabruf für Android-Angebotsinhalte {#prefetch-offer-content-in-android}

Die Vorabruffunktion von Adobe Target verwendet Android Mobile-SDKs, um so wenig wie möglich Angebotsinhalt abzurufen, indem die Serverantworten im Cache abgelegt werden.

>[!IMPORTANT]
>
>Prefetch-Funktionen in mobilen sdks für Android werden für die Aktivitätstypen Automatisches Targeting, Automatisierte Zuordnung und automatisierte Personalisierung in Adobe Target nicht unterstützt.

Dieser Vorgang reduziert die Ladezeit, vermeidet mehrfache Netzwerk-Aufrufe und ermöglicht es Adobe Target, eine Benachrichtigung darüber zu erhalten, welche mbox vom Benutzer der mobilen App besucht wurde. Der gesamte Inhalt wird abgerufen und während des Aufrufs für den Vorabruf im Cache abgelegt, und dieser Inhalt wird bei allen zukünftigen Aufrufen abgerufen, die im Cache abgelegte Inhalte für den spezifizierten mbox-Namen enthalten.

Vorabgerufene Inhalte werden nicht über Starts hinweg behalten. The prefetch content is cached as long as the application lives or until the `clearPrefetchCache()` method is called.

>[!IMPORTANT]
>
>Target prefetch APIs have been available since SDK version 4.14.0. For more information about parameter limitations, see [Batch-input-parameters](https://developers.adobetarget.com/api/#batch-input-parameters).

In der SDK-Version 4.14 oder später wird, sofern spezifiziert, `environmentId``ADBMobileConfig.json` beim Initiieren eines v2 Batch-MBox-TnT-Anrufs aus der Datei „“ gewonnen. Wenn keine `environmentId` in der Datei angegeben ist, wird kein Umgebungsparameter in den TNT-Batch-MBox-Aufruf gesendet und das Angebot für die Standardumgebung wird geliefert.

Beispiel:

```java
if (MobileConfig.getInstance().mobileUsingTarget()){ 
            long environmentID = MobileConfig.getInstance().getEnvironmentID(); 
            if(environmentID != 0L){ 
                parametersJson.put(TargetJson.ENVIRONMENT_ID, environmentID); 
            } 
        }
```

## Pre-fetch methods {#section_05967F1F3A554B0FBC2C08A954554BDE}

Folgende Methoden können Sie in Android für den Vorabruf verwenden:

* **prefetchContent**

   Sendet eine Vorabruf-Anfrage mit einem Array von Speicherorten an den konfigurierten Target-Server und gibt den Anfragestatus im bereitgestellten Rückruf zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void prefetchContent(
      final List<TargetPrefetchObject> targetPrefetchArray,
      final Map<String, Object> profileParameters,
      final TargetCallback<Boolean> callback)
      ```

   * Hier sind die Parameter für diese Methode:

      * **targetPrefetchArray**

         Array von `TargetPrefetchObjects`, das den Namen und mboxParameters für jeden Target-Speicherort enthält, der vorab abgerufen werden soll.

      * **profileParameters**

         Enthält die Schlüssel und Werte von Profilparametern, die mit jedem Standortvorabruf in dieser Anfrage verwendet werden sollen.

      * **callback**

         Wird aufgerufen, wenn der Vorabruf abgeschlossen ist. Returns `true` if the prefetch was successful and `false` if the prefetch was unsuccesful.

* **loadRequests**

   Führt eine Stapelanfrage über mehrere mbox-Orte aus, die im Anfrage-Array enthalten sind.  Jedes Objekt im Array enthält eine Callback-Funktion, die aufgerufen wird, wenn für den angegebenen mbox-Speicherort Inhalt verfügbar ist.

   >[!IMPORTANT]
   >
   >Wenn der Inhalt für die angeforderten Standorte bereits zwischengespeichert ist, wird er sofort im angegebenen Rückruf zurückgegeben. Andernfalls sendet das SDK eine Netzwerkanfrage an die Target-Server, um den Inhalt abzurufen.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void loadRequests( final List<TargetRequestObject> requestArray,  final Map<String, Object> profileParameters)
      ```

   * Hier sind die Parameter für diese Methode:

      * **requestArray**

         Array von `TargetRequestObjects`, das den Namen, den Standardinhalt, die Parameter und die Rückruffunktion für jeden abzurufenden Standort enthält.

      * **profileParameters**

         Enthält Schlüssel und Werte von Profilparametern, die mit jedem Standortvorabruf in dieser Anfrage verwendet werden.

* **clearPrefetchCache**

   Löscht die Daten, die vom Target-Vorabruf zwischengespeichert wurden.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void clearPrefetchCache();
      ```

   * Für diese Methode gibt es keine Parameter.

* **createTargetRequestObject**

   Erstellt mit den bereitgestellten Daten eine `TargetRequestObject`-Instanz und gibt diese zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static TargetPrefetchObject createTargetRequestObject( 
      final String mboxName,
      final String defaultContent, 
      final Map<String, Object> mboxParams, 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams, 
      final Target.TargetCallback<String> callback)
      ```

* **createTargetPrefetchObject**

   Erstellt und gibt eine Instanz von TargetPrefetchObject mit den bereitgestellten Daten zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static TargetPrefetchObject createTargetPrefetchObject( 
      final String mboxName, 
      final Map<String, Object> mboxParams) 
      final Map<String, Object> orderParams, 
      final Map<String, Object> productParams)
      ```

## Public classes {#section_A273E53F069E4327BBC8CE4910B37888}

Dies sind die öffentlichen Klassen, die den Vorabruf in Android unterstützen:

### Klassenverweis: Targetprefetchobject

Umfasst mbox-Namen sowie die Parameter, die für den mbox-Vorabruf verwendet werden.

* **`name`**

   Name des Speicherortes, der vorabgerufen wird.
   * **Typ**: String

* `mboxParameters`

   Sammlung von Schlüssel-Wert-Paaren, die als `mboxParameters` für diese Anfrage von `TargetPrefetchObject` angehängt werden.
   * **Typ**: Map`<String, Object>`

* **`orderParameters`**

   Sammlung von Schlüssel-Wert-Paaren, die an die aktuelle mbox unter dem Bestell-Knoten angehängt werden.
   * **Typ**: Map `<String, Object>`

* **`productParameters`**

   Sammlung von Schlüssel-Wert-Paaren, die an die aktuelle mbox unter dem Produkt-Knoten angehängt werden.

   * **Typ**: Map `<String, Object>`


### Klassenverweis: Targetrequestobject

Diese Klasse kapselt den mbox-Namen, den Standardinhalt, die mbox-Parameter und den Rückruf ein, die für die Target-Standortanfragen verwendet werden.

* **`mboxName`**

   Name des angefragten Standorts.

   * **Typ**: String

* **`mboxParameters`**

   Sammlung von Schlüssel-Wert-Paaren, die als `mboxParameters` für dieses `TargetRequestObject` angehängt werden.

   * **Typ: Map`<String, Object>`**

* **`orderParameters`**

   Sammlung von Schlüssel-Wert-Paaren, die an die aktuelle mbox unter dem Bestell-Knoten angehängt werden.

   * **Typ**: Map `<String, Object>`

* **`productParameters`**

   Sammlung von Schlüssel-Wert-Paaren, die an die aktuelle mbox unter dem Produkt-Knoten angehängt werden.

   * **Typ**: Map `<String, Object>`

* **`defaultContent`**

   Zeichenfolgenwert, der im Rückruf zurückgegeben wird, wenn das SDK Inhalte von Target-Servern nicht abrufen kann.

   * **Typ**: String

* **`callback`**

   Funktionszeiger, der aufgerufen wird, wenn Inhalt für das angegebene `TargetRequestObject` verfügbar ist.

   * **Typ**: Target. targetcallback`<String>`


## Code sample {#section_BF7F49763D254371B4656E17953D520C}

Im Folgenden finden Sie ein Beispiel für den Vorabruf von Inhalten mithilfe der Android-SDKs:

```java
// When your app launches, prefetch the content for a list of locations. 
// Define the list of mboxes that you want to prefetch. 
List<TargetPrefetchObject> prefetchMboxesList = new ArrayList<>(); 
  
Map<String, Object> mboxParameters1 = new HashMap<>(); 
mboxParameters1.put("status", "platinum"); 
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName1", mboxParameters1));

Map<String, Object> mboxParameters2 = new HashMap<>(); 
mboxParameters2.put("userType", "paid"); 
 
List<String> purchasedIds = new ArrayList<String>(); 
purchasedIds.add("34"); 
purchasedIds.add("125");  
Map<String, Object> orderParameters2 = new HashMap<>(); 
orderParameters2.put("id", "ADCKKIM"); 
orderParameters2.put("total", "344.30"); 
orderParameters2.put("purchasedProductIds",  purchasedIds); 
  
Map<String, Object> productParameters2 = new HashMap<>(); 
productParameters2.put("id", "24D3412"); 
productParameters2.put("categoryId","Books"); 
  
prefetchMboxesList.add(Target.createTargetPrefetchObject("mboxName2", mboxParameters2, orderParameters2, productParameters2));

// Define the profile parameters map. 
Map<String, Object> profileParameters = new HashMap<>(); 
profileParameters.put("ageGroup", "20-32");

// Define the target callback for the prefetch call status. 
Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() { 
    @Override 
    public void call(final Boolean status) { 
        // check the returned status for the prefetch call 
    }};

// Call the prefetchContent API. 
Target.prefetchContent(prefetchMboxesList, profileParameters, prefetchStatusCallback);

// When the content is required, you can initiate the locations request. 
// Define the list of target request objects. 
List<TargetRequestObject> locationRequests = new ArrayList<>(); 
  
Target.TargetCallback<String> callback1 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName1. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName1", "defaultContent1", mboxParameters1, callback1));

Target.TargetCallback<String> callback2 = new Target.TargetCallback<String>() { 
    @Override 
    public void call(final String content) { 
        // check the returned content for mboxName2. 
    }}; 
  
locationRequests.add(Target.createTargetRequestObject("mboxName2", "defaultContent2", mboxParameters2, orderParameters2, productParameters2, callback2)); 
  
// Call the loadRequests API. 
Target.loadRequests(locationRequests, profileParameters); 
```

## Weitere Informationen {#section_A454BAD1CD49423E86C71BAEE06125FD}

Im Folgenden einige zusätzliche Informationen zu diesen Beispielen:

* `ProductParameters` erlaubt nur die folgenden Schlüssel:

   * `id`
   * `categoryId`

* `OrderParameters` erlaubt nur die folgenden Schlüssel:

   * `id`
   * `total`
   * `purchasedProductIds`

* `purchasedProducts` akzeptiert eine ArrayList mit Zeichenfolgen.
