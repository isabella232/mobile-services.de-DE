---
description: Versionshinweise und bekannte Probleme für iOS-SDKs 4.x für Experience Cloud-Lösungen.
seo-description: Versionshinweise und bekannte Probleme für iOS-SDKs 4.x für Experience Cloud-Lösungen.
seo-title: Versionshinweise
solution: Marketing Cloud,Analytics
title: Versionshinweise
topic: Entwickler und Implementierung
uuid: e 1613 dc 5-02 a 4-43 a 7-997 a -29 b 4 de 98 b 4 d 1
translation-type: tm+mt
source-git-commit: 80a60276f9926177c8958b8e87e9393a83e7e6a9

---


# Versionshinweise {#release-notes}

Im Folgenden finden Sie die Versionshinweise, bekannte Probleme und Hotfix-Informationen für ios sdks 4. x für Experience Cloud-Lösungen:

**2. August 2019: Version 4.18.7**

* Es wurde eine Änderung zurückgesetzt, die in Version 4.18.6 eingeführt wurde und in einigen Umgebungen einen Absturz auf Geräten verursachte, die eine ältere ios-Version als 11.0 verwendeten.

* Adobe Target: `requestLocationParameters` Die Eigenschaft wurde hinzugefügt `ADBTargetRequestObject`, in der die impressionid mit Target-Anforderungen gesendet werden kann.

**18. Juli 2019: Version 4.18.6**

* Adobe Target: Bei allen Anfragen sind jetzt Client und `sessionId` in den URL-Abfrageparametern enthalten.
* Adobe Target: Ein Speicherleck wurde behoben.
* Besucher-ID-Service: Die APIs `visitorAppendToURL` und `visitorGetUrlVariablesAsync` kodieren ihre Rückgabewerte jetzt nicht mehr doppelt.

   Die Doppelkodierung führte dazu, dass die Rückgabewerte von diesen APIs von bestimmten Sicherheitsprüfungen als falsch gekennzeichnet wurden.

**5. Juni 2019: Version 4.18.5**

* Analytics - Hängen Sie den Status der Push-Teilnahme an Lebenszyklusdaten an, wenn Push-Benachrichtigungen aktiviert sind.

**24. Mai 2019: Version 4.18.4**

* Besucher-ID-Service - Der Rückkehrtimeout für die
   `visitorGetUrlVariablesAsync` API auf 30 Sekunden.

* Besucher-ID-Service - Der `setPushIdentifier` API-Aufruf sendet jetzt bei jedem Aufruf einen Synchronisierungsaufruf an den Besucher-ID-Dienst.

Weitere Informationen zu aktuellen und älteren Versionshinweisen für alle Lösungen finden Sie unter [Adobe Experience Cloud – Versionshinweise](https://marketing.adobe.com/resources/help/en_US/whatsnew/).
