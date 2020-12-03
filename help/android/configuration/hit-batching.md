---
description: Die Stapelverarbeitung von Treffern ermöglicht es Anwendungen, die gesendeten Treffer so lange zu speichern, bis die Anzahl der Treffer in der Warteschlange das konfigurierte Limit überschritten hat.
keywords: android;library;mobile;sdk
seo-description: Die Stapelverarbeitung von Treffern ermöglicht es Anwendungen, die gesendeten Treffer so lange zu speichern, bis die Anzahl der Treffer in der Warteschlange das konfigurierte Limit überschritten hat.
seo-title: Stapelverarbeitung von Treffern
solution: Experience Cloud,Analytics
title: Stapelverarbeitung von Treffern
topic: Developer and implementation
uuid: ada35be3-242b-4b2b-a828-9bf998dd58b5
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 100%

---


# Stapelverarbeitung von Treffern {#hit-batching}

Die Stapelverarbeitung von Treffern ermöglicht es Anwendungen, die gesendeten Treffer so lange zu speichern, bis die Anzahl der Treffer in der Warteschlange das konfigurierte Limit überschritten hat.

>[!IMPORTANT]
>
>Zur Verwendung der Stapelverarbeitung von Treffern **müssen** Sie die Offline-Verfolgung aktivieren und SDK-Version 4.1 oder höher verwenden

Um die Stapelverarbeitung von Treffern zu aktivieren, aktualisieren Sie die Datei `ADBMobileConfig.json` und geben Sie einen Wert für `batchLimit` an:

```js
"analytics": {
    "batchLimit": 5,
    ...
}
```

Wenn der Wert auf eine Zahl größer 0 festgelegt ist, versetzt das SDK die Anzahl der Treffer in die Warteschlange, die dem Wert *`batchLimit`* entspricht. Nachdem dieser Schwellenwert erreicht wurde, werden alle Treffer in der Warteschlange gesendet.

Die folgenden Methoden werden bei der Stapelverarbeitung von Treffern verwendet:

* `Analytics.getQueueSize` gibt einen `long`-Wert mit der Anzahl von Treffern zurück, die sich derzeit in der Warteschlange der Stapelverarbeitung befinden.

* `Analytics.sendQueuedHits` erzwingt in der Bibliothek das Senden aller Treffer aus der Warteschlange – unabhängig von der Anzahl der Treffer.
* `Analytics.clearQueue` löscht alle Treffer aus der Warteschlange, ohne sie zu senden.
