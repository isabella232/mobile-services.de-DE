---
description: Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Eigenschaften und andere Variablen für Berichte zu kopieren.
seo-description: Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Eigenschaften und andere Variablen für Berichte zu kopieren.
seo-title: Verarbeitungsregeln und Kontextdaten
solution: Experience Cloud,Analytics
title: Verarbeitungsregeln und Kontextdaten
topic: Entwickler und Implementierung
uuid: ea892228-86f5-4980-acb8-45ae43c6996d
translation-type: ht
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Verarbeitungsregeln und Kontextdaten {#processing-rules-and-context-data}

Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Eigenschaften und andere Variablen für Berichte zu kopieren. Weitere Informationen finden Sie unter [Regeln](https://docs.adobe.com/content/help/de-DE/analytics/admin/admin-tools/processing-rules/processing-rules.html).

Berücksichtigen Sie beim Umgang mit Verarbeitungsregeln folgende Informationen:

* Gruppieren Sie Ihre Kontextdatenvariablen durch den Einsatz von Namespaces, um eine logische Ordnung zu wahren. Um beispielsweise Informationen zu einem Produkt zu erfassen, können Sie folgende Variablen definieren:

   ```js
   "product.type":"hat" 
   "product.team":"mariners" 
   "product.color":"blue"
   ```

* Kontextdatenvariablen werden in der Oberfläche der Verarbeitungsregeln alphabetisch sortiert. So können Sie schnell ermitteln, welche Variablen sich im selben Namespace befinden.

   Nutzen Sie für die Benennung von Kontextdatenschlüsseln nicht die eVar oder Eigenschaftennummer:

   ```js
   "eVar1":"jimbo"
   ```

   So wird es zwar *ein wenig* einfacher, wenn Sie die einmalige Zuordnung in Verarbeitungsregeln abschließen, aber bei Debugging und künftigen Code-Änderungen wird die Lesbarkeit beeinträchtigt, was die Arbeit erschweren kann. Wir empfehlen stattdessen, eigene beschreibende Namen für Schlüssel und Werte zu verwenden:

   ```js
   "username":"jimbo"
   ```

* Kontextvariablen, die Zählerereignisse definieren, sollten auf „1“ festgelegt werden:

   ```js
   "logon":"1"
   ```

* Kontextvariablen, die Inkrementereignisse definieren, können das Ereignis als Schlüssel und die zu erhöhende Menge als Wert aufweisen:

   ```js
   "levels completed":"6"
   ```

>[!TIP]
>
>Adobe behält sich den Namespace `"a."` vor. Um Probleme zu vermeiden, müssen Kontextdatenvariablen in Ihrem Anmeldeunternehmen eindeutig sein.

