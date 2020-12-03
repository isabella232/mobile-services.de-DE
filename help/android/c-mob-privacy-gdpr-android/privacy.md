---
description: Diese Informationen helfen Ihnen bei einer Anfrage auf Datenlöschung nach DSGVO.
seo-description: Diese Informationen helfen Ihnen bei einer Anfrage auf Datenlöschung nach DSGVO.
seo-title: Auswahlstatus eines Benutzers festlegen
solution: Experience Cloud,Analytics
title: Auswahlstatus eines Benutzers festlegen
topic: Developer and implementation
uuid: f8a3e6be-44dd-494e-9cda-dbbac86d6772
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 100%

---


# Auswahlstatus eines Benutzers festlegen {#setting-the-user-s-opt-status}

Diese Informationen helfen Ihnen bei einer Anfrage auf Datenlöschung nach DSGVO.

>[!IMPORTANT]
>
>Ab Android-SDK 4.15 werden durch Festlegen des Datenschutzstatus auf `unknown` Treffer für Audience Manager- und Experience Cloud ID einbehalten.

Mithilfe der folgenden Einstellungen können Sie festlegen, ob die Analytics-, Target- oder Audience Manager-Aktivität auf dem jeweiligen Gerät zulässig ist:

* `privacyDefault` in der [ADBMobile JSON-Konfiguration](/help/android/configuration/json-config/json-config.md).

   Mit dieser Einstellung können Sie die anfängliche Einstellung festlegen, die beibehalten wird, bis sie im Code geändert wird.

* Die `Config.setPrivacyStatus`-Methode.

   Nachdem die Datenschutzeinstellung mithilfe dieser Methode geändert wurde, bleibt diese Änderung aktiv, bis Sie sie erneut ändern oder die App deinstallieren und erneut installieren. Weitere Informationen zu den Methoden finden Sie unter  [Konfigurationsmethoden](/help/android/configuration/methods.md).

Die folgende Tabelle beschreibt die einzelnen Datenschutzstatus:

* **Opt-in**

   * **Analytics**: Treffer werden gesendet.
   * **Target**: Mbox-Anfragen werden gesendet.
   * **Audience Manager**: Signale und ID-Synchronisationen werden gesendet.
   * Wert in der JSON-Konfigurationsdatei: `optedin`
   * Wert in `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_IN`

* **Opt-out**

   * **Analytics**: Treffer werden verworfen.
   * **Target**: Mbox-Anfragen sind nicht zulässig.
   * **Audience Manager**: Signale und ID-Synchronisationen sind nicht zulässig.
   * Wert in der JSON-Konfigurationsdatei: `optedout`
   * Wert in `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_OPT_OUT`

* **„Unbekannt“**

   * **Analytics**: Wenn die Offline-Verfolgung **aktiviert** ist, werden die Zugriffe gespeichert, bis der Datenschutzstatus zu „opt-in“ (Zugriffe werden dann gesendet) oder „opt-out“ (Zugriffe werden dann verworfen) geändert wird.

      Ist die Offline-Verfolgung <b>nicht aktiviert</b>, werden die Zugriffe verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird.
   * **Target**: Mbox-Anfragen werden gesendet.
   * **Audience Manager**: Signale und ID-Synchronisationen werden gesendet.
   * Wert in der JSON-Konfigurationsdatei: `optunknown`
   * Wert in `setPrivacyStatus`: `MOBILE_PRIVACY_STATUS_UNKNOWN`

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

