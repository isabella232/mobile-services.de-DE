---
description: Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Props und andere Variablen für die Berichterstellung zu kopieren.
solution: Experience Cloud,Analytics
title: Verarbeitungsregeln und Kontextdaten
topic-fix: Developer and implementation
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
exl-id: 543201fd-8118-485f-8235-26ec8f9bbb11
source-git-commit: d1ebb2bbc4742f5288f90a90e977d252f3f30aa3
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 72%

---

# Verarbeitungsregeln und Kontextdaten  {#processing-rules-and-context-data}

Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Props und andere Variablen für die Berichterstellung zu kopieren. Weitere Informationen finden Sie unter [Regeln](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Berücksichtigen Sie beim Umgang mit Verarbeitungsregeln folgende Informationen:

* Gruppieren Sie Ihre Kontextdatenvariablen mithilfe von Namespaces, da Sie damit eine logische Reihenfolge beibehalten können. Wenn Sie beispielsweise Informationen zu einem Produkt erfassen möchten, können Sie die folgenden Variablen definieren:

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* Kontextdatenvariablen werden in der Benutzeroberfläche der Verarbeitungsregeln alphabetisch sortiert, sodass Sie schnell sehen können, welche Variablen sich im selben Namespace befinden.

   Vermeiden Sie die Benennung von Kontextdatenschlüsseln mithilfe der eVar- oder Prop-Nummer:

   ```js
   "eVar1":"jimbo"
   ```

   Dies könnte die einmalige Zuordnung in Verarbeitungsregeln *etwas* vereinfachen. Sie verlieren aber Lesbarkeit während des Debuggens und bei zukünftigen Code-Updates, wodurch diese erschwert werden können. Stattdessen empfehlen wir dringend, beschreibende Namen für Schlüssel und Werte zu verwenden:

   ```js
   "username":"jimbo"
   ```

* Kontextvariablen, die Zählerereignisse definieren, sollten auf 1 gesetzt werden:

   ```js
   "logon":"1"
   ```

* Kontextdatenvariablen, die Inkrementiererereignisse definieren, können das Ereignis als Schlüssel und den Inkrementierungswert als Wert haben:

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe behält sich den Namespace `"a."` vor. Um Probleme zu vermeiden, müssen Kontextdatenvariablen in Ihrem Anmeldeunternehmen eindeutig sein.
