---
description: 'Bevor Sie eine Report Suite konfigurieren und Android-Appdaten erfassen, führen Sie zunächst die folgenden erforderlichen Aufgaben aus '
seo-description: 'Bevor Sie eine Report Suite konfigurieren und Android-Appdaten erfassen, führen Sie zunächst die folgenden erforderlichen Aufgaben aus '
seo-title: Vorbereitung
solution: Marketing Cloud, Analytics
title: Vorbereitung
topic: Entwickler und Implementierung
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Before you start {#before-you-start}

Bevor Sie eine Report Suite konfigurieren und Android-Appdaten erfassen, führen Sie zunächst die folgenden erforderlichen Aufgaben aus:

## Role-specific tasks {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics-Administratoren und App-Entwickler müssen die folgenden Aufgaben ausführen:

### Analytics-Administratoren

So konfigurieren Sie eine Report Suite und erfassen Daten aus mobilen Apps:

1. Führen Sie einen der Abschnitte in [Anmelden bei der UI von Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8) aus.
1. Erstellen Sie ein Analytics-Konto für jeden App-Entwickler.

App-Entwickler können jetzt die von Ihnen erstellten Report Suites anzeigen.

>[!IMPORTANT]
>
>Um eine neue Report Suite zu erstellen und die SDKs herunterzuladen, müssen Sie Analytics-Administrator sein.

### App-Entwickler

1. Stellen Sie sicher, dass Ihr Analytics-Administrator die Schritte im Abschnitt *Analytics-Administratoren* unter [Rollenspezifische Aufgaben](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC) ausgeführt hat.

1. Vergewissern Sie sich, dass Ihr Analytics-Administrator einen der Abschnitte unter [Anmelden bei der UI von Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8) ausgeführt hat.
1. Nachdem die Report Suite konfiguriert wurde, führen Sie die Schritte unter [SDK herunterladen](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46) aus.

Weitere Informationen zu Rollen und Berechtigungen finden Sie unter [Rollen und Berechtigungen](/help/using/gs/c-mob-roles-and-permissions.md).

## Anmelden bei der UI von Adobe Mobile Services {#section_690A2EC4572E47869F183974E932A6A8}

Bei Adobe Mobile Services handelt es sich um die primäre Reporting-Schnittstelle für Analysen und Targeting mobiler Apps. Nachdem Sie diese Schritte ausgeführt haben, können Sie eine Konfigurationsdatei herunterladen, die mit Ihrem Server zur Datenerfassung, Ihrer Report Suite und vielen anderen Einstellungen vorkonfiguriert ist.

Sie können sich auf eine der folgenden Arten bei der UI von Adobe Mobile Services anmelden:

### Experience Cloud

Sie können sich mit Ihrer Adobe ID bei der [Experience Cloud](https://marketing.adobe.com) anmelden. Dies setzt voraus, dass Ihr Unternehmen in der Experience Cloud präsent ist und Sie Ihr Analytics-Konto verknüpft haben. Weitere Informationen finden Sie unter [Verwalten von Experience Cloud-Benutzern und -Produkten](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!TIP]
>
>Wenn Sie sich nicht sicher sind, ob Ihr Unternehmen in der Experience Cloud bereitgestellt wurde, verwenden Sie Ihr bestehendes Adobe Analytics-Konto.

### Adobe Analytics

Klicken Sie auf **[!UICONTROL Mit Analytics-Konto anmelden]** und geben Sie Ihren Analytics-Unternehmensnamen, Ihren Benutzernamen und Ihr Kennwort ein.

## Report Suite erstellen {#section_7BC602ED1ABA42C6AB722F506B5219F3}

So erstellen Sie eine Report Suite, um App-Daten zu erfassen und eine App zu definieren:

1. Klicken Sie auf **[!UICONTROL Neue App erstellen]**.

   If you do not see this button, click **[!UICONTROL Manage Apps]** &gt; **[!UICONTROL Add]**.

1. In the **[!UICONTROL Report Suite]** drop-down, select **[!UICONTROL New Report Suite]**.

1. Geben Sie den Namen Ihrer App ein und wählen Sie einen Typ für die Report Suite.

   Beispiel einer Report Suite-ID: `mycomobileappdev`. Sie müssen separate Report Suites und Apps für die Entwicklungs- und Produktionsversionen einrichten. Sie können diese Schritte also für die Einrichtung der Produktionsversion einfach wiederholen.
1. In **[!UICONTROL Report Suite ID]**, verify that your report suite name is displayed.
1. Überprüfen Sie, ob in **[!UICONTROL Einstellungen kopieren von]** **Mobile App Template[!UICONTROL ausgewählt ist.]**

   Mit dieser Vorlage können Zeitstempel Offline-Daten erfassen und die Variablen der mobilen Lösung aktivieren, um Lebenszyklusmetriken zu erfassen.

1. Wählen Sie Zeitzone und Währung aus und klicken Sie auf **[!UICONTROL Speichern]**.

## SDK herunterladen {#section_044C17DF82BC4FD8A3E409C456CE9A46}

Um das mobile SDK herunterzuladen,

1. melden Sie sich bei der Mobile Services UI an und öffnen Sie Ihre App auf eine der folgenden Arten:

   * Wählen Sie Ihre App im Dropdown-Menü **[!UICONTROL Alle Apps]aus.**
   * Suchen Sie im rechten Bereich nach Ihrer App und öffnen Sie sie.

1. Klicken Sie auf **[!UICONTROL App-Einstellungen verwalten]**.
1. Scrollen Sie zum Abschnitt **[!UICONTROL App SDK Downloads].**
1. Laden Sie das SDK und die Beispiel-App für Ihre Plattform herunter.

>[!TIP]
>
>Eine Konfigurationsdatei für Ihre App wird automatisch in den SDK-Download eingeschlossen. Daher müssen Sie diese Datei nicht separat herunterladen. Wenn Sie das SDK jedoch bereits heruntergeladen haben und nur Ihre Einstellungen aktualisieren möchten, laden Sie die Konfigurationsdatei erneut herunter.

Wenn Sie Android Studio verwenden, können Sie der Datei `build.gradle` in Ihrer App auch Folgendes hinzufügen:

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

Beachten Sie die folgenden Informationen:

* Ersetzen Sie die Versionsnummer im Codebeispiel durch die entsprechende Version der Android-SDKs.
* Laden Sie die Konfigurationsdatei herunter und fügen Sie sie in Ihr Projekt ein.