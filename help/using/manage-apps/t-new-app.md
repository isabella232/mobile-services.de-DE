---
description: Nutzen Sie diese Informationen, um neue Apps zu erstellen und ihre Schlüsselmetriken zu konfigurieren, um die SDK-Optionen für Adobe Analytics und Adobe Audience Manager zu konfigurieren, um die Optionen für Akquise und ID-Dienst zu konfigurieren und um die Konfigurationsdatei, die SDKs sowie die Tools für Entwickler und Tester herunterzuladen.
keywords: mobile
seo-description: Nutzen Sie diese Informationen, um neue Apps zu erstellen und ihre Schlüsselmetriken zu konfigurieren, um die SDK-Optionen für Adobe Analytics und Adobe Audience Manager zu konfigurieren, um die Optionen für Akquise und ID-Dienst zu konfigurieren und um die Konfigurationsdatei, die SDKs sowie die Tools für Entwickler und Tester herunterzuladen.
seo-title: Neue App hinzufügen
solution: Marketing Cloud, Analytics
title: Neue App hinzufügen
topic: Metriken
uuid: 706b5e4d-1318-4a9e-8c69-ffabf51fa02c
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Neue Anwendung hinzufügen{#add-a-new-app}

Nutzen Sie diese Informationen, um neue Apps zu erstellen und ihre Schlüsselmetriken zu konfigurieren, um die SDK-Optionen für Adobe Analytics und Adobe Audience Manager zu konfigurieren, um die Optionen für Akquise und ID-Dienst zu konfigurieren und um die Konfigurationsdatei, die SDKs sowie die Tools für Entwickler und Tester herunterzuladen.

Mithilfe dieser Anweisungen können Sie neue Apps hinzufügen und die Adobe Analytics- und Adobe Audience Manager-Integration konfigurieren.

Bevor Sie Ihre App konfigurieren können, müssen Sie sie in der Adobe Mobile Services-Benutzeroberfläche hinzufügen. Nachdem Sie die App erstellt haben, wird die passende Konfiguration generiert. Diese können Sie den Entwicklern bereitstellen, die das mobile SDK für die App implementieren.

1. Melden Sie sich bei AMS an (Adobe Mobile Services) und führen Sie eine der folgenden Aktionen durch:

   * Klicken Sie auf **[!UICONTROL Neu erstellen], um die App zu erstellen.**
   * Um weitere Apps hinzuzufügen, klicken Sie im linken Navigationsmenü auf Apps verwalten und dann auf **[!UICONTROL Hinzufügen]**.

      For more information about signing in, see Sign in.[](/help/using/gs/gs-signin.md)

      >[!TIP]
      >
      >Um vorhandene Apps zu verwalten, klicken Sie im linken Navigationsmenü auf Apps verwalten und dann auf die App, die Sie ändern möchten. Sie können Änderungen auf der Seite App-informationen vornehmen.

1. Geben Sie Informationen in folgende Felder ein:

   **[!UICONTROL Report Suite]**

   gibt an, in welcher Report Suite in Adobe Analytics die Berichtsdaten erfasst und gespeichert werden. Jede App ist mit einer Analytics Report Suite verknüpft. Wenn Sie App-Daten an mehrere Report Suites senden möchten, müssen Sie für jede Report Suite eine neue App hinzufügen. Jede App ist mit einer Analytics Report Suite verknüpft. Wenn Sie App-Daten an mehrere Report Suites senden möchten, müssen Sie für jede Report Suite eine neue App hinzufügen.

   Wenn Ihnen in Adobe Mobile Analytics-Administratorrechte zugewiesen wurden, können Sie in Adobe Mobile eine neue Report Suite erstellen. To create a new report suite, select **[!UICONTROL New Report Suite]** and type information into the following fields:

   * **[!UICONTROL Report Suite-ID]**

      This ID uniquely identifies the report suite in Adobe Analytics. Ihr Unternehmenspräfix wird automatisch am Anfang der ID hinzugefügt.

   * **[!UICONTROL Einstellungen kopieren aus]**

      The variables, events, processing rules, and other settings are set up in the new report suite exactly like they are in this report suite. Eine in Mobile Services erstellte Report Suite ist nur dann für die Offline-Verwendung aktiviert (bzw. mit einem Zeitstempel versehen), wenn für die Report Suite, von der die **Einstellungen kopiert wurden**, die „Vorlage für mobile App“ verwendet wurde.

   * **[!UICONTROL Zeitzone]**

      Alle Berichtsdaten befinden sich in dieser Zeitzone. Bei der Festlegung der Zeitzone wird versucht, sich an Ihrem Browser zu orientieren.

   * **[!UICONTROL Währung]**

      Revenue is tracked and reported as this type of currency.
   >[!TIP]
   >
   >Informationen zum Verwenden einer Virtual Report Suite (VRS) finden Sie unter [Virtual Report Suites](/help/using/manage-apps/c-mob-vrs.md).

   * **[!UICONTROL Symbol]**

      (**Optional**) To browse to and select an icon for your app, click **[!UICONTROL Icon]**.

   * **[!UICONTROL Name]**

      (**Optional**) Type a descriptive name for the app. Dieser Name hilft Ihnen beim schnellen Auffinden einer App. Ein aussagekräftiger Name hilft Ihnen, schnell den Zweck und die Einstellungen der App zu verstehen.

   * **[!UICONTROL Typ]**

      Wählen Sie einen Typ aus der Dropdownliste aus. Der ausgewählte App-Typ bestimmt, welche Berichte im linken Navigationsmenü verfügbar sind.

      Folgende Typen stehen zur Verfügung:

      * **[!UICONTROL Standard]**

         You can leave the **[!UICONTROL Standard}** option selected for most apps.

      * **[!UICONTROL Publication]**

         Wählen Sie diese Option aus, wenn Ihre App mithilfe der Adobe Digital Publishing Suite erstellt wurde.

      * **[!UICONTROL Spiel]**

         Diese Option ähnelt der Option **[!UICONTROL Standard]**. Der Unterschied liegt darin, dass **Spiel]die in Berichten verwendete Terminologie zu Begriffen aus dem Gaming-Bereich ändert.[!UICONTROL ** Beispielsweise werden Benutzer in Player geändert. Für Spiele-Apps werden automatisch spielespezifische Berichte angezeigt.
   * **[!UICONTROL Beschreibung]**

      (**Optional**) Type a description for the app.



1. Click **[!UICONTROL Save]** to add the new app.

   Nachdem die App hinzugefügt wurde, können Sie auf der Seite App-Informationen zusätzliche Optionen konfigurieren. For more information, see [Manage App Settings](/help/using/c-manage-app-settings/c-manage-app-settings.md).
