---
description: 'Bevor Sie eine Report Suite konfigurieren und Android-Appdaten erfassen, führen Sie zunächst die folgenden erforderlichen Aufgaben aus '
seo-description: 'Bevor Sie eine Report Suite konfigurieren und Android-Appdaten erfassen, führen Sie zunächst die folgenden erforderlichen Aufgaben aus '
seo-title: Vorbereitung
solution: Experience Cloud,Analytics
title: Vorbereitung
topic: Developer and implementation
uuid: 0ca9e937-8d40-4570-9dbf-9aecc6ecedf6
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 100%

---


# Vorbereitung {#before-you-start}

Bevor Sie eine Report Suite konfigurieren und Android-Appdaten erfassen, führen Sie zunächst die folgenden erforderlichen Aufgaben aus:

## Rollenspezifische Aufgaben {#section_8B9EA1FA189F4C6DB7D829F0B5844FBC}

Analytics-Administratoren und App-Entwickler müssen die folgenden Aufgaben ausführen:

### Analytics-Administratoren

So konfigurieren Sie eine Report Suite und erfassen Daten aus mobilen Apps:

1. Füllen Sie einen der Abschnitte unter [Anmelden bei der UI von Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8) aus.
1. Erstellen Sie für jeden App-Entwickler ein Analytics-Konto.

App-Entwickler können jetzt auf die Ansicht der von Ihnen erstellten Report Suites zugreifen.

>[!IMPORTANT]
>
>Um eine neue Report Suite zu erstellen und die SDK herunterzuladen, müssen Sie ein Analytics-Administrator sein.

### App-Entwickler

