---
description: Mit dem Lebenszeitwert können Sie für jeden Android-Benutzer einen Lebenszeitwert messen und vorgeben. Dieser Wert kann verwendet werden, um Lebenszeiteinkäufe, Banner-Anzeigen, abgeschlossene Videos, Informationen zur Freigabe in sozialen Netzwerken, Foto-Uploads usw. zu speichern.
solution: Experience Cloud Services,Analytics
title: Besucherlebenszeitwert
topic-fix: Developer and implementation
uuid: ba0308de-282e-46f9-a14c-19fb6d5c363e
exl-id: 93c6d711-c7c0-4fca-93b2-6a6fc19377bd
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 100%

---

# Besucherlebenszeitwert {#visitor-lifetime-value}

Mit dem Lebenszeitwert können Sie für jeden Android-Benutzer einen Lebenszeitwert messen und vorgeben. Dieser Wert kann verwendet werden, um Lebenszeiteinkäufe, Banner-Anzeigen, abgeschlossene Videos, Informationen zur Freigabe in sozialen Netzwerken, Foto-Uploads usw. zu speichern.

Sobald Sie einen Wert mit `trackLifetimeValueIncrease` senden, wird der Wert zum vorhandenen Wert hinzugefügt. Der Lebenszeitwert wird auf dem Gerät gespeichert und kann jederzeit mithilfe von `lifetimeValue` abgerufen werden.

## Besucherlebenszeitwert verfolgen {#section_390943A49AF841F2941E65D6DF2B3F5A}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zu Ihrem IntelliJ IDEA- oder Eclipse-Projekt hinzufügen* in [Grundlegende Implementierung und Lebenszyklus](/help/android/getting-started/dev-qs.md).
1. Importieren Sie die Bibliothek:

   ```java
   import com.adobe.mobile.*;
   ```

1. Rufen Sie `trackLifetimeValueIncrease` mit der Zahl auf, um die der Wert erhöht werden soll:

   ```java
   Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), null);
   ```

## Zusätzliche Daten senden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Zusätzlich zum Lebenszeitwert können Sie mit jedem trackAction-Aufruf auch zusätzliche Kontextdaten senden:

```java
HashMap cdata = new HashMap<String, Object>(); 
cdata.put("myapp.ImageLiked", imageName); 
Analytics.trackLifetimeValueIncrease(BigDecimal.valueOf(5.0), cdata);
```

Die Kontextdatenwerte müssen benutzerdefinierten Variablen in Adobe Mobile Services zugeordnet werden:

![](assets/map-variable-context-ltv.png)
