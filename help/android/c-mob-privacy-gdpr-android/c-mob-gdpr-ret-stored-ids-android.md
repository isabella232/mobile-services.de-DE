---
description: Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten SDK-Identitäten aus Ihrer Android-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.
title: Gespeicherte IDs abrufen
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
exl-id: 86c990d8-334b-4003-b0ac-d5404cb598e4
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 72%

---

# Gespeicherte IDs abrufen{#retrieving-stored-identifiers}

Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten SDK-Identitäten aus Ihrer Android-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.

>[!IMPORTANT]
>
>Die Methode `getAllIdentifiersAsync` ruft im SDK gespeicherte Identitäten ab. Sie müssen diese Methode **aufrufen, bevor** der Benutzer sich abmeldet.

SDK-Identitäten (sofern zutreffend) werden lokal gespeichert und in einer JSON-Zeichenfolge zurückgegeben, die Folgendes enthalten kann:

* Firmeninformationen: IMS-Org-IDs
* Benutzer-IDs
* Experience Cloud ID (MID), vormals Experience Cloud ID
* Integrationscodes (ADID, Push-ID)
* Datenquellen-IDs (DPID, DPUUID)
* Analytics-IDs (AVID, AID, VID und zugehörige RSIDs)
* Veraltete Target-IDs (TNTID, TNT3rdpartyID)
* Audience Manager-ID (UUID)

Im Folgenden finden Sie ein Beispiel der Methode `ADBMobile getAllIdentifiersAsync` für Android:

```java
Config.getAllIdentifiersAsync(new ConfigCallback<String>() { 
     @Override 
     public void call(String identitiesJson) {                 
         Log.d("ADBMobile Identities", identitiesJson); 
     } 
});
```