1. Stellen Sie sicher, dass Ihr Analytics-Administrator die Schritte in *Analytics-Administratoren* unter [Rollenspezifische Aufgaben](../getting-started/requirements.md#section_8B9EA1FA189F4C6DB7D829F0B5844FBC) ausgeführt hat.
1. Vergewissern Sie sich, dass Ihr Analytics-Administrator einen der Abschnitte unter [Anmelden bei der UI von Adobe Mobile Services](../getting-started/requirements.md#section_690A2EC4572E47869F183974E932A6A8) ausgeführt hat.
1. Nachdem die Report Suite konfiguriert wurde, führen Sie die Schritte unter [SDK herunterladen](../getting-started/requirements.md#section_044C17DF82BC4FD8A3E409C456CE9A46) aus.

Weitere Informationen zu Rollen und Berechtigungen finden Sie unter [Rollen und Berechtigungen](/help/using/gs/c-mob-roles-and-permissions.md).

## Anmelden bei der UI von Adobe Mobile Services   {#section_690A2EC4572E47869F183974E932A6A8}

Adobe Mobile Services ist die primäre Reporting-Benutzeroberfläche für die Analyse und das Targeting mobiler Apps. Nach Abschluss dieser Schritte können Sie eine Konfigurationsdatei herunterladen, die mit Ihrem Datenerfassungs-Server, Ihrer Report Suite und vielen anderen Einstellungen vorkonfiguriert ist.

Sie können sich auf eine der folgenden Arten bei der Benutzeroberfläche von Adobe Mobile Services anmelden:

### Experience Cloud

Sie können sich mit Ihrer Adobe ID bei der [Experience Cloud](https://experiencecloud.adobe.com) anmelden. Dies setzt voraus, dass Ihr Unternehmen in der Experience Cloud präsent ist und Sie Ihr Analytics-Konto verknüpft haben. Weitere Informationen finden Sie unter [Verwalten von Experience Cloud-Benutzern und -Produkten](https://docs.adobe.com/content/help/de-DE/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!TIP]
>
>Wenn Sie sich nicht sicher sind, ob Ihr Unternehmen bereits Teil der Experience Cloud ist, nutzen Sie Ihr bestehendes Adobe Analytics-Konto.

### Adobe Analytics

Klicken Sie auf **[!UICONTROL Mit Analytics-Konto anmelden]** und geben Sie Ihren Analytics-Unternehmensnamen, Ihren Benutzernamen und Ihr Kennwort ein.

## Report Suite erstellen {#section_7BC602ED1ABA42C6AB722F506B5219F3}

So erstellen Sie eine Report Suite, um App-Daten zu erfassen und eine App zu definieren:

1. Melden Sie sich bei der Mobile Services-Benutzeroberfläche an, indem Sie im Browser [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/) eingeben.
1. Klicken Sie auf **[!UICONTROL App erstellen]**.

   Wenn diese Schaltfläche nicht angezeigt wird, klicken Sie auf **[!UICONTROL Apps verwalten]** > **[!UICONTROL Hinzufügen]**.

1. Wählen Sie im Dropdown-Menü **[!UICONTROL Report Suite]** die Option **[!UICONTROL Neue Report Suite]** aus.

1. Geben Sie den Namen Ihrer App ein und wählen Sie einen Typ für die Report Suite.

   Beispiel einer Report Suite-ID: `mycomobileappdev`. Sie müssen separate Report Suites und Apps für die Entwicklungs- und Produktionsversionen einrichten. Sie können diese Schritte also für die Einrichtung der Produktionsversion einfach wiederholen.
1. Überprüfen Sie in **[!UICONTROL Report Suite ID]**, ob der Name der Report Suite angezeigt wird.
1. Überprüfen Sie, ob in **[!UICONTROL Einstellungen kopieren von]** **[!UICONTROL Mobile App Template]** ausgewählt ist.

   Mit dieser Vorlage können Zeitstempel Offline-Daten erfassen und die Variablen der mobilen Lösung aktivieren, um Lebenszyklusmetriken zu erfassen.

1. Wählen Sie Ihre Zeitzone und Währung aus und klicken Sie auf **[!UICONTROL Speichern]**.

## SDK herunterladen {#section_044C17DF82BC4FD8A3E409C456CE9A46}

So laden Sie das mobile SDK herunter:

1. Melden Sie sich bei der Mobile Services-Benutzeroberfläche an, indem Sie im Browser [https://mobilemarketing.adobe.com/](https://mobilemarketing.adobe.com/) eingeben.
1. Klicken Sie im linken Bereich auf die Dropdown-Liste **[!UICONTROL Alle Apps]** und wählen Sie Ihre App aus.
Sie können Ihre App auch im rechten Bereich auswählen.

   >[!IMPORTANT]
   >
   >Um Ihre App im rechten Bereich anzeigen zu können, müssen Sie zunächst eine App erstellen. Weitere Informationen zum Erstellen einer App finden Sie unter [Hinzufügen einer neuen App.](https://docs.adobe.com/content/help/de-DE/mobile-services/using/manage-apps-ug/t-new-app.html)

1. Klicken Sie in Ihrer App im linken Bereich auf **[!UICONTROL App-Einstellungen verwalten]**.

   >[!IMPORTANT]
   >
   >Wenn die Option **[!UICONTROL App-Einstellungen verwalten]** nicht angezeigt wird, stellen Sie sicher, dass Sie in den Adobe Mobile Services angemeldet sind. Klicken Sie zum Überprüfen auf das Symbol ![Lösungsmenü](assets/solution-switcher.png) oben rechts auf der Seite und stellen Sie sicher, dass **[!UICONTROL Adobe Mobile Services]** oben links angezeigt wird.

1. Laden Sie unten auf der Seite „App-Einstellungen verwalten“ im Abschnitt **[!UICONTROL App-SDK-Downloads]** das SDK und die Beispielanwendung für Ihre Plattform herunter.

>[!TIP]
>
>Der SDK-Download beinhaltet auch eine Konfigurationsdatei. Sie müssen die Datei also nicht separat herunterladen. Wenn Sie das SDK jedoch bereits heruntergeladen haben und nur Ihre Einstellungen aktualisieren möchten, laden Sie die Konfigurationsdatei erneut herunter.

Wenn Sie Android Studio verwenden, können Sie der Datei `build.gradle` in Ihrer App auch Folgendes hinzufügen:

```java
compile 'com.adobe.mobile:adobeMobileLibrary:4.13.7'
```

Beachten Sie die folgenden Informationen:

* Ersetzen Sie die Versionsnummer im Codebeispiel durch die entsprechende Version der Android-SDK.
* Laden Sie die Konfigurationsdatei herunter und fügen Sie sie in Ihr Projekt ein.