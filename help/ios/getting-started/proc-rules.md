---
description: Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Eigenschaften und andere Variablen für Berichte zu kopieren.
seo-description: Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Eigenschaften und andere Variablen für Berichte zu kopieren.
seo-title: Verarbeitungsregeln und Kontextdaten
solution: Experience Cloud,Analytics
title: Verarbeitungsregeln und Kontextdaten
topic: Developer and implementation
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 51%

---


# Verarbeitungsregeln und Kontextdaten{#processing-rules-and-context-data}

Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Eigenschaften und andere Variablen für Berichte zu kopieren.

Weitere Informationen finden Sie unter folgenden Themen:

* [Schulung](https://tv.adobe.com/embed/1181/16506/) zu Verarbeitungsregeln anlässlich des Gipfeltreffens 2013
* Autorisierung zur Verwendung der Verarbeitungsregeln erhalten

   Weitere Informationen zu Verarbeitungsregeln finden Sie unter Übersicht über [Verarbeitungsregeln](https://docs.adobe.com/content/help/de-DE/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Berücksichtigen Sie beim Umgang mit Verarbeitungsregeln folgende Informationen:

* Gruppieren Sie Ihre Kontextdatenvariablen mithilfe von Namensräumen, da Sie damit eine logische Reihenfolge beibehalten können.

   Wenn Sie beispielsweise Informationen zu einem Produkt erfassen möchten, können Sie die folgenden Variablen definieren:

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* Kontextdatenvariablen werden in der Benutzeroberfläche der Verarbeitungsregeln alphabetisch sortiert, sodass Sie schnell sehen können, welche Variablen sich im selben Namensraum befinden.

   Vermeiden Sie die Benennung von Kontextdatenschlüsseln mithilfe der evar- oder prop-Nummer:

   ```js
   "eVar1":"jimbo"
   ```

   Dies kann bei der einmaligen Zuordnung in Verarbeitungsregeln *etwas* einfacher sein, Sie verlieren jedoch die Lesbarkeit beim Debugging und bei zukünftigen Codeaktualisierungen, was schwieriger sein kann. Verwenden Sie stattdessen aussagekräftige Namen für Schlüssel und Werte:

   ```js
   "username":"jimbo"
   ```

* Kontextvariablen, die Zähler-Ereignis definieren, sollten auf 1 eingestellt werden:

   ```js
   "logon":"1"
   ```

* Kontextdatenvariablen, die Inkrementor-Ereignis definieren, können das Ereignis als Schlüssel und den Inkrementierungswert als Wert haben:

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe behält sich den Namespace „`a.`“ vor. Abgesehen von dieser Einschränkung, die dazu dient, Konflikte zu vermeiden, besteht die einzige Anforderung darin, dass die Kontextdatenvariablen in Ihrem Anmeldeunternehmen eindeutig sein müssen.

