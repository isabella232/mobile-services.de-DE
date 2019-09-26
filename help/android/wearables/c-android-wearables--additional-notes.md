---
description: Im Folgenden finden Sie einige hilfreiche Informationen für die Konfiguration der Android-Erweiterung, mit deren Hilfe Sie Daten aus Ihrer Android Wearable App erfassen können.
seo-description: Im Folgenden finden Sie einige hilfreiche Informationen für die Konfiguration der Android-Erweiterung, mit deren Hilfe Sie Daten aus Ihrer Android Wearable App erfassen können.
seo-title: Weitere Hinweise zu Android Wearns
solution: Marketing Cloud,Analytics
title: Android Wearables  Additional Notes
topic: Entwickler und Implementierung
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: additional notes{#android-wearables-additional-notes}

Im Folgenden finden Sie einige hilfreiche Informationen für die Konfiguration der Android-Erweiterung, mit deren Hilfe Sie Daten aus Ihrer Android Wearable App erfassen können.

* Die Adobe Mobile Android Wearables-Erweiterung erfordert Android-Version 4.4 (KitKat) oder höher.
* Es gibt nur einen zusätzlichen Kontextwert, `A.RunMode`, der hinzugefügt wurde, um anzuzeigen, ob die Daten aus der entsprechenden App oder von der Erweiterung stammen.

   * `RunMode` = `Application`

      Der Treffer kommt von der Handheld-App.

   * `RunMode` = `Extension`

      Der Treffer kommt von der tragbaren App.

* The SDK automatically syncs the `aid`/`vid`/`visitor` `service id`/`privacy` status from the handheld app to the wearable app, so do not call `setPrivacyStatus`/`setUserIdentifier`/`idSync` from the wearable app.
* [In-App-Nachrichten](/help/android/messaging-main/messaging/messaging.md), [Target](/help/android/target-main/target.md)und [Audience Manager](/help/android/audience-manager/audiencemgmt.md) sind für die tragbare App deaktiviert.

