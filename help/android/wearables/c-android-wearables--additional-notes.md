---
description: Im Folgenden finden Sie einige Informationen zum Konfigurieren der Android-Erweiterung, mit der Sie Daten aus Ihrer Android Wearable-App erfassen können.
seo-description: Im Folgenden finden Sie einige Informationen zum Konfigurieren der Android-Erweiterung, mit der Sie Daten aus Ihrer Android Wearable-App erfassen können.
seo-title: 'Android Wearables: Zusätzliche Hinweise'
solution: Experience Cloud,Analytics
title: 'Android Wearables: Zusätzliche Hinweise'
topic: Developer and implementation
uuid: 3bcf352b-4d46-4ab3-81ec-c27e86fe9be3
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '161'
ht-degree: 100%

---


# Android Wearables: Zusätzliche Hinweise {#android-wearables-additional-notes}

Im Folgenden finden Sie einige Informationen zum Konfigurieren der Android-Erweiterung, mit der Sie Daten aus Ihrer Android Wearable-App erfassen können.

* Für die Adobe Mobile Android Wearables-Erweiterung ist Android-Version 4.4 (KitKat) oder höher erforderlich.
* Es gibt nur einen zusätzlichen Kontextwert, `A.RunMode`, der hinzugefügt wurde, um anzuzeigen, ob die Daten aus der entsprechenden App oder von der Erweiterung stammen.

   * `RunMode` = `Application`

      Der Treffer kommt von der Handheld App.

   * `RunMode` = `Extension`

      Der Treffer kommt von der Wearable App.

* Das SDK synchronisiert den Status `aid`/`vid`/`visitor` `service id`/`privacy` automatisch zwischen Handheld App und Wearable App. Sie müssen `setPrivacyStatus`/`setUserIdentifier`/`idSync` also nicht in der Wearable App aufrufen.
* [In-App-Nachrichten](/help/android/messaging-main/messaging/messaging.md), [Target](/help/android/target-main/target.md) und [Audience Manager](/help/android/audience-manager/audiencemgmt.md) sind für die Wearable App deaktiviert.

