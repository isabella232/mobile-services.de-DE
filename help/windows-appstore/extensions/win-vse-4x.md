---
description: Diese Erweiterungen bieten Ihnen eine wesentlich einfachere Möglichkeit, die Referenz zum Windows-SDK für Experience Cloud-Lösungen 4.x in Ihrem Projekt hinzuzufügen.
solution: Experience Cloud Services,Analytics
title: Windows Visual Studio-Erweiterungen für Experience Cloud-Lösungen mit SDK 4.x
topic-fix: Developer and implementation
uuid: 7d0ea312-340b-46ea-a737-b70a6766a536
exl-id: 63e9e5c7-2a12-47b3-a712-bf51e12821aa
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 13%

---

# Windows Visual Studio-Erweiterungen für Experience Cloud-Lösungen mit SDK 4.x {#windows-visual-studio-extensions-for-experience-cloud-solutions-x-sdk}

Diese Erweiterungen bieten Ihnen eine wesentlich einfachere Möglichkeit, die Referenz zum Windows-SDK für Experience Cloud-Lösungen 4.x in Ihrem Projekt hinzuzufügen.

## Bibliothek von GitHub installieren {#section_F55DB6241EF1475286C05FEAEBF996A3}

1. Laden Sie das universelle Windows-SDK von herunter. [GitHub](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases).
1. Dekomprimieren Sie die heruntergeladene Datei lokal.
1. Doppelklicken Sie auf die Datei ADBMobileWindowsStoreVSIX.vsix oder ADBMobileWindowsPhoneVSIX.vsix , um das Installationsprogramm zu öffnen.

1. Auswählen **[!UICONTROL Globaler Standort]** und installieren Sie die Bibliothek.

## Hinzufügen von Referenzen zu Ihrem Projekt {#section_00C14FE9243D4330BE1F4BB56FCF08B1}

1. Öffnen Sie Ihr Windows 8.1- oder Windows Phone 8.1-Projekt.
1. Öffnen Sie das Dialogfeld Referenz-Manager .

   ![](assets/ref_manager.png)

1. Im **[!UICONTROL Erweiterungen]** Registerkarte von Windows 8.1 oder Windows Phone 8.1, suchen und wählen Sie **[!UICONTROL Adobe Mobile SDK]**.
1. Klicken **[!UICONTROL OK]** , um es zu speichern.

   Das Adobe Mobile SDK wird Ihrem Projekt hinzugefügt. Wenn es noch nicht hinzugefügt wurde, wird die **[!UICONTROL Microsoft Visual C++ Runtime]** -Paket hinzugefügt.

1. Wählen Sie im Configuration Manager einen Platform-Typ aus und beginnen Sie mit dem Testen Ihrer App.
