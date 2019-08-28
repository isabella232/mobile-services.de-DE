---
description: Mithilfe dieser Informationen können Sie die Push-Dienst-Optionen beim Erstellen einer neuen App oder Bearbeiten einer bestehenden App auf der Seite „App-Einstellungen verwalten“ konfigurieren.
keywords: mobile
seo-description: Mithilfe dieser Informationen können Sie die Push-Dienst-Optionen beim Erstellen einer neuen App oder Bearbeiten einer bestehenden App auf der Seite „App-Einstellungen verwalten“ konfigurieren.
seo-title: Push-Benachrichtigung konfigurieren
solution: Marketing Cloud, Analytics
title: Push-Benachrichtigung konfigurieren
topic: Metriken
uuid: 6763858 d -6046-4 d 36-87 c 0-cf 3600 a 44 fb 1
translation-type: tm+mt
source-git-commit: 2c85c31d2fa54de26771553a6d349d3101e0048c

---


# Configure push messaging{#configure-push-messaging}

Mit diesen Informationen können Sie die Optionen für Push-Dienste auf der Seite App-Einstellungen verwalten beim Erstellen einer neuen App oder Bearbeiten einer bestehenden App konfigurieren.

Bevor Sie Push-Nachrichten konfigurieren, müssen Sie die erforderlichen Voraussetzungen erfüllen, um [Push-Nachrichten aktivieren](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md)zu können.

* **Hinweise zu Report Suites**

   Sie können pro Report Suite eine Appstore-App für Apple und eine für Google konfigurieren. Wenn Sie verschiedene Apps benötigen, z. B. eine für die Produktions- und eine andere für die Entwicklungsumgebung, richten Sie eine neue Appstore-App und eine neue Report Suite für jede Umgebung ein.

>[!IMPORTANT]
>
>Das Verschieben Ihrer App in eine neue Report Suite wird nicht unterstützt. Wenn Sie zu einer neuen Berichtssuite migrieren, kann Ihre Push-Konfiguration kaputt gehen und Nachrichten werden möglicherweise nicht gesendet.

1. Füllen Sie unter **[!UICONTROL Push-Dienste folgende Felder aus]**:

   * Apple

      **[!UICONTROL Privater Schlüssel]**

      Browse to and select your valid private key `.p12`, `.key`, or `.pen`.

      >[!IMPORTANT]
      >If the file that you select for the **[!UICONTROL Private Key]** input also contains a certificate, you do not need to specify the certificate.

   * **[!UICONTROL Zertifikat]**

      Geben Sie ein gültiges Zertifikat an. Diese Option ist erforderlich, wenn die Eingabe des **[!UICONTROL privaten Schlüssels]** **kein** Zertifikat enthält. Weitere Informationen zum Abrufen des SSL-Zertifikats und des privaten Schlüssels finden Sie unter [App für die Verwendung von APNS oder FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)konfigurieren.

   * Google

      **[!UICONTROL API-Schlüssel]**

      Geben Sie einen gültigen API-Schlüssel an. Weitere Informationen zum Abrufen des API-Schlüssels finden Sie unter [App für die Verwendung von APNS oder FCM](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-app-apns-gcm.md)konfigurieren.

      Weitere Informationen finden Sie in den folgenden Themen:

      * [Push-Nachrichten in Android](/help/android/messaging-main/push-messaging/push-messaging.md)
      * [Push-Nachrichten in ios](/help/ios/messaging-main/push-messaging/push-messaging.md)

1. Klicken Sie auf **[!UICONTROL Speichern]**.
