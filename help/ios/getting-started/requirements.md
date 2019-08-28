---
description: Führen Sie diese Schritte aus, um eine Report Suite zum Erfassen von iOS-App-Daten zu konfigurieren.
seo-description: Führen Sie diese Schritte aus, um eine Report Suite zum Erfassen von iOS-App-Daten zu konfigurieren.
seo-title: Vorbereitung
solution: Marketing Cloud, Analytics
title: Vorbereitung
topic: Entwickler und Implementierung
uuid: 04133 f 68-3618-41 fd -8 a 13-aec 5 b 6 f 04 df 6
translation-type: tm+mt
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Before you start {#before-you-start}

Führen Sie diese Schritte aus, um eine Report Suite zum Erfassen von iOS-App-Daten zu konfigurieren.

## Role-specific tasks {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics-Administratoren und App-Entwickler müssen die folgenden Aufgaben ausführen:

### Analytics-Administratoren

So konfigurieren Sie eine Report Suite und erfassen Daten aus mobilen Apps:

1. Führen Sie einen der Abschnitte in [Anmelden bei der UI von Adobe Mobile Services](/help/ios/getting-started/getting-started.md) aus.
1. Erstellen Sie ein Analytics-Konto für jeden App-Entwickler.

App-Entwickler können jetzt die von Ihnen erstellten Report Suites anzeigen.

>[!IMPORTANT]
>
>Um eine neue Report Suite zu erstellen und die sdks herunterzuladen, müssen Sie ein Analytics-Administrator sein.

### App-Entwickler

1. Ensure that your Analytics administrator has completed the steps in the *Analytics Administrators* section above.

1. Verify that your Analytics administrator has completed one of the sections in the *Log in to the Adobe Mobile Services UI* below.
1. After the report suite has been configured, complete steps in the *Download the SDK* section below.

Weitere Informationen zu Rollen und Berechtigungen finden Sie unter [Rollen und Berechtigungen](/help/using/gs/c-mob-roles-and-permissions.md).

## Anmelden bei der UI von Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Bei Adobe Mobile Services handelt es sich um die primäre Reporting-Schnittstelle für Analysen und Targeting mobiler Apps. Nachdem Sie diese Schritte ausgeführt haben, können Sie eine Konfigurationsdatei herunterladen, die mit Ihrem Server zur Datenerfassung, Ihrer Report Suite und vielen anderen Einstellungen vorkonfiguriert ist.

Sie können sich auf eine der folgenden Arten bei der von Adobe Mobile Services anmelden:

* **Experience Cloud**

   Sie können sich mit Ihrer Adobe ID bei der [Experience Cloud](https://marketing.adobe.com) anmelden.

   Diese Methode setzt voraus, dass Ihr Unternehmen bereitgestellt wurde und Sie Ihr Analytics-Konto verknüpft haben. Weitere Informationen zur Bereitstellung finden Sie unter [Verwalten von Experience Cloud-Benutzern und -produkten](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html). Weitere Informationen zur Verknüpfung Ihres Kontos finden Sie unter [Organisationen und Kontoverknüpfung](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html).

   >[!TIP]
   >
   >Wenn Sie nicht sicher sind, ob Ihr Unternehmen in der Experience Cloud bereitgestellt wurde, verwenden Sie Ihr vorhandenes Adobe Analytics-Konto.

* **Adobe Analytics**

   Klicken Sie auf **[!UICONTROL Mit Analytics-Konto anmelden]** und geben Sie Ihren Analytics-Unternehmensnamen, Ihren Benutzernamen und Ihr Kennwort ein.

## Report Suite erstellen {#section_7BC602ED1ABA42C6AB722F506B5219F3}

So erstellen Sie eine Report Suite, um App-Daten zu erfassen und eine App zu definieren:

1. Klicken Sie auf **[!UICONTROL Neue App erstellen]**.

   If you do not see this button, click **[!UICONTROL Manage Apps]** &gt; **[!UICONTROL Add]**.

1. In the **[!UICONTROL Report Suite]** drop-down, select **[!UICONTROL New Report Suite]**.

1. Geben Sie den Namen Ihrer App ein und wählen Sie eine eindeutige Report Suite-ID.

   Beispiel einer Report Suite-ID: `mycomobileappdev`. Sie müssen separate Report Suites und Apps für die Entwicklungs- und Produktionsversionen einrichten. Wenn Sie bereit sind, die Produktionsversion einzurichten, wiederholen Sie diese Schritte.
1. Behalten Sie die Option **[!UICONTROL Vorlage für mobile Anwendung]bei.**

   Mit dieser Vorlage können Zeitstempel Offline-Daten erfassen und die Variablen der mobilen Lösung aktivieren, um Lebenszyklusmetriken zu erfassen.

1. Select your **[!UICONTROL Timezone]**, your **[!UICONTROL Currency]**, and click **[!UICONTROL Save]**.

## SDK herunterladen {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Um das mobile SDK herunterzuladen,

1. Melden Sie sich bei Mobile Services an und öffnen Sie die App auf eine der folgenden Weisen:

   * Wählen Sie Ihre App im Dropdown-Menü **[!UICONTROL Alle Apps]aus.**
   * Suchen Sie im rechten Bereich nach Ihrer App und öffnen Sie sie.

1. Klicken Sie auf **[!UICONTROL App-Einstellungen verwalten]**.
1. Scrollen Sie im Abschnitt **[!UICONTROL App-SDK-Downloads]** zum Bereich **App-SDK-Downloads]herunter.[!UICONTROL **

1. Laden Sie das SDK und die Beispiel-App für Ihre Plattform herunter.

>[!TIP]
>
>Eine Konfigurationsdatei für Ihre App wird automatisch im SDK-Download enthalten. Daher müssen Sie diese Datei nicht separat herunterladen. Wenn Sie das SDK jedoch bereits heruntergeladen haben und nur Ihre Einstellungen aktualisieren möchten, laden Sie die Konfigurationsdatei erneut herunter.

