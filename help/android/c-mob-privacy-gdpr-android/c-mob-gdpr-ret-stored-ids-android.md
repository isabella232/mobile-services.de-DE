---
description: Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten SDK-Identitäten aus Ihrer Android-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.
seo-description: Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten SDK-Identitäten aus Ihrer Android-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.
seo-title: Gespeicherte IDs abrufen
title: Gespeicherte IDs abrufen
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 76%

---


# Gespeicherte IDs abrufen{#retrieving-stored-identifiers}

Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten SDK-Identitäten aus Ihrer Android-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.

>[!IMPORTANT]
>
>Die Methode `getAllIdentifiersAsync` ruft im SDK gespeicherte Identitäten ab. You must call this method **before** the user opts-out.

SDK-IDs (sofern zutreffend) werden lokal gespeichert und in einer JSON-Zeichenfolge zurückgegeben, die Folgendes enthalten kann:

* Firmeninformationen: IMS-Org-IDs
* Benutzer-IDs
* Experience Cloud ID (MID), vormals Experience Cloud ID
* Integrationscodes (HINZUFÜGEN, Push-ID)
* Datenquellen-IDs (DPID, DPUUID)
* Analytics-IDs (AVID, AID, VID und zugehörige RSIDs)
* Zielgruppe Legacy-IDs (TNTID, TNT3rdpartyID)
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
