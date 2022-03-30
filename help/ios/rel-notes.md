---
description: Versionshinweise und bekannte Probleme für iOS-SDK 4.x für Experience Cloud-Lösungen.
solution: Experience Cloud Services,Analytics
title: Versionshinweise
topic-fix: Developer and implementation
uuid: e1613dc5-02a4-43a7-997a-29b4de98b4d1
exl-id: dd1e6bab-65e7-4a68-b3ec-21fb1a08aca2
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 99%

---

# Versionshinweise {#release-notes}

Hier finden Sie die Versionshinweise, bekannten Probleme und Hotfix-Informationen für iOS SDK 4.x für die Experience Cloud-Lösungen:

## 13. April 2021: Version 4.21.2

* Besucher-ID-Service: Es wurde ein Problem behoben, bei dem leere Werbe-IDs mit dem Besucher-ID-Service synchronisiert wurden.

## 13. Januar 2021: Version 4.21.1

* Allgemein – Es wurde ein Problem behoben, das evtl. beim Herunterfahren des Programms SQLite Ausnahmen verursachte.

## 15. Dezember 2020: Version 4.21.0

* Allgemein – Das SDK wird jetzt mit XCFrameworks verteilt, um Hardware mit der neuen Apple-M1-Architektur zu unterstützen und gleichzeitig die Unterstützung der bestehenden Intel-Architektur zu erhalten.
   * WICHTIG: Für die Aktualisierung auf AdobeMobile XCFrameworks ist Xcode 12.0 oder höher erforderlich
   * WICHTIG: Bei Verwendung von Cocoapods erfordert die Aktualisierung auf AdobeMobile XCFrameworks die Version Cocoapods 1.10.0 oder höher

## 4. November 2020: Version 4.20.0

* Besucher-ID-Dienst: Der Statusparameter device_approval wurde hinzugefügt, wenn setAdvertisingIdentifier aufgerufen wird, nachdem die Anzeigenverfolgung aktiviert/deaktiviert wurde.
* Analytics: Es wurde ein Fehler behoben, durch den Analytics-Hits bei einer Installation verzögert gesendet wurden, wenn iAd.framework verknüpft ist und auf dem Gerät „Eingeschränkte Anzeigenverfolgung“ aktiviert ist.

## 16. Juli 2020: Version 4.19.3

* Allgemein: Es wurde ein Fehler behoben, der dazu führte, dass Deeplink-URLs mit mehreren Gleichheitszeichen im Abfrageparameter nicht ordnungsgemäß verarbeitet werden konnten.

## 24. März 2020: Version 4.19.2

* Allgemein: Es wurden einige Lecks im Target-Code behoben.

## 12. März 2020: Version 4.19.1

* Allgemein: Ein möglicher Absturz wurde behoben, wenn Swift-Enums in den Kontextdaten für Tracking-Aufrufe enthalten sind.
* Target: Die Target-Sitzungs-ID wird jetzt als Kontextdatenparameter „a.target.sessionId“ im internen Treffer von Analytics für Target hinzugefügt, der an Adobe Analytics gesendet wird.

## 4. Februar 2020: Version 4.19.0

* Lebenszyklus: Es wurde die neue API pauseCollectingLifecycleData hinzugefügt, um die von einigen alten iOS-Geräten gemeldeten anormalen Sitzungslängen zu verringern.

## 8. November 2019: Version 4.18.9

* In-App-Nachrichten: Es wurde ein Fehler behoben, durch den zwischengespeicherte oder gebündelte Bilder nicht in die Vollbildschirm-Nachrichten geladen werden konnten.

## 20. September 2019: Version 4.18.8

* In App-Nachrichten:

   * Auf Geräten mit iOS 10 oder höher wird das `UserNotifications`-Framework jetzt verwendet, um lokale Benachrichtigungen für Apps zu planen, die mit dem `UserNotifications.framework` verknüpft sind.
   * Vollbildnachrichten verwenden jetzt WKWebViews vom `WebKit.framework`, die in Ihrem Xcode-Projekt verknüpft werden müssen.
   * Ein Fehler wurde behoben, durch den die Push-Clickthrough-Payload nicht als Eigenschaft für In-App-Nachrichten verwendet werden konnte.
   * Es wurde ein Absturzproblem behoben.

* Allgemein: Ein Fehler wurde behoben, bei dem SDK-Daten bei jedem Analytics-Aufruf mit der gekoppelten watchOS-App synchronisiert wurden.

## 2. August 2019: Version 4.18.7

* Es wurde eine Änderung rückgängig gemacht, die in Version 4.18.6 eingeführt wurde und in einigen Umgebungen einen Absturz auf Geräten verursachte, auf denen eine iOS-Version älter als 11.0 ausgeführt wurde.

* Adobe Target: Die `requestLocationParameters`-Eigenschaft wurde in `ADBTargetRequestObject` hinzugefügt, die das Senden der impressionId mit Target-Anforderungen ermöglicht.

## 18. Juli 2019: Version 4.18.6

* Adobe Target: Bei allen Anfragen sind jetzt Client und `sessionId` in den URL-Abfrageparametern enthalten.
* Adobe Target: Ein Speicherleck wurde behoben.
* Besucher-ID-Service: Die APIs `visitorAppendToURL` und `visitorGetUrlVariablesAsync` kodieren ihre Rückgabewerte jetzt nicht mehr doppelt.

   Die Doppelkodierung führte dazu, dass die Rückgabewerte von diesen APIs von bestimmten Sicherheitsprüfungen als falsch gekennzeichnet wurden.

## 5. Juni 2019: Version 4.18.5

* Analytics: Der „opt-in“-Status für Push-Benachrichtigungen wird an die Lebenszyklusdaten angehängt, wenn Push-Benachrichtigungen aktiviert sind.

## 24. Mai 2019: Version 4.18.4

* Besucher-ID-Dienst: Das Rückgabe-Timeout für die
   `visitorGetUrlVariablesAsync`-API wurde auf 30 Sekunden erhöht.

* Besucher-ID-Dienst: Der `setPushIdentifier`-API-Aufruf sendet jetzt bei jedem Aufruf einen Synchronisierungsaufruf an den Besucher-ID-Dienst.

Weitere Informationen zu aktuellen und älteren Versionshinweisen für alle Lösungen finden Sie unter [Adobe Experience Cloud – Versionshinweise](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=de).
