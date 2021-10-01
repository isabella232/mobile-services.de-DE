---
description: Diese Erweiterungen bieten Ihnen eine wesentlich einfachere Möglichkeit, die Referenz zum Windows-SDK für Experience Cloud-Lösungen 4.x in Ihrem Projekt hinzuzufügen.
solution: Experience Cloud,Analytics
title: Windows Visual Studio-Erweiterungen für Experience Cloud-Lösungen mit SDK 4.x
topic-fix: Developer and implementation
uuid: e48faf54-8b08-4224-9d80-e553a983129e
exl-id: 8ed91dc1-8f30-4788-8471-21bb54256b0b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 14%

---

# Windows Visual Studio-Erweiterungen für Experience Cloud-Lösungen mit SDK 4.x {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Diese Erweiterung bietet eine wesentlich einfachere Möglichkeit, die Referenz des Windows-SDK für Experience Cloud-Lösungen 4.x in Ihr Projekt einzufügen.

## Bibliothek von GitHub installieren {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Laden Sie das universelle Windows-SDK von [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) herunter.
1. Dekomprimieren Sie die heruntergeladene Datei lokal.
1. Doppelklicken Sie auf die Datei **[!UICONTROL ADBMobileUniversalWindowsVSIX.vsix]** , um das Installationsprogramm zu öffnen.
1. Wählen Sie **[!UICONTROL Global Location]** aus und installieren Sie die Bibliothek.

## Hinzufügen von Referenzen zu Ihrem Projekt {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Öffnen Sie Ihr Windows 10-Projekt.
1. Öffnen Sie das Dialogfeld Referenz-Manager .

   ![](assets/ref_manager.png)

1. Suchen Sie auf der Registerkarte **[!UICONTROL Erweiterungen]** die Option **[!UICONTROL Adobe Mobile SDK]** und wählen Sie sie aus.
1. Klicken Sie auf **[!UICONTROL OK]**, um sie zu speichern.

   Das Adobe Mobile SDK wird Ihrem Projekt hinzugefügt. Wenn das Paket **[!UICONTROL Microsoft Visual C++ Runtime]** noch nicht hinzugefügt wurde, wird dieses Paket auch zu Ihrem Projekt hinzugefügt.

1. Wählen Sie im Configuration Manager einen Plattformtyp aus und beginnen Sie mit dem Testen Ihrer App.
