---
description: Im Folgenden finden Sie einige hilfreiche Informationen für die Konfiguration der Android-Erweiterung, mit deren Hilfe Sie Daten aus Ihrer Android Wearable App erfassen können.
seo-description: Im Folgenden finden Sie einige hilfreiche Informationen für die Konfiguration der Android-Erweiterung, mit deren Hilfe Sie Daten aus Ihrer Android Wearable App erfassen können.
seo-title: 'Android Wearables: Zusätzliche Hinweise'
solution: Experience Cloud,Analytics
title: 'Android Wearables: Zusätzliche Hinweise'
topic: Entwickler und Implementierung
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Android Wearables: Zusätzliche Hinweise{#android-wearables-additional-notes}

Im Folgenden finden Sie einige hilfreiche Informationen für die Konfiguration der Android-Erweiterung, mit deren Hilfe Sie Daten aus Ihrer Android Wearable App erfassen können.

* Die Adobe Mobile Android Wearables-Erweiterung erfordert Android-Version 4.4 (KitKat) oder höher.
* Es gibt nur einen zusätzlichen Kontextwert, `A.RunMode`, der hinzugefügt wurde, um anzuzeigen, ob die Daten aus der entsprechenden App oder von der Erweiterung stammen.

   * `RunMode` = `Application`

      Der Treffer kommt von der Handheld App.

   * `RunMode` = `Extension`

      Der Treffer kommt von der Wearable App.

* Das SDK synchronisiert den Status `aid`/`vid`/`visitor` `service id`/`privacy` automatisch zwischen Handheld App und Wearable App. Sie müssen `setPrivacyStatus`/`setUserIdentifier`/`idSync` also nicht in der Wearable App aufrufen.
* [In-App-Nachrichten](/help/android/messaging-main/messaging/messaging.md), [Target](/help/android/target-main/target.md) und [Audience Manager](/help/android/audience-manager/audiencemgmt.md) sind für die Wearable App deaktiviert.

