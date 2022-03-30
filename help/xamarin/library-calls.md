---
description: Informationen, die Ihnen dabei helfen, das Plug-in aus Ihren Skripten aufzurufen.
keywords: Xamarin
solution: Experience Cloud Services
title: Aufrufen der Bibliothek
uuid: a480201a-4090-4662-8dd8-56f62144cd93
exl-id: a5ec1e1b-e29a-42c9-bcc9-bee05c427044
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 10%

---

# Aufrufen der Bibliothek{#making-calls-to-the-library}

Diese Informationen helfen Ihnen dabei, das Plug-in aus Ihren Skripten aufzurufen.

Wenn Sie das Plug-in aus Ihren Skripten aufrufen möchten, müssen Sie den Namespace importieren.

Durch Verwendung von `Com.Adobe.Mobile`:

* **iOS**: Nach dem Import des Namespace können Sie Aufrufe direkt an das SDK über die statischen Methoden im Abschnitt `ADBMobile` Klassen.

* **Android**: Sie können Aufrufe direkt an das SDK über die statischen Methoden im Abschnitt `Config/Analytics/Target/AudienceManager/Media`Klassen.
