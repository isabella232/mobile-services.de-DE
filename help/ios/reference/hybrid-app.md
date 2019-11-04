---
description: Wenn Ihre App mobile Webinhalte öffnet, müssen Sie sicherstellen, dass die Besucher nicht getrennt identifiziert werden, wenn sie zwischen dem nativen und mobilen Web wechseln.
seo-description: Wenn Ihre App mobile Webinhalte öffnet, müssen Sie sicherstellen, dass die Besucher nicht getrennt identifiziert werden, wenn sie zwischen dem nativen und mobilen Web wechseln.
seo-title: Besucherverfolgung zwischen einer App und dem mobilen Internet
solution: Experience Cloud,Analytics
title: Besucherverfolgung zwischen einer App und dem mobilen Internet
topic: Entwickler und Implementierung
uuid: 2d951de6-3954-4379-a4ff-99b9695b9869
translation-type: ht
source-git-commit: 9257d6b6c2c14d0422cda65fcc9c677ac5ac47a9

---


# Besucher zwischen einer App und dem mobilen Internet verfolgen {#visitor-tracking-between-an-app-and-mobile-web}

Wenn Ihre App mobile Webinhalte öffnet, müssen Sie sicherstellen, dass die Besucher nicht getrennt identifiziert werden, wenn sie zwischen dem nativen und mobilen Web wechseln.

## Besucher-IDs in Apps

Das iOS-SDK generiert eine Unique Visitor-ID, wenn eine App installiert wird. Diese ID wird im persistenten Speicher auf dem Mobilgerät gespeichert und bei jedem Treffer gesendet. Diese ID wird nur entfernt, wenn der Benutzer die App deinstalliert.

>[!TIP]
>
>App-Besucher-IDs bleiben auch bei Upgrades bestehen.

## Besucher-IDs im mobilen Web

Typische Implementierungen des mobilen Webs nutzen dieselben standardmäßigen Analytics-Dateien `s_code.js` oder `AppMeasurement.js`, die auch bei Desktop-Sites verwendet werden. Die JavaScript-Bibliotheken besitzen ihre eigenen Methoden zum Generieren von Unique Visitor-IDs, wodurch eine unterschiedliche Besucher-ID generiert werden muss, wenn Sie mobile Webinhalte über Ihre App öffnen.

Verwenden derselben Besucher-ID in der App und im mobilen Web und Übergeben der App-Besucher-ID in der URL an das mobile Web:

## Besucherverfolgung zwischen einer App und dem mobilen Internet implementieren {#section_EDC91D6C67AD43999227707C2769C65D}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zum Projekt hinzufügen* im Abschnitt [Grundlegende Implementierung und Lebenszyklus](/help/ios/getting-started/dev-qs.md).
1. Um Besucherinformationen an die URL anzuhängen, die zum Öffnen der Webansicht verwendet wird, rufen Sie `visitorAppendToURL` auf:

   ```objective-c
   NSURL *url = [NSURL URLWithString:@”https://www.mydomain.com/index.php"]; 
   NSURL *urlWithVisitorData = [ADBMobile visitorAppendToURL:url]; 
   [[UIApplication sharedApplication] openURL:urlWithVisitorData];
   ```

   Alternativ können Sie ab der SDK-Version 4.16.0 `visitorGetUrlVariablesAsync:` aufrufen und Ihre eigene URL generieren:

   ```objective-c
   NSString *urlString = @"https://www.mydomain.com/index.php"; 
   [ADBMobile visitorGetUrlVariablesAsync:^(NSString * _Nullable urlVariables) { 
       NSString *urlStringWithVisitorData = [NSString stringWithFormat:@"%@?%@", urlString, urlVariables]; 
       NSURL *urlWithVisitorData = [NSURL URLWithString:urlStringWithVisitorData]; 
       [[UIApplication sharedApplication] openURL:urlWithVisitorData options:@{} completionHandler:^(BOOL success) { 
           // handle openURL success 
       }]; 
   }];
   ```

Der ID-Dienstcode auf der Zieldomäne extrahiert die MID aus der URL, statt bei Adobe eine neue ID anzufordern. Der ID-Dienstcode auf der Zielseite verwendet die übergebene MID zum Nachverfolgen des Besuchers.

Überprüfen Sie für Treffer aus dem mobilen Webinhalt, ob der Parameter `mid` bei jedem Treffer vorhanden ist und ob dieser Wert mit dem Parameter `mid` übereinstimmt, der durch den App-Code gesendet wird.

## Fehlerbehebung bei der Besucherverfolgung {#section_C070AE85E3CE4E9893FD4F40E73F2C92}

### Ich kann `[ADBMobile visitorAppendToURL:]` nicht finden.

Stellen Sie sicher, dass das Adobe-SDK, das im Paket der übergeordneten Anwendung enthalten ist, Version 4.12.0 (oder höher) aufweist.

### Adobe IDs werden nicht in meiner URL angezeigt.

Stellen Sie Folgendes sicher:

* Die URL-Zeichenfolge, die zum Öffnen der Webansicht verwendet wird, wurde von `[ADBMobile visitorAppendToURL:]` generiert.

* Die Adobe IDs sind codiert.

   Suchen Sie nach dem Abfrageparameter `adobe_mc`, um zu überprüfen, ob die IDs an die URL angefügt sind, die geöffnet wird.

### Der Parameter „mid“ in meiner App ist nicht mit dem in meiner Webansicht identisch.*

Stellen Sie Folgendes sicher:

* Die URL-Zeichenfolge, die zum Öffnen der Webansicht verwendet wird, wurde von `[ADBMobile visitorAppendToURL:]` generiert.

   Die URL-Zeichenfolge enthält Adobe-Parameter.

   Die Zeichenfolge sollte `adobe_mc="SAMPLE_ID_DATA"` enthalten, wobei `"SAMPLE_ID_DATA"` die IDs enthält, die im Adobe Mobile SDK generiert werden.

* `VisitorAPI.js` weist Version 1.7.0 (oder höher) auf.

Wenn diese Problembehandlungsschritte Ihre Probleme nicht beheben, sollten Sie sich an den Kundendienst von Adobe wenden. Bereiten Sie sich darauf vor, eine Beispielanwendung und deren verknüpfte Website freizugeben, damit Adobe die Implementierung validieren kann.
