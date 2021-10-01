---
description: Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten Experience Cloud SDK-Identitäten aus Ihrer iOS-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.
title: Gespeicherte IDs abrufen
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
exl-id: ec8592af-fb08-4ab3-99a1-51ac5697a3d8
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 67%

---

# Gespeicherte IDs abrufen{#retrieving-stored-identifiers}

Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten Experience Cloud SDK-Identitäten aus Ihrer iOS-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.

Weitere Informationen zur DSGVO finden Sie unter [DSGVO und Ihr Unternehmen](https://www.adobe.com/de/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>Die `getAllIdentifiersAsync`-Methode ruft IDs ab, die in den Experience Cloud-SDK gespeichert sind. Sie müssen diese Methode **aufrufen, bevor** der Benutzer sich abmeldet.

Experience Cloud SDK-Identitäten (falls zutreffend) werden lokal gespeichert und in einer JSON-Zeichenfolge zurückgegeben, die Folgendes enthalten kann:

* Firmeninformationen: IMS-Org-IDs
* Benutzer-IDs
* Experience Cloud ID (MID), vormals Experience Cloud ID
* Integrationscodes (ADID, Push-ID)
* Datenquellen-IDs (DPID, DPUUID)
* Analytics-IDs (AVID, AID, VID und zugehörige RSIDs)
* Veraltete Target-IDs (TNTID, TNT3rdpartyID)
* Audience Manager-ID (UUID)

Im Folgenden finden Sie ein Beispiel der Methode `ADBMobile getAllIdentifiersAsync` für iOS:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```
