---
description: Informationen, die Ihnen dabei helfen, das Plug-in aus Ihren Skripten aufzurufen.
keywords: Xamarin
solution: Experience Cloud
title: Aufrufen der Bibliothek
uuid: a480201a-4090-4662-8dd8-56f62144cd93
exl-id: a5ec1e1b-e29a-42c9-bcc9-bee05c427044
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 10%

---

# Aufrufen der Bibliothek{#making-calls-to-the-library}

Diese Informationen helfen Ihnen dabei, das Plug-in aus Ihren Skripten aufzurufen.

Wenn Sie das Plug-in aus Ihren Skripten aufrufen möchten, müssen Sie den Namespace importieren.

Durch Verwendung von `Com.Adobe.Mobile`:

* **iOS**: Nachdem Sie den Namespace importiert haben, können Sie Aufrufe direkt an das SDK über die statischen Methoden in den  `ADBMobile` Klassen vornehmen.

* **Android**: Sie können das SDK direkt über die statischen Methoden in den  `Config/Analytics/Target/AudienceManager/Media`Klassen aufrufen.
