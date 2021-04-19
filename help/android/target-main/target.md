---
description: Sie können in Android-Anwendungen zielgerichtete Inhalte bereitstellen.
keywords: Android;Bibliothek;Mobile;SDK
seo-description: Sie können in Android-Anwendungen zielgerichtete Inhalte bereitstellen.
seo-title: Target-Konfiguration
solution: Experience Cloud,Analytics
title: Target-Konfiguration
topic-fix: Developer and implementation
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
exl-id: dbcc3114-e76b-4b18-a418-ac46a21a593e
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '76'
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
