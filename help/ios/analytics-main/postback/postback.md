---
description: Mit Postbacks können Sie vom SDK erfasste Daten an einen Drittanbieterserver senden. Mit denselben Auslösern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie das SDK so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.
seo-description: Mit Postbacks können Sie vom SDK erfasste Daten an einen Drittanbieterserver senden. Mit denselben Auslösern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie das SDK so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.
seo-title: Postbacks
solution: Marketing Cloud, Analytics
title: Übersicht über Postbacks
uuid: 25 e 2 a 5 fb -1203-40 dd -96 cd-b 23 e 0 f 23376 d
translation-type: tm+mt
source-git-commit: 83e6968efb0ed1b4ef504286c6cb2e8e4d2eaf94

---


# Übersicht über Postbacks {#postbacks}

Mit Postbacks können Sie vom SDK erfasste Daten an einen Drittanbieterserver senden. Mit denselben Auslösern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie das SDK so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.

>[!IMPORTANT]
>
>Für diese Funktion ist SDK Version 4.6.0 oder höher erforderlich.

Postback-Nachrichten werden in die Warteschlange versetzt und folgen allen vorhandenen Online-/Offline-Regeln, die die Analytics-Datenerfassung regeln. Wenn eine Nachricht übereinstimmt (wie die gezeigten Nachrichten), brechen Postback-Nachrichten die übrigen Nachrichten nicht ab. Dies ermöglicht mehrere Postbacks beim selben Analytics-Treffer. Eine Definition finden Sie in der Zeile *Postbacks* unter [ADBMobile-JSON-Konfiguration](/help/ios/configuration/json-config/json-config.md).

## Template expansions {#section_6758AD05A24C4E9E965F5253294C164A}

Template expansions are available in both the `templateurl` and `templatebody` properties. Template items take the form of `{key}`, where `key` is a context-data key, or traditional data key. Die für die Vorlagenerweiterung verfügbaren Werte beschränken sich auf die in der [Liste für Lebenszyklus-Standardvariablen](/help/ios/metrics.md) aufgeführten, und zwar zusätzlich zu benutzerdefinierten Daten, die an den Treffer angefügt sind, der die Nachricht auslöst. Zurzeit sind keine verlaufsbasierten oder segmentbasierten Daten verfügbar.

Es gibt darüber hinaus spezifische, reservierte Vorlagen, die vom SDK automatisch durch interne Daten, die dem SDK bekannt sind, für Sie ersetzt werden.

Diese Liste enthält Folgendes:

| Token-Name | Token-Beschreibung |
|--- |--- |
| `{%sdkver%}` | Gibt die SDK-Version zurück. |
| `{%cachebust%}` | Löst eine zufällige Zahl zwischen 1 und 100.000.000 auf. |
| `{%adid%}` | Gibt IDFA zurück. Dieses Token funktioniert nur, wenn Sie es verwendet `setAdvertisingIdentifier`haben. |
| `{%pushid%}` | Gibt das Push-ID-Token zurück. Dieses Token funktioniert nur, wenn Sie es verwendet `setPushIdentifier`haben. |
| `{%timestampu%}` | Gibt den aktuellen Zeitstempel in Epochenzeit zurück. |
| `{%timestampz%}` | Gibt den aktuellen Zeitstempel im JavaScript-Format (ISO 8601) zurück. |