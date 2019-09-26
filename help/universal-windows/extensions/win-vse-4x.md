---
description: Mit diesen Erweiterungen können Sie Ihrem Projekt viel einfacher eine Referenz auf Version 4.x des Windows-SDK für Experience Cloud-Lösungen hinzufügen.
seo-description: Mit diesen Erweiterungen können Sie Ihrem Projekt viel einfacher eine Referenz auf Version 4.x des Windows-SDK für Experience Cloud-Lösungen hinzufügen.
seo-title: Windows Visual Studio-Erweiterungen für Experience Cloud-Lösungen 4.x-SDK
solution: Marketing Cloud, Analytics
title: Windows Visual Studio-Erweiterungen für Experience Cloud-Lösungen 4.x-SDK
topic: Entwickler und Implementierung
uuid: e48faf54-8b08-4224-9d80-e553a983129e
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Windows Visual Studio extensions for Experience Cloud Solutions 4.x SDK {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

This extension provides a much easier way to add the reference of the Experience Cloud Solutions 4.x Windows SDK in your project.

## Bibliothek aus GitHub installieren {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Laden Sie das universelle Windows-SDK von [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) herunter.
1. Extrahieren Sie die heruntergeladene Datei lokal.
1. Doppelklicken Sie auf die Datei **[!UICONTRTOL ADBMobileUniversalWindowsVSIX.vsechs]** , um das Installationsprogramm zu öffnen.
1. Select Global Location and install the library.****

## Add references to your project {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Öffnen Sie Ihr Windows 10-Projekt.
1. Open the Reference Manager dialogue box.

   ![](assets/ref_manager.png)

1. On the Extensions tab, locate and select UICONTROL Adobe Mobile SDK.******[]**
1. Klicken Sie auf **[!UICONTROL OK]zum Speichern.**

   The Adobe Mobile SDK will be added to your project. If the UICONTROL Microsoft Visual C++ Runtime package has not yet been added, this package will also be added to your project.**[]**

1. In the Configuration Manager, select a a platform type and begin testing your app.

