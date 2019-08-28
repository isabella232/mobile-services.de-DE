---
description: Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten Experience Cloud SDK-Identitäten aus Ihrer iOS-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.
seo-description: Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten Experience Cloud SDK-Identitäten aus Ihrer iOS-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.
seo-title: Abrufen von gespeicherten Kennungen
title: Abrufen von gespeicherten Kennungen
uuid: 4 fb 2 c 166-6700-4 f 8 b-b 60 b -137 b 199 e 0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Retrieving stored identifiers{#retrieving-stored-identifiers}

Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten Experience Cloud SDK-Identitäten aus Ihrer iOS-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.

Weitere Informationen über die DSGVO finden Sie in unserem Artikel über die [DSGVO und Ihr Unternehmen](https://www.adobe.com/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>Die `getAllIdentifiersAsync` Methode ruft Identitäten ab, die in den Experience Cloud sdks gespeichert werden. Diese Methode muss **vor** dem Opt-out des Benutzers aufgerufen werden.

Experience Cloud SDK-Identitäten (falls anwendbar) werden lokal gespeichert und in einer JSON-Zeichenfolge zurückgegeben, die Folgendes enthalten kann:

* Unternehmenskontext – IMS-Org-ID
* Anwender-IDs
* Experience Cloud ID (MID), vormals Marketing Cloud ID
* Integrationscodes (ADID, Push-ID)
* Datenquellen-IDs (DPID, DPUUID)
* Analytics-IDs (AVID, AID, VID und verbundene RSIDs)
* Ältere Target-IDs (TNTID, TNT3rdpartyID)
* Audience Manager-ID (UUID)

Im Folgenden finden Sie ein Beispiel der Methode `ADBMobile getAllIdentifiersAsync` für iOS:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

