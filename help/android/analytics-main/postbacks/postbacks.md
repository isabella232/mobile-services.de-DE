---
description: Mit Postbacks können Sie vom SDK erfasste Daten an einen Drittanbieterserver senden. Mit denselben Auslösern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie das SDK so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.
keywords: android; library; mobile; sdk
seo-description: Mit Postbacks können Sie vom SDK erfasste Daten an einen Drittanbieterserver senden. Mit denselben Auslösern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie das SDK so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.
seo-title: Postbacks
solution: Marketing Cloud, Analytics
title: Übersicht über Postbacks
topic: Entwickler und Implementierung
uuid: 8 bfd 4374-2767-421 d -891 d-e 1 e 9 a 99 b 977
translation-type: tm+mt
source-git-commit: f26dcd5cf9b19de49c9d034c854d9738c7843fb2

---


# Postbacks {#postbacks}

Mit Postbacks können Sie vom SDK erfasste Daten an einen Drittanbieterserver senden. Mit denselben Auslösern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie das SDK so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.

>[!IMPORTANT]
>
>Für diese Funktion ist SDK Version 4.6.0 oder höher erforderlich.

Postback-Nachrichten werden in die Warteschlange versetzt und folgen allen vorhandenen Online-/Offline-Regeln, die die Analytics-Datenerfassung regeln. Wenn eine Nachricht übereinstimmt (wie die gezeigten Nachrichten), brechen Postback-Nachrichten die übrigen Nachrichten nicht ab. Dies ermöglicht mehrere Postbacks beim selben Analytics-Treffer. Eine Definition finden Sie in der Zeile *Postbacks* unter [ADBMobile-JSON-Konfiguration](/help/android/configuration/json-config/json-config.md).

## Template expansions {#section_6758AD05A24C4E9E965F5253294C164A}

Template expansions are available in the `templateurl` and `templatebody` properties. Template items take the form of `{key}`, where `key` is a context data key or traditional data key. The values that are available for template expansion are limited to the [Lifecycle metrics](/help/android/metrics.md), in addition to any custom data that is attached to the hit that triggers the message. Zur Zeit sind keine verlaufs- oder segmentbasierten Daten verfügbar.

Es gibt auch spezifische, reservierte Vorlagen, die das SDK automatisch durch interne, dem SDK bekannte Daten ersetzt.

Zu dieser Liste zählen folgende Elemente:

| Token-Name | Token-Beschreibung |
|--- |--- |
| {%sdkver%} | Gibt die SDK-Version zurück. |
| {%cachebust%} | Löst eine zufällige Zahl zwischen 1 und 100.000.000 auf. |
| {%adid%} | Gibt die Advertiser-ID für Android zurück. Hinweis: Dies funktioniert nur, wenn Sie `submitAdvertisingIdentifierTask` verwendet haben. |
| {%pushid%} | Gibt das Push-ID-Token zurück. Hinweis: Dies funktioniert nur, wenn Sie `setPushIdentifier` verwendet haben. |
| {%timestampu%} | Gibt den aktuellen Zeitstempel in Epochenzeit zurück. |
| {%timestampz%} | Gibt den aktuellen Zeitstempel im JavaScript-Format (ISO 8601) zurück. |