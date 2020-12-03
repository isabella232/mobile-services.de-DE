---
description: Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten Experience Cloud SDK-Identitäten aus Ihrer iOS-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.
seo-description: Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten Experience Cloud SDK-Identitäten aus Ihrer iOS-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.
seo-title: Abrufen gespeicherter IDs
title: Abrufen gespeicherter IDs
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 69%

---


# Gespeicherte IDs abrufen{#retrieving-stored-identifiers}

Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten Experience Cloud SDK-Identitäten aus Ihrer iOS-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.

Weitere Informationen zu GDPR finden Sie unter [GDPR und Ihr Unternehmen](https://www.adobe.com/de/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>Die `getAllIdentifiersAsync`-Methode ruft IDs ab, die in den Experience Cloud-SDK gespeichert sind. You must call this method **before** the user opts-out.

Experience Cloud SDK-IDs (sofern zutreffend) werden lokal gespeichert und in einer JSON-Zeichenfolge zurückgegeben, die Folgendes enthalten kann:

* Firmeninformationen: IMS-Org-IDs
* Benutzer-IDs
* Experience Cloud ID (MID), vormals Experience Cloud ID
* Integrationscodes (HINZUFÜGEN, Push-ID)
* Datenquellen-IDs (DPID, DPUUID)
* Analytics-IDs (AVID, AID, VID und zugehörige RSIDs)
* Zielgruppe Legacy-IDs (TNTID, TNT3rdpartyID)
* Audience Manager-ID (UUID)

Im Folgenden finden Sie ein Beispiel der Methode `ADBMobile getAllIdentifiersAsync` für iOS:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```

