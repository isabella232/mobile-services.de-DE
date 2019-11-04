---
description: Versionshinweise und bekannte Probleme für iOS-SDK 4.x für Experience Cloud-Lösungen.
seo-description: Versionshinweise und bekannte Probleme für iOS-SDK 4.x für Experience Cloud-Lösungen.
seo-title: Versionshinweise
solution: Experience Cloud,Analytics
title: Versionshinweise
topic: Entwickler und Implementierung
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
translation-type: ht
source-git-commit: 7fe7c78262a6d35dd27787554bb4f9ee92faa952

---


# Versionshinweise {#release-notes}

Hier finden Sie die Versionshinweise, bekannten Probleme und Hotfix-Informationen für iOS SDK 4.x für die Experience Cloud-Lösungen:

**20. September 2019: Version 4.18.8**

* In App-Nachrichten:

   * Auf Geräten mit iOS 10 oder höher wird das `UserNotifications`-Framework jetzt verwendet, um lokale Benachrichtigungen für Apps zu planen, die mit dem `UserNotifications.framework` verknüpft sind.
   * Vollbildnachrichten verwenden jetzt WKWebViews vom `WebKit.framework`, die in Ihrem Xcode-Projekt verknüpft werden müssen.
   * Ein Fehler wurde behoben, durch den die Push-Clickthrough-Payload nicht als Eigenschaft für In-App-Nachrichten verwendet werden konnte.
   * Es wurde ein Absturzproblem behoben.

* Allgemein: Ein Fehler wurde behoben, bei dem SDK-Daten bei jedem Analytics-Aufruf mit der gekoppelten watchOS-App synchronisiert wurden.

**2. August 2019: Version 4.18.7**

* Es wurde eine Änderung rückgängig gemacht, die in Version 4.18.6 eingeführt wurde und in einigen Umgebungen einen Absturz auf Geräten verursachte, auf denen eine iOS-Version älter als 11.0 ausgeführt wurde.

* Adobe Target: Die `requestLocationParameters`-Eigenschaft wurde in `ADBTargetRequestObject` hinzugefügt, die das Senden der impressionId mit Target-Anforderungen ermöglicht.

**18. Juli 2019: Version 4.18.6**

* Adobe Target: Bei allen Anfragen sind jetzt Client und `sessionId` in den URL-Abfrageparametern enthalten.
* Adobe Target: Ein Speicherleck wurde behoben.
* Besucher-ID-Service: Die APIs `visitorAppendToURL` und `visitorGetUrlVariablesAsync` kodieren ihre Rückgabewerte jetzt nicht mehr doppelt.

   Die Doppelkodierung führte dazu, dass die Rückgabewerte von diesen APIs von bestimmten Sicherheitsprüfungen als falsch gekennzeichnet wurden.

**5. Juni 2019: Version 4.18.5**

* Analytics: Der „opt-in“-Status für Push-Benachrichtigungen wird an die Lebenszyklusdaten angehängt, wenn Push-Benachrichtigungen aktiviert sind.

**24. Mai 2019: Version 4.18.4**

* Besucher-ID-Dienst: Das Rückgabe-Timeout für die
   `visitorGetUrlVariablesAsync`-API wurde auf 30 Sekunden erhöht.

* Besucher-ID-Dienst: Der `setPushIdentifier`-API-Aufruf sendet jetzt bei jedem Aufruf einen Synchronisierungsaufruf an den Besucher-ID-Dienst.

Weitere Informationen zu aktuellen und älteren Versionshinweisen für alle Lösungen finden Sie unter [Adobe Experience Cloud – Versionshinweise](https://marketing.adobe.com/resources/help/de_DE/whatsnew/).
