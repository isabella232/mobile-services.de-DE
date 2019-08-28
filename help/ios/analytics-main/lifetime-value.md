---
description: Mit dem Lebenszeitwert können Sie für jeden Benutzer einen Lebenszeitwert messen und vorgeben.
seo-description: Mit dem Lebenszeitwert können Sie für jeden Benutzer einen Lebenszeitwert messen und vorgeben.
seo-title: Besucherlebenszeitwert
solution: Marketing Cloud, Analytics
title: Besucherlebenszeitwert
topic: Entwickler und Implementierung
uuid: d 830 d 18 b -4313-43 bb -8 d 75-3789869 d 0 f 1 d
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Visitor lifetime value {#visitor-lifetime-value}

Mit dem Lebenszeitwert können Sie für jeden Benutzer einen Lebenszeitwert messen und vorgeben.

Sobald Sie einen Wert mit `trackLifetimeValueIncrease` senden, wird der Wert zum vorhandenen Wert hinzugefügt. Der Lebenszeitwert wird auf dem Gerät gespeichert und kann jederzeit mithilfe von `lifetimeValue` abgerufen werden. Dies kann verwendet werden, um Lebenszeiteinkäufe, Banneranzeigen, abgeschlossene Videos, Informationen zur Freigabe in sozialen Netzwerken, Fotouploads usw. zu speichern.

## Track the visitor lifetime value {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden *Sie unter SDK und Config File to your Project* in [Core Implementation and Lifecycle](/help/ios/getting-started/dev-qs.md).
1. Importieren Sie die Bibliothek:

   ```objective-c
   import com.adobe.mobile.*;
   ```

1. Rufen Sie `trackLifetimeValueIncrease` mit der Zahl auf, um die der Wert erhöht werden soll:

   ```objective-c
   [ADBMobile trackLifetimeValueIncrease:increaseAmount data:nil];
   ```

## Send additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Zusätzlich zum Lebenszeitwert können Sie bei jedem Verfolgungsaktionsaufruf zusätzliche Kontextdaten senden:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:imageName forKey:@"myapp.ImageLiked"]; 
[ADBMobile trackLifetimeValueIncrease:increaseAmount data:contextData];
```

Kontextdatenwerte müssen benutzerdefinierte Variablen zugeordnet werden:

![](assets/map-variable-context-ltv.png)

