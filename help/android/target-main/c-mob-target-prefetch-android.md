---
description: Die Vorabruffunktion von Adobe Target verwendet Android Mobile-SDK, um so wenig wie möglich Angebotsinhalt abzurufen, indem die Serverantworten im Cache abgelegt werden.
title: Vorabruf für Android-Angebotsinhalte
uuid: 063451b8-e191-4d58-8ed8-1723e310ad1a
exl-id: 60fd9703-972b-4c2c-bf9c-86e1f59bfba5
source-git-commit: 5d44c09a18a557e934628533c4eefaa9e26aba42
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 92%

---

# Vorabruf für Android-Angebotsinhalte {#prefetch-offer-content-in-android}

Die Vorabruffunktion von Adobe Target verwendet Android Mobile-SDK, um so wenig wie möglich Angebotsinhalt abzurufen, indem die Serverantworten im Cache abgelegt werden.

Dadurch wird die Ladezeit verkürzt, es werden mehrere Netzwerkaufrufe verhindert und Adobe Target kann darüber informiert werden, welche Mbox vom Benutzer der mobilen App besucht wurde. Alle Inhalte werden während des Vorabrufs abgerufen und zwischengespeichert. Dieser Inhalt wird für alle zukünftigen Aufrufe abgerufen, die zwischengespeicherten Inhalt für den angegebenen Mbox-Namen enthalten.

Vorabgerufene Inhalte werden nicht über Starts hinweg behalten. Der vorabgerufene Inhalt verbleibt im Cache, bis die Lebensdauer der App endet oder die Methode `clearPrefetchCache()` aufgerufen wird.

>[!IMPORTANT]
>
>Vorabruf-APIs für Target gibt es bereits seit SDK-Version 4.14.0. Weitere Informationen zu den Parameterbeschränkungen finden Sie unter [Batch-Eingabeparameter](https://developers.adobetarget.com/api/#batch-input-parameters).

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

## Vorabrufmethoden {#section_05967F1F3A554B0FBC2C08A954554BDE}

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

   * Hier finden Sie die Parameter für diese Methode:

      * **targetPrefetchArray**

         Array von `TargetPrefetchObjects`, das den Namen und mboxParameters für jeden Target-Speicherort enthält, der vorab abgerufen werden soll.

      * **profileParameters**

         Enthält die Schlüssel und Werte von Profilparametern, die mit jedem Standortvorabruf in dieser Anfrage verwendet werden sollen.

      * **callback**

         Wird aufgerufen, wenn der Vorabruf abgeschlossen ist. Gibt den Wert `true` aus, wenn der Vorabruf erfolgreich war, und den Wert `false`, wenn der Vorabruf nicht erfolgreich war.

* **loadRequests**

   Führt eine Stapelanfrage über mehrere mbox-Orte aus, die im Anfrage-Array enthalten sind.  Jedes Objekt im Array enthält eine Callback-Funktion, die aufgerufen wird, wenn für den angegebenen mbox-Speicherort Inhalt verfügbar ist.

   >[!IMPORTANT]
   >
   >Wenn der Inhalt für die angefragten Speicherorte bereits zwischengespeichert ist, wird er sofort im bereitgestellten Rückruf zurückgegeben. Andernfalls sendet das SDK eine Netzwerkanfrage an die Target-Server, um den Inhalt abzurufen.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void loadRequests( final List<TargetRequestObject> requestArray,  final Map<String, Object> profileParameters)
      ```

   * Hier finden Sie die Parameter für diese Methode:

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

## Öffentliche Klassen {#section_A273E53F069E4327BBC8CE4910B37888}

Dies sind die öffentlichen Klassen, die den Vorabruf in Android unterstützen:

### Class reference: TargetPrefetchObject

Umfasst mbox-Namen sowie die Parameter, die für den mbox-Vorabruf verwendet werden.

* **`name`**

   Name des Speicherortes, der vorabgerufen wird.
   * **Typ**: Zeichenfolge

* `mboxParameters`

   Sammlung von Schlüssel-Wert-Paaren, die als `mboxParameters` für diese Anfrage von `TargetPrefetchObject` angehängt werden.
   * **Typ**: Karte`<String, Object>`

* **`orderParameters`**

   Sammlung von Schlüssel-Wert-Paaren, die an die aktuelle mbox unter dem Bestell-Knoten angehängt werden.
   * **Typ**: Karte `<String, Object>`

* **`productParameters`**

   Sammlung von Schlüssel-Wert-Paaren, die an die aktuelle mbox unter dem Produkt-Knoten angehängt werden.

   * **Typ**: Karte `<String, Object>`


### Class reference: TargetRequestObject

Diese Klasse kapselt den mbox-Namen, den Standardinhalt, die mbox-Parameter und den Rückruf ein, die für die Target-Standortanfragen verwendet werden.

* **`mboxName`**

   Name des angefragten Standorts.

   * **Typ**: Zeichenfolge

* **`mboxParameters`**

   Sammlung von Schlüssel-Wert-Paaren, die als `mboxParameters` für dieses `TargetRequestObject` angehängt werden.

   * **Typ: Karte`<String, Object>`**

* **`orderParameters`**

   Sammlung von Schlüssel-Wert-Paaren, die an die aktuelle mbox unter dem Bestell-Knoten angehängt werden.

   * **Typ**: Karte `<String, Object>`

* **`productParameters`**

   Sammlung von Schlüssel-Wert-Paaren, die an die aktuelle mbox unter dem Produkt-Knoten angehängt werden.

   * **Typ**: Karte `<String, Object>`

* **`defaultContent`**

   Zeichenfolgenwert, der im Rückruf zurückgegeben wird, wenn das SDK Inhalte von Target-Servern nicht abrufen kann.

   * **Typ**: Zeichenfolge

* **`callback`**

   Funktionszeiger, der aufgerufen wird, wenn Inhalt für das angegebene `TargetRequestObject` verfügbar ist.

   * **Typ**: Target.TargetCallback`<String>`


## Codebeispiel {#section_BF7F49763D254371B4656E17953D520C}

Im Folgenden finden Sie ein Beispiel für den Vorabruf von Inhalten mithilfe der Android-SDK:

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
