---
description: Die Stapelverarbeitung von Treffern ermöglicht es Anwendungen, die gesendeten Treffer so lange zu speichern, bis die Anzahl der Treffer in der Warteschlange das konfigurierte Limit überschritten hat.
keywords: android; library; mobile; sdk
seo-description: Die Stapelverarbeitung von Treffern ermöglicht es Anwendungen, die gesendeten Treffer so lange zu speichern, bis die Anzahl der Treffer in der Warteschlange das konfigurierte Limit überschritten hat.
seo-title: Stapelverarbeitung von Treffern
solution: Marketing Cloud, Analytics
title: Stapelverarbeitung von Treffern
topic: Entwickler und Implementierung
uuid: ada 35 be 3-242 b -4 b 2 b-a 828-9 bf 998 dd 58 b 5
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Stapelverarbeitung von Treffern {#hit-batching}

Die Stapelverarbeitung von Treffern ermöglicht es Anwendungen, die gesendeten Treffer so lange zu speichern, bis die Anzahl der Treffer in der Warteschlange das konfigurierte Limit überschritten hat.

>[!IMPORTANT]
>
>Um Trefferstapel zu verwenden, **müssen** Sie Offline-Verfolgung aktivieren und SDK-Version 4.1 oder höher verwenden.

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

When the value is set to a number greater than 0, the SDK queues the number of hits equal to the *`batchLimit`* value. Nachdem dieser Grenzwert erreicht wurde, werden alle Treffer in der Warteschlange gesendet.

Die folgenden Methoden werden mit Treffer-Stapelverarbeitung verwendet:

* `Analytics.getQueueSize` () gibt einen `long`-Wert mit der Anzahl von Treffern zurück, die sich derzeit in der Warteschlange der Stapelverarbeitung befinden.

* `Analytics.sendQueuedHits` erzwingt in der Bibliothek das Senden aller Treffer aus der Warteschlange – unabhängig von der Anzahl der Treffer.
* `Analytics.clearQueue` löscht alle Treffer aus der Warteschlange, ohne sie zu senden.
