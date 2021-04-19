---
description: Zeitgesteuerte Aktionen ermöglichen Ihnen die Messung der in der App verbrachten Zeit sowie der Gesamtzeit zwischen Start und Ende einer Aktion. Das SDK berechnet die Zeit in der Sitzung und die Gesamtzeit (sitzungsübergreifend) berechnen, die zum Abschluss der Aktion erforderlich ist. Sie können zeitgesteuerte Aktionen nutzen, um Segmente zu definieren. So können Sie verschiedene zeitliche Aspekte vergleichen, wie z. B. die Zeit bis zum Tätigen eines Kaufs oder Abschluss eines Levels, den Ablauf des Kaufvorgangs usw.
seo-description: Zeitgesteuerte Aktionen ermöglichen Ihnen die Messung der in der App verbrachten Zeit sowie der Gesamtzeit zwischen Start und Ende einer Aktion. Das SDK berechnet die Zeit in der Sitzung und die Gesamtzeit (sitzungsübergreifend) berechnen, die zum Abschluss der Aktion erforderlich ist. Sie können zeitgesteuerte Aktionen nutzen, um Segmente zu definieren. So können Sie verschiedene zeitliche Aspekte vergleichen, wie z. B. die Zeit bis zum Tätigen eines Kaufs oder Abschluss eines Levels, den Ablauf des Kaufvorgangs usw.
seo-title: Zeitgesteuerte Aktionen
solution: Experience Cloud,Analytics
title: Zeitgesteuerte Aktionen
topic-fix: Developer and implementation
uuid: 5a48a580-b942-4e49-9f1b-078fea7fccdb
exl-id: d9851440-6e65-4d89-a6b3-81c8abd2bf06
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 100%

---

# Zeitgesteuerte Aktionen {#timed-actions}

Zeitgesteuerte Aktionen ermöglichen Ihnen die Messung der in der App verbrachten Zeit sowie der Gesamtzeit zwischen Start und Ende einer Aktion. Das SDK berechnet die Zeit in der Sitzung und die Gesamtzeit (sitzungsübergreifend) berechnen, die zum Abschluss der Aktion erforderlich ist. Sie können zeitgesteuerte Aktionen nutzen, um Segmente zu definieren. So können Sie verschiedene zeitliche Aspekte vergleichen, wie z. B. die Zeit bis zum Tätigen eines Kaufs oder Abschluss eines Levels, den Ablauf des Kaufvorgangs usw.

Die folgenden Metriken werden für zeitgesteuerte Aktionen gemeldet:

* Gesamtanzahl der Sekunden in der App zwischen Start und Ende (sitzungsübergreifend)
* Gesamtanzahl der Sekunden zwischen Start und Ende (Uhrzeit)

Bei einem optionalen Callback können Sie zusätzliche Aktionen ausführen, wenn die zeitgesteuerte Aktion abgeschlossen ist:

* Code ausführen und eine Logik hinzufügen – optionale benutzerdefinierte Logik basierend auf den Ergebnissen der Dauer.
* Kontextdaten vor der Übergabe von Dauern hinzufügen.
* Treffer und noch nicht gesendete Dauern abbrechen.

## Zeitgesteuerte Aktionen verfolgen {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zu Ihrem IntelliJ IDEA- oder Eclipse-Projekt hinzufügen* in [Grundlegende Implementierung und Lebenszyklus](/help/android/getting-started/dev-qs.md).
1. Importieren Sie die Bibliothek:

   ```java
   import com.adobe.mobile.*;
   ```

1. Rufen Sie `trackTimedActionStart` auf und geben Sie einen Namen sowie optional Kontextdaten für die zeitgesteuerte Aktion an.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("ExperienceName", experience); 
   Analytics.trackTimedActionStart("TimeUntilPurchase", cdata);
   ```

1. (Optional) Sie können jederzeit `trackTimedActionUpdate` mit dem Namen der zeitgesteuerten Aktion aufrufen, um zusätzliche Kontextdaten hinzuzufügen.

   ```java
   HashMap cdata = new HashMap<String, Object>(); 
   cdata.put("myapp.ImageLiked", imageName); 
   Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
   ```

1. Rufen Sie `trackTimedActionEnd` auf und geben Sie den Namen der zeitgesteuerten Aktion und `TimedActionBlock` (Callback) weiter, wenn das Ereignis abgeschlossen wird. Dadurch werden alle Daten nachgeschlagen und die Zeitdauer berechnet.

   ```java
   Analytics.trackTimedActionEnd("TimeUntilPurchase", cdata);
   ```

   Zeitgesteuerte Ereignismetriken werden in Variablen für die mobile Lösung gespeichert, um automatisches Reporting zu ermöglichen.

## Zusätzliche Daten senden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Zusätzlich zu dem Namen der zeitgesteuerten Aktion können Sie mit den Aufrufen zum Aktionsstart bzw. zur -änderung auch zusätzliche Kontextdaten senden:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata);
```

Die Kontextdatenwerte müssen benutzerdefinierten Variablen in Adobe Mobile Services zugeordnet werden:

![](assets/map-variable-context-ltv.png)

## Beispiele {#section_7BA344B8BD4F48DCBAE27AC9320CBCEA}

```java
// Timed Action Start Example 
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("ExperienceName", experience); 
Analytics.trackTimedActionStart("TimeUntilPurchase", cdata); 
 
// Timed Action Update Example 
cdata = new HashMap<String, Object>(); 
cdata.put("ImageLiked", imageName); 
Analytics.trackTimed​ActionUpdate("TimeUntilPurchase", cdata); 
 
// Timed Action End Example 
Analytics.trackTimedActionEnd("TimeUntilPurchase", null); 
 
// Timed Action End Example with Callback 
Analytics.trackTimedActionEnd("TimeUntilPurchase", new Analytics.TimedActionBlock<Boolean>() { 
 @Override 
 public Boolean call(long inAppDuration, long totalDuration, Map<String, Object> contextData) { 
  contextData.put("PurchaseItem", "Item453"); 
  return true; // return true to send the hit, false to cancel 
 } 
});
```
