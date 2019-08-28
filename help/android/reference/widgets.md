---
description: Android-Widgets können über dieselben Methoden wie Apps verfolgt werden. Widgets haben denselben Anwendungskontext wie die App. Daher werden die Hit-Reihenfolge und die Besucheridentifizierung beibehalten.
keywords: android; library; mobile; sdk
seo-description: Android-Widgets können über dieselben Methoden wie Apps verfolgt werden. Widgets haben denselben Anwendungskontext wie die App. Daher werden die Hit-Reihenfolge und die Besucheridentifizierung beibehalten.
seo-title: Android-Widgets
solution: Marketing Cloud, Analytics
title: Android-Widgets
topic: Entwickler und Implementierung
uuid: 1 a 3718 ff -967 b -4 c 8 e-ae 0 b-ba 15 bddbda 0 a
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Android widgets {#android-widgets}

Android-Widgets können über dieselben Methoden wie Apps verfolgt werden. Widgets haben denselben Anwendungskontext wie die App. Daher werden die Hit-Reihenfolge und die Besucheridentifizierung beibehalten.

Sie können Android-Widgets anhand der folgenden Richtlinien verfolgen:

* Do not implement lifecycle metrics ( `startActivity`/ `stopActivity`) calls in the widget.

* Fügen Sie einen `trackState`- oder `trackEvent`-Aufruf zur `onEnabled`-Methode eines Widgets hinzu, um aufzuzeichnen, wenn das Widget zum Startbildschirm hinzugefügt wird.

* Um aufzuzeichnen, wenn die App über ein Widget gestartet wird, fügen Sie einen `trackState`- oder `trackEvent`-Aufruf hinzu, bevor Sie den Intent für den Start der Anwendung erstellen.

* To track the context of an action, you can define a `ContextData` variable that provides the option to segment each action separately (for example, `AppExperienceType="widget"` vs. `app`).

