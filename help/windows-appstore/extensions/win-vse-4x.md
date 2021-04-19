---
description: Diese Erweiterungen bieten Ihnen eine wesentlich einfachere Möglichkeit, die Referenz des Windows SDK für Experience Cloud Solutions 4.x in Ihr Projekt einzufügen.
seo-description: Diese Erweiterungen bieten Ihnen eine wesentlich einfachere Möglichkeit, die Referenz des Windows SDK für Experience Cloud Solutions 4.x in Ihr Projekt einzufügen.
seo-title: Windows Visual Studio-Erweiterungen für Experience Cloud-Lösungen mit SDK 4.x
solution: Experience Cloud,Analytics
title: Windows Visual Studio-Erweiterungen für Experience Cloud-Lösungen mit SDK 4.x
topic-fix: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
exl-id: 63e9e5c7-2a12-47b3-a712-bf51e12821aa
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 16%

---

# Windows Visual Studio-Erweiterungen für Experience Cloud-Lösungen mit SDK 4.x {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Diese Erweiterungen bieten Ihnen eine wesentlich einfachere Möglichkeit, die Referenz des Windows SDK für Experience Cloud Solutions 4.x in Ihr Projekt einzufügen.

## Bibliothek aus GitHub {#section_F55DB6241EF1475286C05FEAEBF996A3} installieren

1. Laden Sie das Windows Universal SDK von [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) herunter.
1. Dekomprimieren Sie die heruntergeladene Datei lokal.
1. Klicken Sie bei gedrückter Dublette auf die Datei ADBMobileWindowsStoreVSIX.vsechs oder ADBMobileWindowsPhoneVSIX.vsechsf, um das Installationsprogramm zu öffnen.

1. Wählen Sie **[!UICONTROL Globaler Speicherort]** und installieren Sie die Bibliothek.

## hinzufügen Verweise auf Ihr Projekt {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Öffnen Sie das Windows 8.1- oder Windows Phone 8.1-Projekt.
1. Öffnen Sie das Dialogfeld &quot;Referenz-Manager&quot;.

   ![](assets/ref_manager.png)

1. Suchen Sie auf der Registerkarte **[!UICONTROL Erweiterungen]** von Windows 8.1 oder Windows Phone 8.1 nach **[!UICONTROL Adobe Mobile SDK]** und wählen Sie es aus.
1. Klicken Sie auf **[!UICONTROL OK]**, um es zu speichern.

   Das Adobe Mobile SDK wird Ihrem Projekt hinzugefügt. Wenn es noch nicht hinzugefügt wurde, wird auch das **[!UICONTROL Microsoft Visual C++ Runtime]**-Paket hinzugefügt.

1. Wählen Sie im Configuration Manager einen Plattformtyp und beginnen Sie mit dem Testen der App.
