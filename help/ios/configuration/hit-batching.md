---
description: Die Stapelverarbeitung von Treffern ermöglicht es Anwendungen, bei denen Offline-Verfolgung aktiviert ist, Treffer erst dann zu senden, wenn die Anzahl der Treffer in der Warteschlange den konfigurierten Wert erreicht.
seo-description: Die Stapelverarbeitung von Treffern ermöglicht es Anwendungen, bei denen Offline-Verfolgung aktiviert ist, Treffer erst dann zu senden, wenn die Anzahl der Treffer in der Warteschlange den konfigurierten Wert erreicht.
seo-title: Stapelverarbeitung von Treffern
solution: Experience Cloud,Analytics
title: Stapelverarbeitung von Treffern
topic: Entwickler und Implementierung
uuid: 3dda7372-0695-4cb7-b779-6abca2d6e0d9
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Stapelverarbeitung von Treffern {#hit-batching}

Die Stapelverarbeitung von Treffern ermöglicht es Anwendungen, bei denen Offline-Verfolgung aktiviert ist, Treffer erst dann zu senden, wenn die Anzahl der Treffer in der Warteschlange den konfigurierten Wert erreicht.

>[!IMPORTANT]
>
>Die Stapelverarbeitung von Treffern erfordert die SDK-Version 4.1 oder höher.

Um die Stapelverarbeitung von Treffern zu aktivieren, aktualisieren Sie die Datei `ADBMobileConfig.json` und geben Sie einen Wert für `batchLimit` an:

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
>Die Offline-Verfolgung muss aktiviert sein, um die Stapelverarbeitung von Treffern zu verwenden.

