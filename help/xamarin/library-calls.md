---
description: Informationen, die Sie beim Aufrufen des Plugins von Ihren Skripten aus unterstützen.
keywords: Xamarin
seo-description: Informationen, die Sie beim Aufrufen des Plugins von Ihren Skripten aus unterstützen.
seo-title: Aufrufen der Bibliothek
solution: Experience Cloud
title: Aufrufen der Bibliothek
uuid: a480201a-4090-4662-8dd8-56f62144cd93
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 13%

---


# Aufrufen der Bibliothek{#making-calls-to-the-library}

Diese Informationen helfen Ihnen, das Plugin von Ihren Skripten aufzurufen.

Wenn Sie das Plugin von Ihren Skripten aufrufen möchten, müssen Sie den Namensraum importieren.

Durch Verwendung `Com.Adobe.Mobile`:

* **iOS**: Nach dem Importieren des Namensraums können Sie über die statischen Methoden in den `ADBMobile` Klassen direkt an das SDK aufrufen.

* **Android**: Sie können das SDK direkt über die statischen Methoden in den `Config/Analytics/Target/AudienceManager/Media`Klassen aufrufen.

