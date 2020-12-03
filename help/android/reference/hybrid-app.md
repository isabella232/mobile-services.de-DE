---
description: Wenn Ihre App mobile Webinhalte öffnet, stellen Sie sicher, dass Besucher zwischen App und mobilem Web nicht unterschiedlich identifiziert werden.
seo-description: Wenn Ihre App mobile Webinhalte öffnet, stellen Sie sicher, dass Besucher zwischen App und mobilem Web nicht unterschiedlich identifiziert werden.
seo-title: Besucher zwischen einer App und dem mobilen Internet verfolgen
solution: Experience Cloud,Analytics
title: Besucher zwischen einer App und dem mobilen Internet verfolgen
topic: Developer and implementation
uuid: 073572e4-4c55-4b27-b4a7-e4349ccde7bf
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 100%

---


# Besucher zwischen einer App und dem mobilen Internet verfolgen {#visitor-tracking-between-an-app-and-mobile-web}

Wenn Ihre App mobile Webinhalte öffnet, stellen Sie sicher, dass Besucher zwischen App und mobilem Web nicht unterschiedlich identifiziert werden.

## Besucher-IDs in Apps

Das Android SDK generiert eine Unique Visitor-ID, wenn eine App installiert wird. Diese ID wird im persistenten Speicher des Mobilgeräts gespeichert, bei jedem Treffer gesendet und nur entfernt, wenn der Benutzer die App deinstalliert.

>[!TIP]
>
>App-Besucher-IDs bleiben auch bei Upgrades bestehen.

## Besucher-IDs im mobilen Web

Typische Implementierungen des mobilen Webs nutzen dieselben standardmäßigen Analytics-Dateien `s_code.js` oder `AppMeasurement.js`, die auch bei Desktop-Sites verwendet werden. Die JavaScript-Bibliotheken besitzen ihre eigenen Methoden zum Generieren von Unique Visitor-IDs, wodurch eine unterschiedliche Besucher-ID generiert werden muss, wenn Sie mobile Webinhalte über Ihre App öffnen.

## Besucherverfolgung zwischen einer App und dem mobilen Internet implementieren {#section_1755BCCFD42D456EB2319141030FDDFF}

So verwenden Sie dieselbe Besucher-ID in der App und im mobilen Web:

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zu Ihrem IntelliJ IDEA- oder Eclipse-Projekt hinzufügen* in [Grundlegende Implementierung und Lebenszyklus](/help/android/getting-started/dev-qs.md).

1. Um Besucherinformationen an die URL anzuhängen, die zum Öffnen der Webansicht verwendet wird, rufen Sie `visitorAppendToURL` auf:

   ```java
   String urlString = "https://www.mydomain.com/index.php"; 
   String urlStringWithVisitorData = Visitor.appendToURL(urlString); 
   Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
   startActivity(browserIntent);
   ```

   Alternativ können Sie ab der SDK-Version 4.16.0 `Visitor.getUrlVariablesAsync` aufrufen und Ihre eigene URL generieren:

   ```java
   final String urlString = "https://www.mydomain.com/index.php"; 
   Visitor.getUrlVariablesAsync(new Visitor.VisitorCallback(){ 
       @Override 
       public void call(String urlVariables) { 
           final String urlStringWithVisitorData = String.format("%s?%s", urlString, urlVariables); 
           final Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(urlStringWithVisitorData)); 
           startActivity(browserIntent); 
       } 
   });
   ```

Der ID-Service-Code auf der Ziel-Domäne extrahiert die MID aus der URL, statt bei Adobe eine neue ID anzufordern. Der Code verwendet die übergebene MID zum Tracking des Besuchers.

Stellen Sie bei Treffern aus dem mobilen Webinhalt sicher, dass der Parameter `mid` bei jedem Treffer vorhanden ist und mit dem vom App-Code gesendeten `mid`-Parameter übereinstimmt.

## Fehlerbehebung bei der Besucherverfolgung {#section_9B641F8569E34A089C52AA28EA4C891D}

### Ich kann `Visitor.appendToURL` nicht finden.

Stellen Sie sicher, dass das Adobe-SDK, das im Paket der übergeordneten Anwendung enthalten ist, Version 4.12.0 (oder höher) aufweist.

**Adobe IDs werden nicht in meiner URL angezeigt.**

* Stellen Sie Folgendes sicher:
   * Die URL-Zeichenfolge, die zum Öffnen der Webansicht verwendet wird, wurde von `Visitor.appendToURL(urlString)` generiert.
   * Die Adobe IDs sind codiert. 
Achten Sie darauf, dass der Abfrageparameter `adobe_mc` in der URL angezeigt wird, um sicherzustellen, dass die IDs an die geöffnete URL angehängt werden.

### Der `mid`-Wert unterscheidet sich in App- und Webansicht.

* Stellen Sie Folgendes sicher:

   * Die URL-Zeichenfolge, die zum Öffnen der Webansicht verwendet wird, wurde von `Visitor.appendToURL(urlString)` generiert.
   * Die URL-Zeichenfolge enthält Adobe-Parameter.

      Die Zeichenfolge sollte `adobe_mc="SAMPLE_ID_DATA"` enthalten, wobei `"SAMPLE_ID_DATA"` die IDs enthält, die im Adobe Mobile SDK generiert werden.
   * `VisitorAPI.js` weist Version 1.7.0 (oder höher) auf.

Wenn Sie das Problem nicht mithilfe dieser Schritte beheben können, wenden Sie sich an den Adobe-Kundenservice.

>[!IMPORTANT]
>
>Damit Adobe die Implementierung überprüfen kann, sind eine Beispiel-App und die zugehörige Site erforderlich.

