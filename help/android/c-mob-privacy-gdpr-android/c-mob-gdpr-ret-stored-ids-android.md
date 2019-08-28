---
description: Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten SDK-Identitäten aus Ihrer Android-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.
seo-description: Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten SDK-Identitäten aus Ihrer Android-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.
seo-title: Abrufen gespeicherter Bezeichner
title: Abrufen gespeicherter Bezeichner
uuid: 6 fd 3 d 202-b 0 a 1-4 c 80-96 f 4-369 fc 24 ac 0 a 3
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Retrieving stored identifiers{#retrieving-stored-identifiers}

Diese Informationen helfen Ihnen beim Abrufen von lokal gespeicherten SDK-Identitäten aus Ihrer Android-Anwendung sowie bei Anfragen auf Datenzugriff nach DSGVO.

>[!IMPORTANT]
>
>The `getAllIdentifiersAsync` method retrieves identities stored in the SDK. Diese Methode muss **vor** dem Opt-out des Benutzers aufgerufen werden.

SDK-Identitäten (falls anwendbar) werden lokal gespeichert und in einer JSON-Zeichenfolge zurückgegeben, die Folgendes enthalten kann:

* Unternehmenskontext – IMS-Org-ID
* Anwender-IDs
* Experience Cloud ID (MID), vormals Marketing Cloud ID
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
