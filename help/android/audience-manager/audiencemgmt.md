---
description: Sie können über Zielgruppen-Management Signale senden und Besuchersegmente erhalten.
keywords: Android;Bibliothek;Mobile;SDK
solution: Experience Cloud Services,Analytics
title: Audience Manager-Konfiguration
topic-fix: Developer and implementation
uuid: f68d5b2e-fa2c-4db6-98ad-d1855a2c45ac
exl-id: 05033748-5461-482f-a01d-1ba73f64616a
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 100%

---

# Audience Manager-Konfiguration{#audience-manager-configuration}

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
