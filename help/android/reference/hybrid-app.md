---
description: Wenn Ihre App mobile Webinhalte öffnet, stellen Sie sicher, dass Besucher zwischen App und mobilem Web nicht unterschiedlich identifiziert werden.
seo-description: Wenn Ihre App mobile Webinhalte öffnet, stellen Sie sicher, dass Besucher zwischen App und mobilem Web nicht unterschiedlich identifiziert werden.
seo-title: Visitor Tracking between an app and mobile web
solution: Marketing Cloud,Analytics
title: Visitor Tracking between an app and mobile web
topic: Entwickler und Implementierung
uuid: 073572e4-4c55-4b27-b4a7-e4349ccde7bf
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Visitor tracking between an app and the mobile web {#visitor-tracking-between-an-app-and-mobile-web}

Wenn Ihre App mobile Webinhalte öffnet, stellen Sie sicher, dass Besucher zwischen App und mobilem Web nicht unterschiedlich identifiziert werden.

## Besucher-IDs in Apps

Das Android-SDK generiert eine Unique Visitor-ID, wenn eine App installiert wird. Diese ID wird im persistenten Arbeitsspeicher des Mobilgeräts gespeichert, mit jedem Treffer gesendet und nur entfernt, wenn der Nutzer die App deinstalliert.

>[!TIP]
>
>App-Besucher-IDs werden durch Aktualisierungen beibehalten.

## Besucher-IDs im mobilen Web

Typische Implementierungen des mobilen Webs nutzen dieselben standardmäßigen Analytics-Dateien `s_code.js` oder `AppMeasurement.js`, die auch bei Desktop-Sites verwendet werden. Die JavaScript-Bibliotheken besitzen ihre eigenen Methoden zum Generieren von Unique Visitor-IDs, wodurch eine unterschiedliche Besucher-ID generiert werden muss, wenn Sie mobile Webinhalte über Ihre App öffnen.

## Implementing visitor tracking between an app and the mobile web {#section_1755BCCFD42D456EB2319141030FDDFF}

So verwenden Sie dieselbe Besucher-ID in der App und im mobilen Web:

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK- und Konfigurationsdatei zu Ihrer IntelliJ-IDEA- oder Eclipse-Projekt* in der [Core-Implementierung und im Lebenszyklus](/help/android/getting-started/dev-qs.md)hinzufügen.

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

Der ID-Dienstcode auf der Zieldomäne extrahiert die MID aus der URL, statt bei Adobe eine neue ID anzufordern. Der Code verwendet den übermittelten MID zur Besuchernachverfolgung.

Stellen Sie bei Treffern aus dem mobilen Webinhalt sicher, dass der Parameter `mid` bei jedem Treffer vorhanden ist und mit dem vom App-Code gesendeten `mid`-Parameter übereinstimmt.

## Troubleshooting visitor tracking {#section_9B641F8569E34A089C52AA28EA4C891D}

### I do not see `Visitor.appendToURL`.

Stellen Sie sicher, dass das Adobe-SDK, das im Paket der übergeordneten Anwendung enthalten ist, Version 4.12.0 (oder höher) aufweist.

**Adobe IDs werden nicht in meiner URL angezeigt.**

* Stellen Sie Folgendes sicher:
   * Die URL-Zeichenfolge, die zum Öffnen der Webansicht verwendet wird, wurde von `Visitor.appendToURL(urlString)` ) generiert.
   * Die Adobe IDs sind codiert.
To ensure that the IDs that are appended to the URL that is being opened, verify that the `adobe_mc` query parameter appears in the URL.

### Der `mid`-Wert unterscheidet sich in App- und Webansicht.

* Stellen Sie Folgendes sicher:

   * Die URL-Zeichenfolge, die zum Öffnen der Webansicht verwendet wird, wurde von `Visitor.appendToURL(urlString)` ) generiert.
   * Die URL-Zeichenfolge enthält Adobe-Parameter.

      The string should contain `adobe_mc="SAMPLE_ID_DATA"` where `"SAMPLE_ID_DATA"` contains the IDs that are generated in the Adobe Mobile SDK.
   * `VisitorAPI.js` weist Version 1.7.0 (oder höher) auf.

Wenn Sie das Problem nicht mithilfe dieser Schritte beheben können, wenden Sie sich an den Adobe-Kundenservice.

>[!IMPORTANT]
>
>Damit Adobe die Implementierung validieren kann, müssen Sie eine Beispielanwendung und die zugehörige Site freigeben.

