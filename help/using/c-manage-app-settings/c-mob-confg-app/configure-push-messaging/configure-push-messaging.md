---
description: Mithilfe dieser Informationen können Sie die Push-Dienst-Optionen beim Erstellen einer neuen App oder Bearbeiten einer bestehenden App auf der Seite „App-Einstellungen verwalten“ konfigurieren.
keywords: mobile
seo-description: Mithilfe dieser Informationen können Sie die Push-Dienst-Optionen beim Erstellen einer neuen App oder Bearbeiten einer bestehenden App auf der Seite „App-Einstellungen verwalten“ konfigurieren.
seo-title: Push-Benachrichtigung konfigurieren
solution: Experience Cloud,Analytics
title: Push-Benachrichtigung konfigurieren
topic: Metrics
uuid: 6763858d-6046-4d36-87c0-cf3600a44fb1
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '318'
ht-degree: 100%

---


# Push-Benachrichtigung konfigurieren {#configure-push-messaging}

Mithilfe dieser Informationen können Sie die Push-Dienst-Optionen beim Erstellen einer neuen App oder Bearbeiten einer bestehenden App auf der Seite „App-Einstellungen verwalten“ konfigurieren.

Führen Sie vor dem Konfigurieren von Push-Nachrichten die unter [Voraussetzungen für die Aktivierung der Push-Benachrichtigung](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md) erforderlichen Aufgaben aus.

* **Überlegungen zur Report Suite**

   Sie können in jeder Report Suite eine App-Store-App für Apple und eine für Google konfigurieren. Wenn Sie zusätzliche Apps benötigen, z. B. eine für eine Produktionsumgebung und eine für eine Entwicklungsumgebung, richten Sie für jede Umgebung eine neue App-Store-App und eine neue Report Suite ein.

>[!IMPORTANT]
>
>Das Verschieben Ihrer App in eine neue Report Suite wird nicht unterstützt. Wenn Sie zu einer neuen Berichtssuite migrieren, kann Ihre Push-Konfiguration kaputt gehen und Nachrichten werden möglicherweise nicht gesendet.

1. Füllen Sie unter **[!UICONTROL Push-Dienste]** folgende Felder aus:

   * Apple

      **[!UICONTROL Privater Schlüssel]**

      Suchen Sie nach dem gültigen privaten Schlüssel (`.p12`, `.key` oder `.pen`) und wählen Sie ihn aus.

      >[!IMPORTANT]
      >Wenn die für die Eingabe des **[!UICONTROL privaten Schlüssels]** ausgewählte Datei auch ein Zertifikat enthält, müssen Sie das Zertifikat nicht angeben.

   * **[!UICONTROL Zertifikat]**

      Geben Sie ein gültiges Zertifikat an. Diese Option ist erforderlich, wenn die Eingabe des **[!UICONTROL privaten Schlüssels]** **kein** Zertifikat enthält. Weitere Informationen zum Abrufen des SSL-Zertifikats und des privaten Schlüssels finden Sie in [App für die Verwendung von APNS oder FCM konfigurieren](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

   * Google

      **[!UICONTROL API-Schlüssel]**

      Geben Sie einen gültigen API-Schlüssel an. Weitere Informationen zum Abrufen des API-Schlüssels finden Sie in [App für die Verwendung von APNS oder FCM konfigurieren](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md).

      Weitere Informationen finden Sie in den folgenden Themen:

      * [Push-Nachrichten in Android](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [Push-Nachrichten in iOS](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. Klicken Sie auf **[!UICONTROL Speichern]**.
