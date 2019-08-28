---
description: Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Eigenschaften und andere Variablen für Berichte zu kopieren.
seo-description: Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Eigenschaften und andere Variablen für Berichte zu kopieren.
seo-title: Verarbeitungsregeln und Kontextdaten
solution: Marketing Cloud, Analytics
title: Verarbeitungsregeln und Kontextdaten
topic: Entwickler und Implementierung
uuid: 51338 ccd-fa 52-4 d 9 c -97 c 4-947 a 4100465 d
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Processing rules and context data{#processing-rules-and-context-data}

Verarbeitungsregeln werden verwendet, um die in Kontextdatenvariablen gesendeten Daten in eVars, Eigenschaften und andere Variablen für Berichte zu kopieren.

Weitere Informationen finden Sie unter folgenden Themen:

* [Training zu Verarbeitungsregeln](https://tv.adobe.com/embed/1181/16506/) beim Summit 2013
* Autorisierung zur Verwendung von Verarbeitungsregeln

   Weitere Informationen zu Verarbeitungsregeln finden Sie unter [Verarbeitungsregeln.](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html)

Berücksichtigen Sie beim Umgang mit Verarbeitungsregeln folgende Informationen:

* Gruppieren Sie Ihre Kontextdatenvariablen durch den Einsatz von Namespaces, um eine logische Ordnung zu wahren.

   Wenn Sie beispielsweise Informationen zu einem Produkt erfassen möchten, können Sie die folgenden Variablen definieren:

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

   Dadurch wird es *etwas* einfacher, wenn Sie die einmalige Zuordnung in den Verarbeitungsregeln durchführen. Sie verlieren dadurch jedoch auch die Lesbarkeit während des Debuggings und künftiger Codeaktualisierungen, was wiederum komplizierter sein kann. Verwenden Sie stattdessen beschreibende Namen für Schlüssel und Werte:

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
>Adobe behält sich den Namespace `a.`vor. Abgesehen von dieser Einschränkung, die dazu dient, Konflikte zu vermeiden, besteht die einzige Anforderung darin, dass die Kontextdatenvariablen in Ihrem Anmeldeunternehmen eindeutig sein müssen.

