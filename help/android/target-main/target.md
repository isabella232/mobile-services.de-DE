---
description: Sie können in Android-Anwendungen zielgerichtete Inhalte bereitstellen.
keywords: android;library;mobile;sdk
seo-description: Sie können in Android-Anwendungen zielgerichtete Inhalte bereitstellen.
seo-title: Target configuration
solution: Marketing Cloud, Analytics
title: Zielkonfiguration
topic: Entwickler und Implementierung
uuid: 09fe2c9c-7b60-49c3-bb9d-36a30ce7c350
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Target configuration {#target-configuration}

Sie können in Android-Anwendungen zielgerichtete Inhalte bereitstellen.

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**(Erforderlich)** Die `setContext()` Methode muss einmal in der `onCreate()` Methode Ihrer Hauptaktivität aufgerufen werden.

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
