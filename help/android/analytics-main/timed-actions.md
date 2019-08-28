---
description: Zeitgesteuerte Aktionen ermöglichen Ihnen die Messung der in der App verbrachten Zeit sowie der Gesamtzeit zwischen Start und Ende einer Aktion. Das SDK berechnet die Zeit in jeder Sitzung und die Gesamtzeit über alle Sitzungen hinweg, die bis zum Abschluss der Aktion benötigt werden. Sie können zeitgesteuerte Aktionen nutzen, um Segmente zu definieren. So können Sie verschiedene zeitliche Aspekte vergleichen, wie z. B. die Zeit bis zum Tätigen eines Kaufs oder Abschluss eines Levels, den Ablauf des Kaufvorgangs usw.
seo-description: Zeitgesteuerte Aktionen ermöglichen Ihnen die Messung der in der App verbrachten Zeit sowie der Gesamtzeit zwischen Start und Ende einer Aktion. Das SDK berechnet die Zeit in jeder Sitzung und die Gesamtzeit über alle Sitzungen hinweg, die bis zum Abschluss der Aktion benötigt werden. Sie können zeitgesteuerte Aktionen nutzen, um Segmente zu definieren. So können Sie verschiedene zeitliche Aspekte vergleichen, wie z. B. die Zeit bis zum Tätigen eines Kaufs oder Abschluss eines Levels, den Ablauf des Kaufvorgangs usw.
seo-title: Zeitgesteuerte Aktionen
solution: Marketing Cloud, Analytics
title: Zeitgesteuerte Aktionen
topic: Entwickler und Implementierung
uuid: 5 a 48 a 580-b 942-4 e 49-9 f 1 b -078 fea 7 fccdb
translation-type: tm+mt
source-git-commit: 97c0dc17bcc624b38e9eb8023eb1d69d02568d11

---


# Timed actions {#timed-actions}

Zeitgesteuerte Aktionen ermöglichen Ihnen die Messung der in der App verbrachten Zeit sowie der Gesamtzeit zwischen Start und Ende einer Aktion. Das SDK berechnet die Zeit in jeder Sitzung und die Gesamtzeit über alle Sitzungen hinweg, die bis zum Abschluss der Aktion benötigt werden. Sie können zeitgesteuerte Aktionen nutzen, um Segmente zu definieren. So können Sie verschiedene zeitliche Aspekte vergleichen, wie z. B. die Zeit bis zum Tätigen eines Kaufs oder Abschluss eines Levels, den Ablauf des Kaufvorgangs usw.

Die folgenden Metriken werden für zeigesteuerte Aktionen erfasst:

* Gesamtanzahl der Sekunden in der App zwischen Start und Ende (sitzungsübergreifend)
* Gesamtanzahl der Sekunden zwischen Start und Ende (Uhrzeit)

Ein optionaler Rückruf ermöglicht die Durchführung zusätzlicher Aktionen nach Abschluss der zeitgesteuerten Aktion:

* Führen Sie den Code aus und fügen Sie basierend auf den Dauerergebnissen optionale benutzerdefinierte Logiken hinzu.
* Fügen Sie Kontextdaten hinzu, bevor Sie die Dauern übergeben.
* Abbruch-Treffer und -Dauern werden noch nicht gesendet.

## Track timed actions {#section_FF5B1EDC1A5340A5B13BC0F1BF2E13E1}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Config File to your intellij IDEA oder Eclipse Project* in [Core Implementation and lifeycle](/help/android/getting-started/dev-qs.md).
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

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

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

