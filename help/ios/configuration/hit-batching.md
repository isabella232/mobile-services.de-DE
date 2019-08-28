---
description: Die Stapelverarbeitung von Treffern ermöglicht es Anwendungen, bei denen Offline-Verfolgung aktiviert ist, Treffer erst dann zu senden, wenn die Anzahl der Treffer in der Warteschlange den konfigurierten Wert erreicht.
seo-description: Die Stapelverarbeitung von Treffern ermöglicht es Anwendungen, bei denen Offline-Verfolgung aktiviert ist, Treffer erst dann zu senden, wenn die Anzahl der Treffer in der Warteschlange den konfigurierten Wert erreicht.
seo-title: Stapelverarbeitung von Treffern
solution: Marketing Cloud, Analytics
title: Stapelverarbeitung von Treffern
topic: Entwickler und Implementierung
uuid: 3 dda 3737-0695-4 cb 7-b 779-6 abca 2 d 6 e 0 d 9
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Stapelverarbeitung von Treffern {#hit-batching}

Die Stapelverarbeitung von Treffern ermöglicht es Anwendungen, bei denen Offline-Verfolgung aktiviert ist, Treffer erst dann zu senden, wenn die Anzahl der Treffer in der Warteschlange den konfigurierten Wert erreicht.

>[!IMPORTANT]
>
>Für Treffer-Batching ist SDK Version 4.1 oder höher erforderlich.

To enable hit batching, update your `ADBMobileConfig.json` file and specify a value for `batchLimit`:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Wenn der Wert auf eine Zahl größer 0 festgelegt ist, versetzt das SDK die Anzahl der Treffer in die Warteschlange, die mit *`batchLimit`*. Nachdem dieser Grenzwert erreicht wurde, werden alle Treffer in der Warteschlange gesendet.

Die folgenden Methoden werden mit Treffer-Stapelverarbeitung verwendet:

* `trackingGetQueueSize()` gibt einen `NSUInteger` mit der Anzahl der Treffer zurück, die sich aktuell in der Warteschlange für die Stapelverarbeitung von Treffern befinden.
* `trackingSendQueuedHits()` erzwingt in der Bibliothek das Senden aller Treffer aus der Warteschlange – unabhängig von der Anzahl der Treffer.
* `trackingClearQueue()` löscht alle Treffer aus der Warteschlange, ohne sie zu senden.

>[!CAUTION]
>
>Offline-Verfolgung muss aktiviert sein, um Trefferstapel zu verwenden.

