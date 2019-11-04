---
description: Mit Postbacks können Sie vom SDK erfasste Daten an einen Drittanbieterserver senden. Mit denselben Auslösern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie das SDK so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.
keywords: Android;Bibliothek;Mobile;SDK
seo-description: Mit Postbacks können Sie vom SDK erfasste Daten an einen Drittanbieterserver senden. Mit denselben Auslösern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie das SDK so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.
seo-title: Postbacks
solution: Experience Cloud,Analytics
title: Übersicht über Postbacks
topic: Entwickler und Implementierung
uuid: 8bfd4374-2767-421d-891d-e1e9a99b6977
translation-type: ht
source-git-commit: f26dcd5cf9b19de49c9d034c854d9738c7843fb2

---


# Postbacks {#postbacks}

Mit Postbacks können Sie vom SDK erfasste Daten an einen Drittanbieterserver senden. Mit denselben Auslösern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie das SDK so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.

>[!IMPORTANT]
>
>Für diese Funktion ist die SDK-Version 4.6.0 oder höher erforderlich.

Postback-Nachrichten werden in die Warteschlange versetzt und folgen allen vorhandenen Online-/Offline-Regeln, die die Analytics-Datenerfassung regeln. Wenn eine Nachricht übereinstimmt (wie die gezeigten Nachrichten), brechen Postback-Nachrichten die übrigen Nachrichten nicht ab. Dies ermöglicht mehrere Postbacks beim selben Analytics-Treffer. Eine Definition finden Sie in der Zeile *Postbacks* unter [ADBMobile-JSON-Konfiguration](/help/android/configuration/json-config/json-config.md).

## Vorlagenerweiterungen {#section_6758AD05A24C4E9E965F5253294C164A}

Vorlagenerweiterungen sind in den Eigenschaften `templateurl` und `templatebody` verfügbar. Vorlagenelemente treten in folgender Form auf: `{key}`, wobei es sich bei dem `key` um einen Kontextdaten- oder herkömmlichen Schlüssel handeln kann. Die Werte, die für die Vorlagenerweiterung verfügbar sind, beschränken sich auf die [Lebenszyklusmetriken](/help/android/metrics.md) sowie auf jegliche benutzerdefinierten Daten, die an den Treffer angehängt sind, der die Nachricht ausgelöst hat. Zur Zeit sind keine verlaufs- oder segmentbasierten Daten verfügbar.

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