---
description: Sie können über Zielgruppen-Management Signale senden und Besuchersegmente erhalten.
keywords: android; library; mobile; sdk
seo-description: Sie können über Zielgruppen-Management Signale senden und Besuchersegmente erhalten.
seo-title: Audience Manager-Konfiguration
solution: Marketing Cloud, Analytics
title: Audience Manager-Konfiguration
topic: Entwickler und Implementierung
uuid: f 68 d 5 b 2 e-fa 2 c -4 db 6-98 ad-d 1855 a 2 c 45 ac
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# Audience Manager configuration{#audience-manager-configuration}

Sie können Signale senden und Besuchersegmente aus Audience Manager abrufen.

## Set the application context {#section_37CAE496FF894FCA821F7760605574CA}

**(Erforderlich)** Die `setContext()` Methode muss einmal in der `onCreate()` Methode Ihrer Hauptaktivität aufgerufen werden.

Hier finden Sie ein Code-Beispiel für diese Methode:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
  super.onCreate(savedInstanceState); 
  setContentView(R.layout.main); 
  Config.setContext(this.getApplicationContext()); 
}
```

Wenn Sie diesen Methodenaufruf bei Implementierung von Analytics oder Target hinzugefügt haben, müssen Sie ihn nicht erneut hinzufügen.
