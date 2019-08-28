---
description: Diese Informationen helfen Ihnen bei einer Anfrage auf Datenlöschung nach DSGVO.
seo-description: Diese Informationen helfen Ihnen bei einer Anfrage auf Datenlöschung nach DSGVO.
seo-title: Festlegen des Auswahlstatus eines Benutzers
solution: Marketing Cloud, Analytics
title: Festlegen des Auswahlstatus eines Benutzers
topic: Entwickler und Implementierung
uuid: 44 a 09 a 25-93 c 6-4 e 1 a-b 69 e -710018 e 8 b 6 c 3
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Setting the user's opt status {#setting-the-user-s-opt-status}

Diese Informationen helfen Ihnen bei einer Anfrage auf Datenlöschung nach DSGVO.

>[!IMPORTANT]
>
>Starting with Experience Cloud iOS SDKs 4.15, setting the privacy status to `unknown` holds Audience Manager and Experience Cloud ID hits.

Durch Verwendung der folgenden Einstellungen können Sie steuern, ob Aktivitäten von Analytics, Target und Audience Manager auf einem Gerät zulässig sind:

* `privacyDefault` in adbmobile [JSON Config](/help/ios/configuration/json-config/json-config.md).

   Diese Einstellung steuert die anfängliche Einstellung, die beibehalten wird, bis sie im Code geändert wird.

* `setPrivacyStatus` method.

   Nachdem die Datenschutzeinstellung mithilfe dieser Methode geändert wurde, ist die Änderung so lange dauerhaft, bis sie mithilfe dieser Methode erneut geändert wird oder wenn Sie die App deinstallieren und erneut installieren.

   Weitere Informationen zu den Methoden finden Sie unter [Konfigurationsmethoden](/help/ios/configuration/json-config/json-config.md).

Im Folgenden finden Sie Informationen zu den einzelnen Datenschutzstatus:

* **Opt-in**

   * Analytics: Treffer werden gesendet.
   * Target: Mbox-Anfragen werden gesendet.
   * Audience Manager: Signale und ID-Synchronisationen werden gesendet.
   * Value in the JSON config file: `optedin`
   * Wert in `setPrivacyStatus`: `ADBMobilePrivacyStatusOptIn`

* **Opt-out**

   * Analytics: Treffer werden verworfen.
   * Target: Mbox-Anfragen sind nicht zulässig.
   * Audience Manager: Signale und ID-Synchronisationen sind nicht zulässig.
   * Value in the JSON config file: `optedout`
   * Wert in `setPrivacyStatus`: `ADBMobilePrivacyStatusOptOut`

* **„Unbekannt“**

   * Analytics: Wenn die Offline-Verfolgung **aktiviert** ist, werden die Zugriffe gespeichert, bis der Datenschutzstatus zu „opt-in“ (Zugriffe werden dann gesendet) oder „opt-out“ (Zugriffe werden dann verworfen) geändert wird.

      Ist die Offline-Verfolgung **nicht aktiviert**, werden die Zugriffe verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird.

   * Target: Mbox-Anfragen werden gesendet.
   * Audience Manager: Signale und ID-Synchronisationen werden gesendet.
   * Value in the JSON config file: `optunknown`
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

