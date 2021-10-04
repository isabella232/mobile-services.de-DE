---
description: Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Props und andere Variablen für die Berichterstellung zu kopieren.
solution: Experience Cloud,Analytics
title: Verarbeitungsregeln und Kontextdaten
topic-fix: Developer and implementation
uuid: 51338ccd-fa52-4d9c-97c4-947a4100465d
exl-id: a3968160-42c4-4671-b541-c14639b8a451
source-git-commit: 1fa6111d6bf1c2d36f15d2f037718646a035435a
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 67%

---

# Verarbeitungsregeln und Kontextdaten {#processing-rules-and-context-data}

Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Props und andere Variablen für die Berichterstellung zu kopieren.

Weitere Informationen zu Verarbeitungsregeln finden Sie unter [Übersicht über Verarbeitungsregeln](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) in der Adobe Analytics-Dokumentation.

Berücksichtigen Sie beim Umgang mit Verarbeitungsregeln folgende Informationen:

* Gruppieren Sie Ihre Kontextdatenvariablen mithilfe von Namespaces, da Sie damit eine logische Reihenfolge beibehalten können.

   Wenn Sie beispielsweise Informationen zu einem Produkt erfassen möchten, können Sie die folgenden Variablen definieren:

   ```js
   "product.type":"hat";
   "product.team":"mariners";
   "product.color":"blue";
   ```

* Kontextdatenvariablen werden in der Benutzeroberfläche der Verarbeitungsregeln alphabetisch sortiert, sodass Sie schnell sehen können, welche Variablen sich im selben Namespace befinden.

   Vermeiden Sie die Benennung von Kontextdatenschlüsseln mithilfe der eVar- oder Prop-Nummer:

   ```js
   "eVar1":"jimbo";
   ```

   Dies könnte die einmalige Zuordnung in Verarbeitungsregeln *etwas* vereinfachen. Sie verlieren aber Lesbarkeit während des Debuggens und bei zukünftigen Code-Updates, wodurch diese erschwert werden können. Verwenden Sie stattdessen aussagekräftige Namen für Schlüssel und Werte:

   ```js
   "username":"jimbo";
   ```

* Kontextvariablen, die Zählerereignisse definieren, sollten auf 1 gesetzt werden:

   ```js
   "logon":"1";
   ```

* Kontextdatenvariablen, die Inkrementiererereignisse definieren, können das Ereignis als Schlüssel und den Inkrementierungswert als Wert haben:

   ```js
   "levels completed":"6";
   ```

>[!TIP]
>
>Adobe behält sich den Namespace „`a.`“ vor. Abgesehen von dieser Einschränkung, die dazu dient, Konflikte zu vermeiden, besteht die einzige Anforderung darin, dass die Kontextdatenvariablen in Ihrem Anmeldeunternehmen eindeutig sein müssen.
