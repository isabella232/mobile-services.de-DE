---
description: Diese Erweiterungen bieten Ihnen eine wesentlich einfachere Möglichkeit, die Referenz zum Windows-SDK für Experience Cloud-Lösungen 4.x in Ihrem Projekt hinzuzufügen.
solution: Experience Cloud Services,Analytics
title: Windows Visual Studio-Erweiterungen für Experience Cloud-Lösungen mit SDK 4.x
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 14%

---

# Windows Visual Studio-Erweiterungen für Experience Cloud-Lösungen mit SDK 4.x {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Diese Erweiterung bietet eine wesentlich einfachere Möglichkeit, die Referenz des Windows-SDK für Experience Cloud-Lösungen 4.x in Ihr Projekt einzufügen.

## Bibliothek von GitHub installieren {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Laden Sie das universelle Windows-SDK von herunter. [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Dekomprimieren Sie die heruntergeladene Datei lokal.
1. Doppelklicken Sie auf die **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** -Datei, um das Installationsprogramm zu öffnen.
1. Auswählen **[!UICONTROL Globaler Standort]** und installieren Sie die Bibliothek.

## Hinzufügen von Referenzen zu Ihrem Projekt {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Öffnen Sie Ihr Windows 10-Projekt.
1. Öffnen Sie das Dialogfeld Referenz-Manager .

   ![](assets/ref_manager.png)

1. Im **[!UICONTROL Erweiterungen]** Registerkarte, suchen und auswählen **[!UICONTROL Adobe Mobile SDK]**.
1. Klicken **[!UICONTROL OK]** , um es zu speichern.

   Das Adobe Mobile SDK wird Ihrem Projekt hinzugefügt. Wenn die Variable **[!UICONTROL Microsoft Visual C++ Runtime]** -Paket noch nicht hinzugefügt wurde, wird dieses Paket auch zu Ihrem Projekt hinzugefügt.

1. Wählen Sie im Configuration Manager einen Plattformtyp aus und beginnen Sie mit dem Testen Ihrer App.
