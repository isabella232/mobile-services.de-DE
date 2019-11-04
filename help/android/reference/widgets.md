---
description: Android-Widgets können über dieselben Methoden wie Apps verfolgt werden. Widgets haben denselben Anwendungskontext wie die App. Daher werden die Hit-Reihenfolge und die Besucheridentifizierung beibehalten.
keywords: Android;Bibliothek;Mobile;SDK
seo-description: Android-Widgets können über dieselben Methoden wie Apps verfolgt werden. Widgets haben denselben Anwendungskontext wie die App. Daher werden die Hit-Reihenfolge und die Besucheridentifizierung beibehalten.
seo-title: Android-Widgets
solution: Experience Cloud,Analytics
title: Android-Widgets
topic: Entwickler und Implementierung
uuid: 1a3718ff-967b-4c8e-ae0b-ba15bddbda0a
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Android-Widgets {#android-widgets}

Android-Widgets können über dieselben Methoden wie Apps verfolgt werden. Widgets haben denselben Anwendungskontext wie die App. Daher werden die Hit-Reihenfolge und die Besucheridentifizierung beibehalten.

Sie können Android-Widgets anhand der folgenden Richtlinien verfolgen:

* Implementieren Sie Aufrufe zu Lebenszyklusmetriken (`startActivity`/ `stopActivity`) im Widget.

* Fügen Sie einen `trackState`- oder `trackEvent`-Aufruf zur `onEnabled`-Methode eines Widgets hinzu, um aufzuzeichnen, wenn das Widget zum Startbildschirm hinzugefügt wird.

* Um aufzuzeichnen, wenn die App über ein Widget gestartet wird, fügen Sie einen `trackState`- oder `trackEvent`-Aufruf hinzu, bevor Sie den Intent für den Start der Anwendung erstellen.

* Um den Kontext einer Aktion zu verfolgen, können Sie eine `ContextData`-Variable definieren, die die Option bietet, jede Aktion separat zu segmentieren (z. B. `AppExperienceType="widget"` statt `app`).

