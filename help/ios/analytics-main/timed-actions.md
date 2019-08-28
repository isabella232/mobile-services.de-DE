---
description: Zeitgesteuerte Aktionen ermöglichen Ihnen die Messung der in der App verbrachten Zeit sowie der Gesamtzeit zwischen Start und Ende einer Aktion. Das SDK berechnet die Dauer in jeder Sitzung und die sitzungsübergreifende Gesamtzeit, die zum Abschluss einer Aktion benötigt wird. Sie können zeitgesteuerte Aktionen nutzen, um Segmente zu definieren. So können Sie verschiedene zeitliche Aspekte vergleichen, wie z. B. die Zeit bis zum Tätigen eines Kaufs oder Abschluss eines Levels, den Ablauf des Kaufvorgangs usw.
seo-description: Zeitgesteuerte Aktionen ermöglichen Ihnen die Messung der in der App verbrachten Zeit sowie der Gesamtzeit zwischen Start und Ende einer Aktion. Das SDK berechnet die Dauer in jeder Sitzung und die sitzungsübergreifende Gesamtzeit, die zum Abschluss einer Aktion benötigt wird. Sie können zeitgesteuerte Aktionen nutzen, um Segmente zu definieren. So können Sie verschiedene zeitliche Aspekte vergleichen, wie z. B. die Zeit bis zum Tätigen eines Kaufs oder Abschluss eines Levels, den Ablauf des Kaufvorgangs usw.
seo-title: Zeitgesteuerte Aktionen
solution: Marketing Cloud, Analytics
title: Zeitgesteuerte Aktionen
topic: Entwickler und Implementierung
uuid: dbcbac 5 a -6345-49 f 6-b 050-0 db 05292 f 005
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Timed actions {#timed-actions}

Zeitgesteuerte Aktionen ermöglichen Ihnen die Messung der in der App verbrachten Zeit sowie der Gesamtzeit zwischen Start und Ende einer Aktion. Das SDK berechnet die Dauer in jeder Sitzung und die sitzungsübergreifende Gesamtzeit, die zum Abschluss einer Aktion benötigt wird. Sie können zeitgesteuerte Aktionen nutzen, um Segmente zu definieren. So können Sie verschiedene zeitliche Aspekte vergleichen, wie z. B. die Zeit bis zum Tätigen eines Kaufs oder Abschluss eines Levels, den Ablauf des Kaufvorgangs usw.

Die folgenden Metriken werden für zeitgesteuerte Aktionen gemeldet:

* Sitzungsübergreifende Gesamtdauer in Sekunden in der App zwischen dem Start und Ende
* Gesamtdauer in Sekunden zwischen dem Start und Ende (Ist-Zeit)

Ein optionaler Rückruf ermöglicht die Durchführung zusätzlicher Aktionen nach Abschluss der zeitgesteuerten Aktion:

* Ausführen von Code und Hinzufügen von Logik – optional benutzerdefinierte Logik anhand der Zeitdauer.
* Hinzufügen von Kontext vor dem Weitergeben der Zeitdauer.
* Abbrechen von Treffern und der Zeitdauer, die bisher nicht gesendet wurden.

## Tracking timed actions {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden *Sie unter SDK und Config File to your Project* in [Core Implementation and Lifecycle](/help/ios/getting-started/dev-qs.md).
1. Importieren Sie die Bibliothek:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Rufen Sie `trackTimedActionStart` auf und geben Sie einen Namen sowie optional Kontextdaten für die zeitgesteuerte Aktion an.

   ```objective-c
   [ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                               data:@{@"ExperienceName" : experience}];
   ```

1. (Optional) Wenn Sie weitere Kontextdaten hinzufügen möchten, können Sie `trackTimedActionUpdate` mit dem zeitlich beschränkten Aktionsnamen aufrufen.

   ```objective-c
   [ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                                data:@{@"myapp.ImageLiked" : imageName}];
   ```

1. Rufen Sie `trackTimedActionEnd` auf und geben Sie den Namen der zeitgesteuerten Aktion und `TimedActionBlock` (Callback) weiter, wenn das Ereignis abgeschlossen wird. Dadurch werden alle Daten nachgeschlagen und die Zeitdauer berechnet.

   Zeitgesteuerte Ereignismetriken werden in Variablen für die mobile Lösung gespeichert, um automatisches Reporting zu ermöglichen.

   ```objective-c
   [ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                            logic:nil];
   ```

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Zusätzlich zum zeitgesteuerten Aktionsnamen können Sie weitere Kontextdaten mit den Aufrufen zum Starten und Aktualisieren der Aktion senden:

```objective-c
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"myapp.ImageLiked" : imageName}];
```

Kontextdatenwerte müssen benutzerdefinierte Variablen zugeordnet werden:

![](assets/map-variable-context-ltv.png)

## Beispiel {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```objective-c
// Timed Action Start Example 
[ADBMobile trackTimedActionStart:@"TimeUntilPurchase"  
                            data:@{@"ExperienceName" : experience}];

// Timed Action Update Example 
[ADBMobile trackTimedActionUpdate:@"TimeUntilPurchase"  
                             data:@{@"ImageLiked" : imageName}];

// Timed Action End Example 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:nil]; 
 
// Timed Action End Example with Callback 
[ADBMobile trackTimedActionEnd:@"TimeUntilPurchase"  
                         logic:^BOOL(NSTimeInterval inAppDuration,  
                                     NSTimeInterval totalDuration,  
                                     NSMutableDictionary *data) { 
                                        [data setObject:@"PurchaseItem" forKey:@"Item453"]; 
                                        return YES; //return YES to send the hit, NO to cancel 
                                     }];
```

