---
description: Sie können über Zielgruppen-Management Signale senden und Besuchersegmente erhalten.
keywords: Android;Bibliothek;Mobile;SDK
seo-description: Sie können über Zielgruppen-Management Signale senden und Besuchersegmente erhalten.
seo-title: Audience Manager-Konfiguration
solution: Experience Cloud,Analytics
title: Audience Manager-Konfiguration
topic-fix: Developer and implementation
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
exl-id: 05033748-5461-482f-a01d-1ba73f64616a
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 100%

---

# Audience Manager-Konfiguration {#audience-manager-configuration}

Sie können über Audience Manager Signale senden und Besuchersegmente erhalten.

## App-Kontext festlegen {#section_37CAE496FF894FCA821F7760605574CA}

**(Erforderlich)** Die Methode `setContext()` muss einmal in der Methode `onCreate()` der Hauptaktivität aufgerufen werden.

Hier finden Sie ein Code-Beispiel für diese Methode:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Wenn Sie diesen Methodenaufruf hinzugefügt haben, als Sie Analytics oder Target installiert haben, müssen Sie ihn nicht erneut hinzufügen.
