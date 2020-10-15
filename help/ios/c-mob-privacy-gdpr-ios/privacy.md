---
description: Diese Informationen helfen Ihnen bei einer Anfrage auf Datenlöschung nach DSGVO.
seo-description: Diese Informationen helfen Ihnen bei einer Anfrage auf Datenlöschung nach DSGVO.
seo-title: Auswahlstatus eines Benutzers festlegen
solution: Experience Cloud,Analytics
title: Auswahlstatus eines Benutzers festlegen
topic: Developer and implementation
uuid: 44a09a25-93c6-4e1a-b69e-710018e8b6c3
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '270'
ht-degree: 100%

---


# Auswahlstatus eines Benutzers festlegen {#setting-the-user-s-opt-status}

Diese Informationen helfen Ihnen bei einer Anfrage auf Datenlöschung nach DSGVO.

>[!IMPORTANT]
>
>Ab den Experience Cloud iOS-SDK Version 4.15 werden durch Festlegen des Datenschutzstatus auf `unknown` Treffer für Audience Manager- und Experience Cloud ID einbehalten.

Durch Verwendung der folgenden Einstellungen können Sie steuern, ob Aktivitäten von Analytics, Target und Audience Manager auf einem Gerät zulässig sind:

* `privacyDefault` in der [ADBMobile JSON-Konfiguration](/help/ios/configuration/json-config/json-config.md).

   Diese Einstellung steuert die anfängliche Einstellung, die beibehalten wird, bis sie im Code geändert wird.

* `setPrivacyStatus` method.

   Nachdem die Datenschutzeinstellung mithilfe dieser Methode geändert wurde, ist die Änderung so lange dauerhaft, bis sie mithilfe dieser Methode erneut geändert wird, oder wenn Sie die App deinstallieren und erneut installieren.

   Weitere Informationen zu den Methoden finden Sie unter  [Konfigurationsmethoden](/help/ios/configuration/json-config/json-config.md).

Hier finden Sie Informationen zu den einzelnen Datenschutzstatus:

* **Opt-in**

   * Analytics: Treffer werden gesendet.
   * Target: Mbox-Anfragen werden gesendet.
   * Audience Manager: Signale und ID-Synchronisationen werden gesendet.
   * Wert in der JSON-Konfigurationsdatei: `optedin`
   * Wert in `setPrivacyStatus`: `ADBMobilePrivacyStatusOptIn`

* **Opt-out**

   * Analytics: Treffer werden verworfen.
   * Target: Mbox-Anfragen sind nicht zulässig.
   * Audience Manager: Signale und ID-Synchronisationen sind nicht zulässig.
   * Wert in der JSON-Konfigurationsdatei: `optedout`
   * Wert in `setPrivacyStatus`: `ADBMobilePrivacyStatusOptOut`

* **„Unbekannt“**

   * Analytics: Wenn die Offline-Verfolgung **aktiviert** ist, werden die Zugriffe gespeichert, bis der Datenschutzstatus zu „opt-in“ (Zugriffe werden dann gesendet) oder „opt-out“ (Zugriffe werden dann verworfen) geändert wird.

      Ist die Offline-Verfolgung **nicht aktiviert**, werden die Zugriffe verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird.

   * Target: Mbox-Anfragen werden gesendet.
   * Audience Manager: Signale und ID-Synchronisationen werden gesendet.
   * Wert in der JSON-Konfigurationsdatei: `optunknown`
   * Wert in `setPrivacyStatus`: `ADBMobilePrivacyStatusUnknown`

## Beispiele {#section_128AC455EE024193B5D4E5A565B53D00}

```objective-c
- (IBAction) setPrivacyOptIn { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptIn]; 
} 
- (IBAction) setPrivacyOptOut { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusOptOut]; 
} 
- (IBAction) setPrivacyOptUnknown { 
 [ADBMobile setPrivacyStatus:ADBMobilePrivacyStatusUnknown]; 
}
```

