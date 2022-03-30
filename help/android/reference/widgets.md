---
description: Android-Widgets können mit denselben Methoden wie Ihre App verfolgt werden. Widgets teilen den Anwendungskontext mit Ihrer Anwendung, so dass die Reihenfolge der Treffer und die Identifizierung der Besucher erhalten bleibt.
keywords: Android;Bibliothek;Mobile;SDK
solution: Experience Cloud Services,Analytics
title: Android-Widgets
topic-fix: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
exl-id: 229ea987-256a-45f4-a5ca-afe17dd596b8
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 100%

---

# Android-Widgets {#android-widgets}

Android-Widgets können mit denselben Methoden wie Ihre App verfolgt werden. Widgets teilen den Anwendungskontext mit Ihrer Anwendung, so dass die Reihenfolge der Treffer und die Identifizierung der Besucher erhalten bleibt.

Die folgenden Richtlinien helfen Ihnen beim Tracking von Android-Widgets:

* Implementieren Sie Aufrufe zu Lebenszyklusmetriken (`startActivity`/ `stopActivity`) im Widget.

* Fügen Sie einen `trackState`- oder `trackEvent`-Aufruf zur `onEnabled`-Methode eines Widgets hinzu, um aufzuzeichnen, wenn das Widget zum Startbildschirm hinzugefügt wird.

* Um aufzuzeichnen, wenn die App über ein Widget gestartet wird, fügen Sie einen `trackState`- oder `trackEvent`-Aufruf hinzu, bevor Sie den Intent für den Start der Anwendung erstellen.

* Um den Kontext einer Aktion zu verfolgen, können Sie eine `ContextData`-Variable definieren, die die Option bietet, jede Aktion separat zu segmentieren (z. B. `AppExperienceType="widget"` statt `app`).
