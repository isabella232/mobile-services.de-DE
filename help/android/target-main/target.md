---
description: Sie können in Android-Anwendungen zielgerichtete Inhalte bereitstellen.
keywords: android;library;mobile;sdk
seo-description: Sie können in Android-Anwendungen zielgerichtete Inhalte bereitstellen.
seo-title: Target-Konfiguration
solution: Experience Cloud,Analytics
title: Target-Konfiguration
topic: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 100%

---


# Target-Konfiguration {#target-configuration}

Sie können in Android-Anwendungen zielgerichtete Inhalte bereitstellen.

## App-Kontext festlegen {#section_37CAE496FF894FCA821F7760605574CA}

**(Erforderlich)** Die Methode `setContext()` muss einmal in der Methode `onCreate()` der Hauptaktivität aufgerufen werden.

Beispiel:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Wenn Sie diesen Methodenaufruf bereits hinzugefügt haben, als Sie Analytics oder Zielgruppen-Management installiert haben, müssen Sie ihn nicht erneut hinzufügen.
