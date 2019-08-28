---
description: Sie können in Android-Anwendungen zielgerichtete Inhalte bereitstellen.
keywords: android; library; mobile; sdk
seo-description: Sie können in Android-Anwendungen zielgerichtete Inhalte bereitstellen.
seo-title: Target-Konfiguration
solution: Marketing Cloud, Analytics
title: Target-Konfiguration
topic: Entwickler und Implementierung
uuid: 09 fe 2 c 9 c -7 b 60-49 c 3-bb 9 d -36 a 30 ce 7 c 350
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
