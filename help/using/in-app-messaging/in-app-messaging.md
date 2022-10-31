---
description: Erstellen und verwalten Sie In-App- und Push-Nachrichten und erstellen Sie Berichte zu diesen Nachrichten.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: Messaging
topic-fix: Metrics
uuid: e32d3e35-2d09-4ddf-8919-75dc895abcb3
exl-id: e6d076fc-3176-4591-8388-314b936c58cd
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 100%

---

# Messaging {#messaging}

{#eol}

Sie können In-App- und Push-Nachrichten erstellen und verwalten und entsprechende Berichte anzeigen.

## Neue Adobe Experience Cloud SDK-Version

Sind Sie auf der Suche nach Informationen und Dokumentation zu Mobile SDK für die Adobe Experience Platform? Klicken Sie [hier](https://aep-sdks.gitbook.io/docs/), um unsere aktuelle Dokumentation abzurufen.

Seit September 2018 steht eine neue, bessere Version des SDK zur Verfügung. Diese neuen Adobe Experience Platform Mobile SDK können über [Experience Platform Launch](https://www.adobe.com/de/experience-platform/launch.html) konfiguriert werden.

* Gehen Sie zu [Launch](https://launch.adobe.com/), um zu beginnen.
* Gehen Sie zu [Github: Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks), um zu sehen, was in den Experience Platform SDK-Repositorys enthalten ist.

>[!IMPORTANT]
>
> Wenn Sie die Mobile SDK für Adobe Experience Platform mit Adobe Launch verwenden, **müssen** Sie außerdem die Adobe Analytics Mobile Services-Erweiterung installieren, um die Funktionen von Adobe Mobile Services wie Akquise-Links zu verwenden. Weitere Informationen finden Sie unter [Adobe Analytics – Mobile Services](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services). Informationen zur Verwendung von Push- und In-App-Messaging mit den Experience Platform SDK finden Sie unter [Einrichten von Push-Messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-push-messaging) und [Einrichten von In-App-Messaging](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-analytics-mobile-services#set-up-in-app-messaging).

## In-App-Nachrichten {#section_8984F4568BC24D32A87429FFCB5184A6}

In-App-Nachrichten werden Benutzern in Echtzeit ausgeliefert, basierend auf ihren Aktionen und Eigenschaften. Die Nachrichten werden durch Analytics-Daten ausgelöst, die bereits vom SDK verfolgt werden.

Die folgenden Nachrichtentypen werden unterstützt:

* Benutzerdefinierte und thematische
* Vollbild
* Native Warnhinweise
* Lokale Benachrichtigungen

Hier finden Sie einige zusätzliche Informationen, die Ihnen helfen, die Funktionsweise von In-App-Messaging besser zu verstehen:

* Für In-App-Nachrichten ist SDK-Version 4.2 oder höher erforderlich.
* Sie müssen angeben, wer über Mobile App Admin-Rechte verfügt.

   Diese Rechte ermöglichen den Zugriff auf Akquise-Links und In-App-Nachrichten. Weitere Informationen finden Sie unter [Rollen und Berechtigungen](/help/using/gs/c-mob-roles-and-permissions.md).
* Nachdem eine Nachricht genehmigt wurde, wird sie automatisch in der Anwendung veröffentlicht.
* Das SDK stellt die Nachricht den Benutzern bereit, wenn die Nachrichtenparameter wie Eigenschaften, Auslöser und Zeitplan erfüllt sind.
* Nachrichten können benutzerdefiniertes HTML oder ein Bild unter Verwendung einer Online-URL enthalten.

   Für Nachrichten, die offline ausgelöst werden, kann auch ein Backup- oder ein alternatives Bild aus dem App-Packet angegeben werden.
* Aktive und abgeschlossene Nachrichten bieten Berichte zu der Gesamtanzahl der Ansichten, Clickthrough-Raten usw.
* Für benutzerdefinierte Nachrichten stehen Vorlagen zur Verfügung, mit denen Sie schnell und einfach Ihre eigene In-App-Nachricht erstellen können.

## Push-Nachrichten {#section_90555A55BCE7427A90B1577E14BEF51B}

Push-Nachrichten werden an Benutzer gesendet, die den Erhalt von Benachrichtigungen aktiviert haben. Sie können diese Push-Nachrichten an Benutzer in Analytics-Segmenten oder in benutzerdefinierten Segmenten richten. Sie können Push-Nachrichten verwenden, um den Kontakt zu passiven Benutzern wiederherzustellen oder zeit- und standortspezifische Informationen zu übermitteln, da die Nachrichten außerhalb Ihrer App angezeigt werden.

Bevor Sie Push-Nachrichten konfigurieren können, lesen Sie [Voraussetzungen für die Aktivierung der Push-Benachrichtigung](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/prerequisites-push-messaging.md). Nachdem Sie diese Aufgaben ausgeführt haben, müssen Sie Push-Nachrichten in den Einstellungen Ihrer App konfigurieren. Weitere Informationen finden Sie unter [Push-Benachrichtigung konfigurieren](/help/using/c-manage-app-settings/c-mob-confg-app/configure-push-messaging/configure-push-messaging.md).
