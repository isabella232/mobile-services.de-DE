---
description: Mit Postbacks können Sie Daten, die vom SDK erfasst werden, an einen Drittanbieter-Server senden. Mit denselben Triggern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie das SDK so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.
keywords: Android;Bibliothek;Mobile;SDK
solution: Experience Cloud Services,Analytics
title: Übersicht über Postbacks
topic-fix: Developer and implementation
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
exl-id: 318f6eab-ff71-4bfe-8eb7-51a35380b992
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 100%

---

# Postbacks {#postbacks}

Mit Postbacks können Sie Daten, die vom SDK erfasst werden, an einen Drittanbieter-Server senden. Mit denselben Triggern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie das SDK so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.

>[!IMPORTANT]
>
>Für diese Funktion ist die SDK-Version 4.6.0 oder höher erforderlich.

Postback-Nachrichten werden in die Warteschlange gestellt und befolgen alle bestehenden Online-/Offline-Regeln, die für die Analysedatenerfassung gelten. Wenn eine Nachricht übereinstimmt (wie es bei angezeigten Nachrichten der Fall ist), brechen Postback-Nachrichten den Rest der Nachrichten nicht ab. Dadurch können mehrere Postbacks für denselben Analytics-Treffer ausgeführt werden. Eine Definition finden Sie in der Zeile *Postbacks* unter  [ADBMobile-JSON-Konfiguration](/help/android/configuration/json-config/json-config.md).

## Vorlagenerweiterungen {#section_6758AD05A24C4E9E965F5253294C164A}

Vorlagenerweiterungen sind in den Eigenschaften `templateurl` und `templatebody` verfügbar. Vorlagenelemente treten in folgender Form auf: `{key}`, wobei es sich bei dem `key` um einen Kontextdaten- oder herkömmlichen Schlüssel handeln kann. Die Werte, die für die Vorlagenerweiterung verfügbar sind, beschränken sich auf die [Lebenszyklusmetriken](/help/android/metrics.md) sowie auf jegliche benutzerdefinierten Daten, die an den Treffer angehängt sind, der die Nachricht ausgelöst hat. Derzeit sind keine historischen oder segmentbasierten Daten verfügbar.

Es gibt auch spezifische, reservierte Vorlagen, die das SDK automatisch durch interne Daten ersetzt, die dem SDK bekannt sind.

Diese Liste umfasst:

| Token-Name | Token-Beschreibung |
|--- |--- |
| {%sdkver%} | Gibt die SDK-Version zurück. |
| {%cachebust%} | Löst eine zufällige Zahl zwischen 1 und 100.000.000 auf. |
| {%adid%} | Gibt die Advertiser-ID für Android zurück. Hinweis: Dies funktioniert nur, wenn Sie `submitAdvertisingIdentifierTask` verwendet haben. |
| {%pushid%} | Gibt das Push-ID-Token zurück. Hinweis: Dies funktioniert nur, wenn Sie `setPushIdentifier` verwendet haben. |
| {%timestampu%} | Gibt den aktuellen Zeitstempel in Epochenzeit zurück. |
| {%timestampz%} | Gibt den aktuellen Zeitstempel im JavaScript-Format (ISO 8601) zurück. |
