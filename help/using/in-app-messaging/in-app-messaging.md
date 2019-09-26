---
description: Erstellen und verwalten Sie In-App- und Push-Nachrichten und erstellen Sie Berichte zu diesen Nachrichten.
keywords: mobile
seo-description: Erstellen und verwalten Sie In-App- und Push-Nachrichten und erstellen Sie Berichte zu diesen Nachrichten.
seo-title: Messaging
solution: Marketing Cloud, Analytics
title: Messaging
topic: Metriken
uuid: e32d3e35-2d09-4ddf-8919-75dc895abcb3
translation-type: tm+mt
source-git-commit: 3b744229b3fc288363be74c3c4adcd71ecc4fad4

---


# Messaging {#messaging}

Sie können In-App- und Push-Nachrichten erstellen, verwalten und Berichte dazu erstellen.

## Neue Adobe Experience Cloud SDK-Version

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDKs für die Adobe Experience Platform? Klicken Sie für die neueste Dokumentation [hier](https://aep-sdks.gitbook.io/docs/).

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDKs können über die [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) konfiguriert werden.

* Gehen Sie zu [Launch](https://launch.adobe.com/), um zu beginnen.
* Gehen Sie zu [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK Repositorys enthalten ist.

>[!IMPORTANT]
>
> If you are using the Adobe Experience Platform Mobile SDKs with Adobe Launch, you **must** also install the Adobe Analytics Mobile Services extension to use Adobe Mobile Services features such as Acquisition links. Weitere Informationen finden Sie unter [Adobe Analytics - Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). Informationen zur Verwendung von Push- und In-App-Messaging mit den Experience Platform SDKs finden Sie unter [Einrichten von Push-Messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) und [Einrichten von In-App-Messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

## In-App-Nachrichten {#section_8984F4568BC24D32A87429FFCB5184A6}

In-App-Nachrichten werden Benutzern in Echtzeit ausgeliefert, basierend auf ihren Aktionen und Eigenschaften. Die Nachrichten werden durch Analytics-Daten ausgelöst, die bereits vom SDK verfolgt werden.

Folgende Nachrichtentypen werden unterstützt:

* Benutzerdefiniert und mit Design
* Vollbild
* Native Warnhinweise
* Lokale Benachrichtigungen

To help you understand how in-app messaging works, here is some additional information:

* In-app messages require SDK version 4.2 or later.
* You must specify who has Mobile App Admin rights.

   These rights enable access to acquisition links and in-app messages. For more information, see Roles and permissions.[](/help/using/gs/c-mob-roles-and-permissions.md)
* Nachdem eine Nachricht genehmigt wurde, wird sie automatisch in der App veröffentlicht.
* Wenn die Nachrichtenparameter, wie z. B. Eigenschaften, Auslöser und Zeitplan, erfüllt sind, zeigt das SDK dem Benutzer die Nachricht an.
* Nachrichten können benutzerdefinierte HTML oder ein per Online-URL eingefügtes Bild enthalten.

   Für Nachrichten, die ausgelöst werden, während der Benutzer offline ist, kann auch ein Sicherungs- oder ein alternatives Bild aus dem App-Paket angegeben werden.
* Aktive und abgeschlossene Nachrichten bieten Berichte zu der Gesamtanzahl der Ansichten, Clickthrough-Raten usw.
* Für benutzerdefinierte Nachrichten stehen Vorlagen zur Verfügung, mit denen Sie schnell und einfach Ihre eigene In-App-Nachricht erstellen können.

## Push messages {#section_90555A55BCE7427A90B1577E14BEF51B}

Push-Nachrichten werden an Benutzer gesendet, die den Erhalt von Benachrichtigungen aktiviert haben. Sie können diese Push-Nachrichten an Benutzer in Analytics-Segmenten oder in benutzerdefinierten Segmenten richten. Sie können Push-Nachrichten verwenden, um den Kontakt zu passiven Benutzern wiederherzustellen oder zeit- und standortspezifische Informationen zu übermitteln, da die Nachrichten außerhalb Ihrer App angezeigt werden.

Before you can configure push messaging, see Prerequisites to enable push messaging. [](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md) Nachdem Sie diese Schritte durchgeführt haben, müssen Sie die Push-Benachrichtigung in den Einstellungen der App konfigurieren. Weitere Informationen finden Sie unter [Configure push messaging](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md).
