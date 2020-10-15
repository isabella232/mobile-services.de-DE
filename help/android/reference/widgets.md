---
description: Android-Widgets können mit denselben Methoden wie Ihre App verfolgt werden. Widgets teilen den Anwendungskontext mit Ihrer Anwendung, so dass die Reihenfolge der Treffer und die Identifizierung der Besucher erhalten bleibt.
keywords: android;library;mobile;sdk
seo-description: Android-Widgets können mit denselben Methoden wie Ihre App verfolgt werden. Widgets teilen den Anwendungskontext mit Ihrer Anwendung, so dass die Reihenfolge der Treffer und die Identifizierung der Besucher erhalten bleibt.
seo-title: Android-Widgets
solution: Experience Cloud,Analytics
title: Android-Widgets
topic: Developer and implementation
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '179'
ht-degree: 100%

---


# Android-Widgets {#android-widgets}

Android-Widgets können mit denselben Methoden wie Ihre App verfolgt werden. Widgets teilen den Anwendungskontext mit Ihrer Anwendung, so dass die Reihenfolge der Treffer und die Identifizierung der Besucher erhalten bleibt.

Die folgenden Richtlinien helfen Ihnen beim Tracking von Android-Widgets:

* Implementieren Sie Aufrufe zu Lebenszyklusmetriken (`startActivity`/ `stopActivity`) im Widget.

* Fügen Sie einen `trackState`- oder `trackEvent`-Aufruf zur `onEnabled`-Methode eines Widgets hinzu, um aufzuzeichnen, wenn das Widget zum Startbildschirm hinzugefügt wird.

* Um aufzuzeichnen, wenn die App über ein Widget gestartet wird, fügen Sie einen `trackState`- oder `trackEvent`-Aufruf hinzu, bevor Sie den Intent für den Start der Anwendung erstellen.

* Um den Kontext einer Aktion zu verfolgen, können Sie eine `ContextData`-Variable definieren, die die Option bietet, jede Aktion separat zu segmentieren (z. B. `AppExperienceType="widget"` statt `app`).

