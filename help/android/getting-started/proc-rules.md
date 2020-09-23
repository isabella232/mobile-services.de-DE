---
description: Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Eigenschaften und andere Variablen für Berichte zu kopieren.
seo-description: Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Eigenschaften und andere Variablen für Berichte zu kopieren.
seo-title: Verarbeitungsregeln und Kontextdaten
solution: Experience Cloud,Analytics
title: Verarbeitungsregeln und Kontextdaten
topic: Developer and implementation
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 48%

---


# Verarbeitungsregeln und Kontextdaten {#processing-rules-and-context-data}

Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Eigenschaften und andere Variablen für Berichte zu kopieren. Weitere Informationen finden Sie unter [Regeln](https://docs.adobe.com/content/help/de-DE/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Berücksichtigen Sie beim Umgang mit Verarbeitungsregeln folgende Informationen:

* Gruppieren Sie Ihre Kontextdatenvariablen mithilfe von Namensräumen, da Sie damit eine logische Reihenfolge beibehalten können. Um beispielsweise Informationen zu einem Produkt zu erfassen, können Sie die folgenden Variablen definieren:

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

   Dies kann beim Abschluss der einmaligen Zuordnung in Verarbeitungsregeln *etwas* einfacher sein, Sie verlieren jedoch die Lesbarkeit während des Debuggens und künftiger Codeaktualisierungen, was schwieriger sein kann. Stattdessen empfehlen wir dringend, beschreibende Namen für Schlüssel und Werte zu verwenden:

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
>Adobe behält sich den Namespace `"a."` vor. Um Probleme zu vermeiden, müssen Kontextdatenvariablen in Ihrem Anmeldeunternehmen eindeutig sein.

