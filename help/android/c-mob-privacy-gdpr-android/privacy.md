---
description: Diese Informationen helfen Ihnen bei einer Anfrage auf Datenlöschung nach DSGVO.
seo-description: Diese Informationen helfen Ihnen bei einer Anfrage auf Datenlöschung nach DSGVO.
seo-title: Festlegen des Opt-Status des Benutzers
solution: Marketing Cloud, Analytics
title: Festlegen des Opt-Status des Benutzers
topic: Entwickler und Implementierung
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Setting the user's opt status{#setting-the-user-s-opt-status}

Diese Informationen helfen Ihnen bei einer Anfrage auf Datenlöschung nach DSGVO.

>[!IMPORTANT]
>
>Starting with Android SDK 4.15 , setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

Mithilfe der folgenden Einstellungen können Sie festlegen, ob die Analytics-, Target- oder Audience Manager-Aktivität auf dem jeweiligen Gerät zulässig ist:

* `privacyDefault` in ADBMobile JSON Config.[](/help/android/configuration/json-config/json-config.md)

   Mit dieser Einstellung können Sie die anfängliche Einstellung festlegen, die beibehalten wird, bis sie im Code geändert wird.

* The  method.`Config.setPrivacyStatus`

   Nachdem die Datenschutzeinstellung mithilfe dieser Methode geändert wurde, bleibt diese Änderung aktiv, bis Sie sie erneut ändern oder die App deinstallieren und erneut installieren. Weitere Informationen zu den Methoden finden Sie unter [Konfigurationsmethoden](/help/android/configuration/methods.md).

Die folgende Tabelle beschreibt die einzelnen Datenschutzstatus:

* **Opt-in**

   * **Analytics**: Treffer werden gesendet.
   * **Target**: Mbox-Anfragen werden gesendet.
   * **Audience Manager**: Signale und ID-Synchronisationen werden gesendet.
   * Value in the JSON Config file: `optedin`
   * Value in : `setPrivacyStatus``MOBILE_PRIVACY_STATUS_OPT_IN`

* **Opt-out**

   * **Analytics**: Treffer werden verworfen.
   * **Target**: Mbox-Anfragen sind nicht zulässig.
   * **Audience Manager**: Signale und ID-Synchronisationen sind nicht zulässig.
   * Value in the JSON config file: `optedout`
   * Value in : `setPrivacyStatus``MOBILE_PRIVACY_STATUS_OPT_OUT`

* **„Unbekannt“**

   * **Analytics**: Wenn die Offline-Verfolgung **aktiviert** ist, werden die Treffer gespeichert, bis der Datenschutzstatus in "opt-in"(Treffer werden gesendet) oder "opt-out"(Treffer werden verworfen) geändert wird.

      Ist die Offline-Verfolgung <b>nicht aktiviert</b>, werden die Zugriffe verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird.
   * **Target**: Mbox-Anfragen werden gesendet.
   * **Audience Manager**: Signale und ID-Synchronisationen werden gesendet.
   * Value in the JSON config file: `optunknown`
   * Value in : `setPrivacyStatus``MOBILE_PRIVACY_STATUS_UNKNOWN`

## Beispiele {#section_128AC455EE024193B5D4E5A565B53D00}

```java
public void setOptIn(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_IN); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptOut(View view) { 
 Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_OPT_OUT); 
 currentStatus = Config.getPrivacyStatus(); 
} 
public void setOptUnknown(View view) { 
  Config.setPrivacyStatus(MobilePrivacyStatus.MOBILE_PRIVACY_STATUS_UNKNOWN); 
 currentStatus = Config.getPrivacyStatus(); 
}
```

