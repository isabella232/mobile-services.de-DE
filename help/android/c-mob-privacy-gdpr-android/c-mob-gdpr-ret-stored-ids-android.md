---
description: Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten SDK-Identitäten aus Ihrer Android-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.
seo-description: Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten SDK-Identitäten aus Ihrer Android-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.
seo-title: Gespeicherte IDs abrufen
title: Gespeicherte IDs abrufen
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
translation-type: ht
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Gespeicherte IDs abrufen{#retrieving-stored-identifiers}

Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten SDK-Identitäten aus Ihrer Android-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.

>[!IMPORTANT]
>
>Die Methode `getAllIdentifiersAsync` ruft im SDK gespeicherte Identitäten ab. Diese Methode muss **vor** dem Opt-out des Benutzers aufgerufen werden.

SDK-Identitäten (falls anwendbar) werden lokal gespeichert und in einer JSON-Zeichenfolge zurückgegeben, die Folgendes enthalten kann:

* Unternehmenskontext – IMS-Org-ID
* Anwender-IDs
* Experience Cloud ID (MID), vormals Experience Cloud ID
* Integrationscodes (ADID, Push-ID)
* Datenquellen-IDs (DPID, DPUUID)
* Analytics-IDs (AVID, AID, VID und verbundene RSIDs)
* Ältere Target-IDs (TNTID, TNT3rdpartyID)
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
