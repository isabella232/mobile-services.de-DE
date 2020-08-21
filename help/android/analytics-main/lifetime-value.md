---
description: Mit dem Lebenszeitwert können Sie die Zielgruppe und den Lebenszeitwert für jeden Android-Benutzer messen. Der Wert kann zum Speichern von Käufen während der Lebensdauer, Ansichten, Videobeendigungen, Social Sharing, Foto-Uploads usw. verwendet werden.
seo-description: Mit dem Lebenszeitwert können Sie die Zielgruppe und den Lebenszeitwert für jeden Android-Benutzer messen. Der Wert kann zum Speichern von Käufen während der Lebensdauer, Ansichten, Videobeendigungen, Social Sharing, Foto-Uploads usw. verwendet werden.
seo-title: Besucherlebenszeitwert
solution: Marketing Cloud,Analytics
title: Besucherlebenszeitwert
topic: Developer and implementation
uuid: ba0308de-282e-46f9-a14c-19fb6d5c363e
translation-type: tm+mt
source-git-commit: 7ae626be4d71641c6efb127cf5b1d3e18fccb907
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 52%

---


# Besucherlebenszeitwert {#visitor-lifetime-value}

Mit dem Lebenszeitwert können Sie die Zielgruppe und den Lebenszeitwert für jeden Android-Benutzer messen. Der Wert kann zum Speichern von Käufen während der Lebensdauer, Ansichten, Videobeendigungen, Social Sharing, Foto-Uploads usw. verwendet werden.

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

