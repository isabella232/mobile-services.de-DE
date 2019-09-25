---
description: Versionshinweise und bekannte Probleme bei Android SDK 4.x für Experience Cloud-Lösungen.
seo-description: Versionshinweise und bekannte Probleme bei Android SDK 4.x für Experience Cloud-Lösungen.
seo-title: Versionshinweise
solution: Marketing Cloud, Analytics
title: Versionshinweise
topic: Entwickler und Implementierung
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
translation-type: tm+mt
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# Versionshinweise {#release-notes}

Here is the release notes, known issues, and hot fix information for Android SDK 4.x for Experience Cloud Solutions:

**September 20, 2019: Version 4.17.10**

* General: Fixed locale string generation for some regions on Android API level 21 or newer.

**July 18, 2019: Version 4.17.8**

* Adobe Target: Alle Anforderungen enthalten jetzt den Client und die sessionId in den URL-Abfrageparametern.
* In-App-Messaging: Ein Problem wurde behoben, bei dem beim Auslösen einer Nachricht mit einer leeren Clickthrough-URL Android-Apps abgestürzt sind.
* Besucher-ID-Service: Die APIs `Visitor.appendToURL` und `Visitor.getUrlVariablesAsync` kodieren ihre Rückgabewerte jetzt nicht mehr doppelt.

   Die Doppelkodierung führte dazu, dass die Rückgabewerte von diesen APIs von bestimmten Sicherheitsprüfungen als falsch gekennzeichnet wurden.

**June 6, 2019: Version 4.17.7**

* General - Networking calls on Android API levels lower than 20 will now use TLS 1.1 or TLS 1.2.
* Analytics - Appended push opt-in status to Lifecycle data when push notifications are enabled.

**May 24, 2019: Version 4.17.6**

* visitor ID Service - The
   `setPushIdentifier` API call now sends a
sync call to the Visitor ID Service every time it is called.

* Visitor ID Service - Increased the connect and read
timeouts from 2 seconds to 5 seconds.


Weitere Informationen zu aktuellen und älteren Versionshinweisen für alle Lösungen finden Sie unter [Adobe Experience Cloud – Versionshinweise](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
