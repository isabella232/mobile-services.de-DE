---
description: Ab iOS 10 können Sie mit Apple eine Erweiterung erstellen, die als eigenständige Erweiterung bezeichnet wird und ohne eine übergeordnete App verteilt werden kann. Mit dieser Erweiterung benötigen Sie keine App-Gruppe, da es keine übergeordnete App gibt, mit der Daten geteilt werden können.
seo-description: Ab iOS 10 können Sie mit Apple eine Erweiterung erstellen, die als eigenständige Erweiterung bezeichnet wird und ohne eine übergeordnete App verteilt werden kann. Mit dieser Erweiterung benötigen Sie keine App-Gruppe, da es keine übergeordnete App gibt, mit der Daten geteilt werden können.
seo-title: Implementierung einer eigenständigen Erweiterung
solution: Experience Cloud,Analytics
title: Implementierung einer eigenständigen Erweiterung
topic: Developer and implementation
uuid: 9b47f082-b78f-4611-968d-014c32ede6bc
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 100%

---


# Implementierung einer eigenständigen Erweiterung {#stand-alone-extension-implementation}

Ab iOS 10 können Sie mit Apple eine Erweiterung erstellen, die als eigenständige Erweiterung bezeichnet wird und ohne eine übergeordnete App verteilt werden kann. Mit dieser Erweiterung benötigen Sie keine App-Gruppe, da es keine übergeordnete App gibt, mit der Daten geteilt werden können.

>[!IMPORTANT]
>
>Um eigenständige Erweiterungen zu nutzen, ist Mobile SDK Version 4.13.0 oder höher erforderlich.

## Konfigurieren Ihrer eigenständigen Erweiterung für die Verwendung mit dem SDK {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

So konfigurieren Sie Ihre eigenständige Erweiterung:

1. Stellen Sie sicher, dass die Datei `ADBMobileConfig.json` ein Mitglied des Ziels Ihrer Erweiterung ist.
1. Verknüpfen Sie die folgenden Bibliotheken und Frameworks:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. Legen Sie im Hauptansichtscontroller Ihrer Erweiterung den Erweiterungstyp im SDK auf `ADBMobileAppExtensionTypeStandAlone` fest, bevor Sie SDK-bezogene Aktivitäten abschließen.

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. Bestätigen Sie, dass Ihre App ohne unerwartete Fehler erstellt wird.

## Weitere Hinweise {#section_1C9A55E2309A44BF842310F735702B3D}

Zusätzliche Informationen:

* Ein zusätzlicher Kontextdatenwert mit dem Namen `a.RunMode` wurde hinzugefügt, um anzugeben, ob die Daten aus Ihrer übergeordneten App oder Ihrer Erweiterung stammen:

   * `a.RunMode = Application`

      Dieser Wert bedeutet, dass der Treffer aus der übergeordneten App stammt.
   * `a.RunMode = Extension`

      Dieser Wert bedeutet, dass der Treffer aus der Erweiterung stammt.

* Für iOS-Erweiterungs-Apps wird kein Lebenszyklusaufruf ausgelöst.

