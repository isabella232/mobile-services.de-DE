---
description: Ab iOS 10 können Sie durch Apple eine als eigenständige Erweiterung bezeichnete Erweiterung erstellen, die ohne eine übergeordnete App verteilt werden kann. Mit dieser Erweiterung benötigen Sie keine App-Gruppe, da keine übergeordnete App vorhanden ist, für die Daten freigegeben werden müssen.
seo-description: Ab iOS 10 können Sie durch Apple eine als eigenständige Erweiterung bezeichnete Erweiterung erstellen, die ohne eine übergeordnete App verteilt werden kann. Mit dieser Erweiterung benötigen Sie keine App-Gruppe, da keine übergeordnete App vorhanden ist, für die Daten freigegeben werden müssen.
seo-title: Implementierung einer eigenständigen Erweiterung
solution: Marketing Cloud, Analytics
title: Implementierung einer eigenständigen Erweiterung
topic: Entwickler und Implementierung
uuid: 9 b 47 f 082-b 78 f -4611-968 d -014 c 32 ede 6 bc
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Stand-alone extension implementation {#stand-alone-extension-implementation}

Ab iOS 10 können Sie durch Apple eine als eigenständige Erweiterung bezeichnete Erweiterung erstellen, die ohne eine übergeordnete App verteilt werden kann. Mit dieser Erweiterung benötigen Sie keine App-Gruppe, da keine übergeordnete App vorhanden ist, für die Daten freigegeben werden müssen.

>[!IMPORTANT]
>
>Für die Verwendung eigenständiger Erweiterungen muss Mobile SDK Version 4.13.0 oder höher verwendet werden.

## Konfigurieren Ihrer eigenständigen Erweiterung für die Verwendung mit dem SDK {#section_B7A84603BB9D4B48BB46BE8D3B9E3CF0}

So konfigurieren Sie Ihre eigenständige Erweiterung:

1. Ensure that the `ADBMobileConfig.json` file is a member of your extension's target.
1. Verknüpfen Sie die folgenden Bibliotheken und Frameworks:

   * `AdobeMobileLibrary_Extension.a`
   * `libsqlite3.tbd`
   * `SystemConfiguration.framework`

1. Legen Sie im Hauptansichtscontroller Ihrer Erweiterung den Erweiterungstyp im SDK auf `ADBMobileAppExtensionTypeStandAlone` fest, bevor Sie SDK-bezogene Aktivitäten abschließen.

   ```objective-c
   [ADBMobile setAppExtensionType:ADBMobileAppExtensionTypeStandAlone];
   ```

1. Bestätigen Sie, dass Ihre App ohne unerwartete Fehler erstellt wird.

## Additional notes {#section_1C9A55E2309A44BF842310F735702B3D}

Zusätzliche Informationen:

* Ein zusätzlicher Kontextdatenwert mit dem Namen `a.RunMode` wurde hinzugefügt, um anzugeben, ob die Daten aus Ihrer übergeordneten App oder Ihrer Erweiterung stammen:

   * `a.RunMode = Application`

      Dieser Wert bedeutet, dass der Treffer aus der übergeordneten App stammt.
   * `a.RunMode = Extension`

      Dieser Wert bedeutet, dass der Treffer aus der Erweiterung stammt.

* Für iOS-Erweiterungs-Apps wird kein Lebenszyklusaufruf ausgelöst.

