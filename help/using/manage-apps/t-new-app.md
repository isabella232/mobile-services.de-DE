---
description: Nutzen Sie diese Informationen, um neue Apps zu erstellen und ihre Schlüsselmetriken zu konfigurieren, um die SDK-Optionen für Adobe Analytics und Adobe Audience Manager zu konfigurieren, um die Optionen für Akquise und ID-Dienst zu konfigurieren und um die Konfigurationsdatei, die SDK sowie die Tools für Entwickler und Tester herunterzuladen.
keywords: mobile
seo-description: Nutzen Sie diese Informationen, um neue Apps zu erstellen und ihre Schlüsselmetriken zu konfigurieren, um die SDK-Optionen für Adobe Analytics und Adobe Audience Manager zu konfigurieren, um die Optionen für Akquise und ID-Dienst zu konfigurieren und um die Konfigurationsdatei, die SDK sowie die Tools für Entwickler und Tester herunterzuladen.
seo-title: Neue App hinzufügen
solution: Marketing Cloud,Analytics
title: Neue App hinzufügen
topic: Metrics
uuid: 706b5e4d-1318-4a9e-8c69-ffabf51fa02c
translation-type: tm+mt
source-git-commit: c198ae57b05f8965a8e27191443ee2cd552d6c50
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 95%

---


# Neue Anwendung hinzufügen{#add-a-new-app}

Nutzen Sie diese Informationen, um neue Apps zu erstellen und ihre Schlüsselmetriken zu konfigurieren, um die SDK-Optionen für Adobe Analytics und Adobe Audience Manager zu konfigurieren, um die Optionen für Akquise und ID-Dienst zu konfigurieren und um die Konfigurationsdatei, die SDK sowie die Tools für Entwickler und Tester herunterzuladen.

Mithilfe dieser Anweisungen können Sie neue Apps hinzufügen und die Adobe Analytics- und Adobe Audience Manager-Integration konfigurieren.

Bevor Sie Ihre App konfigurieren können, müssen Sie sie in der Adobe Mobile Services-Benutzeroberfläche hinzufügen. Nachdem Sie die App erstellt haben, wird die passende Konfiguration generiert. Diese können Sie den Entwicklern bereitstellen, die das mobile SDK für die App implementieren.

1. Melden Sie sich bei AMS an (Adobe Mobile Services) und führen Sie eine der folgenden Aktionen durch:

   * Klicken Sie auf **[!UICONTROL Neu erstellen]**, um die App zu erstellen.
   * Um weitere Apps hinzuzufügen, klicken Sie im linken Navigationsmenü auf Apps verwalten und dann auf **[!UICONTROL Hinzufügen]**.

      Weitere Informationen zum Anmelden finden Sie unter [Anmelden](/help/using/gs/gs-signin.md).

      >[!TIP]
      >
      >Um vorhandene Apps zu verwalten, klicken Sie im linken Navigationsmenü auf „Apps verwalten“ und anschließend auf die App, die Sie anpassen möchten. Sie können Änderungen auf der Seite App-informationen vornehmen.

1. Geben Sie Informationen in folgende Felder ein:

   **[!UICONTROL Report Suite]**

   Geben Sie an, in welcher Report Suite in Adobe Analytics die Berichtsdaten erfasst und gespeichert werden. Jede App ist mit einer Analytics Report Suite verknüpft. Wenn Sie App-Daten an mehrere Report Suites senden möchten, müssen Sie für jede Report Suite eine neue App hinzufügen. Jede App ist mit einer Analytics Report Suite verknüpft. Wenn Sie App-Daten an mehrere Report Suites senden möchten, müssen Sie für jede Report Suite eine neue App hinzufügen.

   Wenn Ihnen in Adobe Mobile Analytics-Administratorrechte zugewiesen wurden, können Sie in Adobe Mobile eine neue Report Suite erstellen. Um eine neue Report Suite zu erstellen, wählen Sie **[!UICONTROL Neue Report Suite]** aus und geben Sie Informationen in folgende Felder ein:

   * **[!UICONTROL Report Suite-ID]**

      Diese ID identifiziert die Report Suite in Adobe Analytics eindeutig. Ihr Unternehmenspräfix wird automatisch am Anfang der ID hinzugefügt.

   * **[!UICONTROL Einstellungen kopieren von]**

      Variablen, Ereignisse, Verarbeitungsregeln und andere Einstellungen werden in der neuen Report Suite genau so eingerichtet wie in dieser Report Suite. Eine in Mobile Services erstellte Report Suite ist nur dann für die Offline-Verwendung aktiviert (bzw. mit einem Zeitstempel versehen), wenn für die Report Suite, von der die **[!UICONTROL Einstellungen kopiert wurden]**, die „Vorlage für mobile App“ verwendet wurde.

   * **[!UICONTROL Zeitzone]**

      Alle Berichtsdaten beziehen sich auf diese Zeitzone. Bei der Festlegung der Zeitzone wird versucht, sich an Ihrem Browser zu orientieren.

   * **[!UICONTROL Währung]**

      In dieser Währung werden die Umsätze verfolgt und in Berichten gemeldet.
   >[!TIP]
   >
   >Informationen zum Verwenden einer Virtual Report Suite (VRS) finden Sie unter [Virtual Report Suites](/help/using/manage-apps/c-mob-vrs.md).

   * **[!UICONTROL Symbol]**

      (**Optional**) Klicken Sie auf **[!UICONTROL Symbol]**, um ein Symbol für Ihre App auszuwählen.

   * **[!UICONTROL Name]**

      (**Optional**) Geben Sie einen beschreibenden Namen für die App ein. Dieser Name hilft Ihnen beim schnellen Auffinden einer App. Ein aussagekräftiger Name hilft Ihnen, schnell den Zweck und die Einstellungen der App zu verstehen.

   * **[!UICONTROL Typ]**

      Select a type from the drop-down list. Die verfügbaren Berichte, die im linken Navigationsmenü angezeigt werden, hängen vom ausgewählten App-Typ ab.

      Folgende Typen stehen zur Verfügung:

      * **[!UICONTROL Standard]**

         Die Option **[!UICONTROL Standard}** können Sie für die meisten Apps verwenden.

      * **[!UICONTROL Veröffentlichung]**

         Wählen Sie diese Option aus, wenn Ihre App mithilfe der Adobe Digital Publishing Suite erstellt wurde.

      * **[!UICONTROL Spiel]**

         Diese Option ähnelt der Option **[!UICONTROL Standard]**. Der Unterschied liegt darin, dass **[!UICONTROL Spiel]** die in Berichten verwendete Terminologie zu Begriffen aus dem Gaming-Bereich ändert. Beispielsweise werden Benutzer in Spieler geändert. Für Spiele-Apps werden automatisch spielespezifische Berichte angezeigt.
   * **[!UICONTROL Beschreibung]**

      (**Optional**) Geben Sie eine Beschreibung für die App ein.



1. Klicken Sie auf **[!UICONTROL Speichern]**, um die neue App hinzuzufügen.

   Nachdem die App hinzugefügt wurde, können Sie auf der Seite App-Informationen zusätzliche Optionen konfigurieren. Weitere Informationen finden Sie unter [App-Einstellungen verwalten](/help/using/c-manage-app-settings/c-manage-app-settings.md).
