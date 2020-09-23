---
description: Mit Postbacks können Sie Daten, die vom SDK erfasst werden, an einen Drittanbieter-Server senden. Indem Sie dieselben Auslöser und Eigenschaften verwenden, die Sie zur Anzeige einer In-App-Nachricht verwenden, können Sie das SDK so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.
seo-description: Mit Postbacks können Sie Daten, die vom SDK erfasst werden, an einen Drittanbieter-Server senden. Indem Sie dieselben Auslöser und Eigenschaften verwenden, die Sie zur Anzeige einer In-App-Nachricht verwenden, können Sie das SDK so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.
seo-title: Postbacks
solution: Experience Cloud,Analytics
title: Übersicht über Postbacks
uuid: 25e2a5fb-1203-40dd-96cd-b23e0f23376d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 27%

---


# Übersicht über Postbacks {#postbacks}

Mit Postbacks können Sie Daten, die vom SDK erfasst werden, an einen Drittanbieter-Server senden. Indem Sie dieselben Auslöser und Eigenschaften verwenden, die Sie zur Anzeige einer In-App-Nachricht verwenden, können Sie das SDK so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet.

>[!IMPORTANT]
>
>Für diese Funktion ist die SDK-Version 4.6.0 oder höher erforderlich.

Postback-Nachrichten werden in die Warteschlange gestellt und befolgen alle bestehenden Online-/Offline-Regeln, die für die Datenerfassung in der Analyse gelten. Wenn eine Nachricht übereinstimmt (wie die angezeigten Nachrichten), werden die übrigen Nachrichten nicht durch Postback-Nachrichten abgebrochen. Dadurch können mehrere Postbacks für denselben Analytics-Treffer ausgeführt werden. Eine Definition finden Sie in der Zeile *Postbacks* unter [ADBMobile-JSON-Konfiguration](/help/ios/configuration/json-config/json-config.md).

## Vorlagenerweiterungen {#section_6758AD05A24C4E9E965F5253294C164A}

Vorlagenerweiterungen sind in den Eigenschaften `templateurl` und `templatebody` verfügbar. Vorlagenelemente treten in folgender Form auf: `{key}`, wobei es sich bei dem `key` um einen Kontextdaten- oder herkömmlichen Schlüssel handeln kann. The values available for template expansion are limited to the [standard Lifecycle variables list](/help/ios/metrics.md), in addition to any custom data attached to the hit that triggers the message. Derzeit sind keine historischen oder segmentbasierten Daten verfügbar.

Es gibt auch spezielle, reservierte Vorlagen, die das SDK automatisch durch interne Daten ersetzt, die dem SDK bekannt sind.

Diese Liste umfasst:

| Token-Name | Token-Beschreibung |
|--- |--- |
| `{%sdkver%}` | Gibt die SDK-Version zurück. |
| `{%cachebust%}` | Löst eine zufällige Zahl zwischen 1 und 100.000.000 auf. |
| `{%adid%}` | Gibt IDFA zurück. Dieses Token funktioniert nur, wenn Sie `setAdvertisingIdentifier` verwendet haben. |
| `{%pushid%}` | Gibt das Push-ID-Token zurück. Dieses Token funktioniert nur, wenn Sie `setPushIdentifier` verwendet haben. |
| `{%timestampu%}` | Gibt den aktuellen Zeitstempel in Epochenzeit zurück. |
| `{%timestampz%}` | Gibt den aktuellen Zeitstempel im JavaScript-Format (ISO 8601) zurück. |