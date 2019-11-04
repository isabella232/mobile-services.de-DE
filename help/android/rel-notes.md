---
description: Versionshinweise und bekannte Probleme bei Android SDK 4.x für Experience Cloud-Lösungen.
seo-description: Versionshinweise und bekannte Probleme bei Android SDK 4.x für Experience Cloud-Lösungen.
seo-title: Versionshinweise
solution: Experience Cloud,Analytics
title: Versionshinweise
topic: Entwickler und Implementierung
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: ht
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# Versionshinweise {#release-notes}

Hier finden Sie die Versionshinweise, bekannten Probleme und Hotfix-Informationen für Android-SDK 4.x für die Experience Cloud-Lösungen:

**20. September 2019: Version 4.17.10**

* Allgemein: Die Generierung von Gebietsschema-Zeichenfolgen für einige Regionen auf Android-API-Stufe 21 oder höher wurde korrigiert.

**18. Juli 2019: Version 4.17.8**

* Adobe Target: Bei allen Anfragen sind jetzt Client und sessionId in den URL-Abfrageparametern enthalten.
* In-App-Messaging: Ein Problem wurde behoben, bei dem beim Auslösen einer Nachricht mit einer leeren Clickthrough-URL Android-Apps abgestürzt sind.
* Besucher-ID-Service: Die APIs `Visitor.appendToURL` und `Visitor.getUrlVariablesAsync` kodieren ihre Rückgabewerte jetzt nicht mehr doppelt.

   Die Doppelkodierung führte dazu, dass die Rückgabewerte von diesen APIs von bestimmten Sicherheitsprüfungen als falsch gekennzeichnet wurden.

**6. Juni 2019: Version 4.17.7**

* Allgemein: Netzwerkaufrufe auf Android-API-Ebenen unter 20 verwenden jetzt TLS 1.1 oder TLS 1.2.
* Analytics: Der „opt-in“-Status für Push-Benachrichtigungen wird an die Lebenszyklusdaten angehängt, wenn Push-Benachrichtigungen aktiviert sind.

**24. Mai 2019: Version 4.17.6**

* Besucher-ID-Dienst: Der
   `setPushIdentifier`-API-Aufruf sendet jetzt bei jedem Aufruf einen Synchronisierungsaufruf an den Besucher-ID-Dienst.

* Besucher-ID-Dienst: Die Timeouts für das Verbinden und Lesen wurden von 2 Sekunden auf 5 Sekunden erhöht.


Weitere Informationen zu aktuellen und älteren Versionshinweisen für alle Lösungen finden Sie unter [Adobe Experience Cloud – Versionshinweise](https://marketing.adobe.com/resources/help/de_DE/whatsnew/).
