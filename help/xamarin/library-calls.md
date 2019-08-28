---
description: Informationen, die Ihnen dabei helfen, das Plug-in aus Ihren Skripten aufzurufen.
keywords: Xamarin
seo-description: Informationen, die Ihnen dabei helfen, das Plug-in aus Ihren Skripten aufzurufen.
seo-title: Aufrufen der Bibliothek
solution: Marketing Cloud, Entwickler
title: Aufrufen der Bibliothek
uuid: a 480201 a -4090-4662-8 dd 8-56 f 62144 cd 93
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Making calls to the library{#making-calls-to-the-library}

Diese Informationen helfen Ihnen, das Plugin aus Ihren Skripten aufzurufen.

Wenn das Plug-in aus den Skripten heraus aufgerufen werden soll, müssen Sie den Namespace importieren.

Verwenden `Com.Adobe.Mobile`von:

* **Ios**: Nachdem Sie den Namespace importiert haben, können Sie das SDK direkt über die statischen Methoden in den `ADBMobile` Klassen aufrufen.

* **Android**: Sie können das SDK direkt über die statischen Methoden in den `Config/Analytics/Target/AudienceManager/Media`Klassen aufrufen.

