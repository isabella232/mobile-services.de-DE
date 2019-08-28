---
description: Versionshinweise und bekannte Probleme bei Android SDK 4.x für Experience Cloud-Lösungen.
seo-description: Versionshinweise und bekannte Probleme bei Android SDK 4.x für Experience Cloud-Lösungen.
seo-title: Versionshinweise
solution: Marketing Cloud,Analytics
title: Versionshinweise
topic: Entwickler und Implementierung
uuid: 16 bb 4 de 8-a 216-47 a 8-928 c -0 b 1 e 1421 adcf
translation-type: tm+mt
source-git-commit: 4c68e3fb3687a555fc7fdfa50a42e837b76a7d88

---


# Versionshinweise {#release-notes}

Im Folgenden finden Sie die Versionshinweise, bekannte Probleme und Hotfix-Informationen für Android SDK 4. x für Experience Cloud-Lösungen:

**2. August 2019: Version 4.17.9**

* Besucher-ID-Service: Korrektur der `StrictMode` Verletzung beim Aufruf von syncidentifiers.

   Diese Verletzung wurde durch Lesen freigegebener Voreinstellungen auf dem Haupt-Thread verursacht.

* Adobe Target: `requestLocationParameters` Das Attribut wurde hinzugefügt `TargetRequestObject`, in dem die impressionid mit Target-Anforderungen gesendet werden kann.

**18. Juli 2019: Version 4.17.8**

* Adobe Target: Alle Anforderungen enthalten jetzt den Client und die sessionid in den URL-Abfrageparametern.
* In-App-Messaging: Ein Problem wurde behoben, bei dem beim Auslösen einer Nachricht mit einer leeren Clickthrough-URL Android-Apps abgestürzt sind.
* Besucher-ID-Service: Die APIs `Visitor.appendToURL` und `Visitor.getUrlVariablesAsync` kodieren ihre Rückgabewerte jetzt nicht mehr doppelt.

   Die Doppelkodierung führte dazu, dass die Rückgabewerte von diesen APIs von bestimmten Sicherheitsprüfungen als falsch gekennzeichnet wurden.

**6. Juni 2019: Version 4.17.7**

* Allgemein: Netzwerkaufrufe auf Android-API-Ebenen unter 20 verwenden jetzt TLS 1.1 oder TLS 1.2.
* Analytics - Angehängte Push-Teilnahme an Lebenszyklusdaten an Lebenszyklusdaten, wenn Push-Benachrichtigungen aktiviert sind.

**24. Mai 2019: Version 4.17.6**

* Besucher-ID-Service - Die
   `setPushIdentifier` Der API-Aufruf sendet jetzt bei jedem Aufruf einen
Synchronisierungsaufruf an den Besucher-ID-Dienst.

* Besucher-ID-Service: Die Verbindungs- und Lestzeitzeichen
wurden von 2 Sekunden bis 5 Sekunden erhöht.


Weitere Informationen zu aktuellen und älteren Versionshinweisen für alle Lösungen finden Sie unter [Adobe Experience Cloud – Versionshinweise](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
