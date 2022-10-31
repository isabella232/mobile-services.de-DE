---
description: Bei einer Virtual Report Suite (VRS) handelt es sich um eine Report Suite, die durch Anwenden einer oder mehrerer Segmentdefinitionen auf eine Report Suite erstellt wird. So können Benutzer ihre Daten in der Report Suite beibehalten und sie dennoch so verwalten, als befänden sie sich in separaten Report Suites.
title: Virtual Report Suites
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febbd
exl-id: c9ce7f7c-2023-4a9d-9e4d-bacc21f9ad40
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 73%

---

# Virtual Report Suites {#virtual-report-suites}

{#eol}

Bei einer Virtual Report Suite (VRS) handelt es sich um eine Report Suite, die durch Anwenden einer oder mehrerer Segmentdefinitionen auf eine Report Suite erstellt wird. So können Benutzer ihre Daten in der Report Suite beibehalten und sie dennoch so verwalten, als befänden sie sich in separaten Report Suites.

Apps, die eine VRS verwenden, verhalten sich abgesehen von der Verwaltung folgender Funktionen genauso wie Apps mit normalen Report Suites:

* Verarbeitungsregeln
* eVars/props/listvars/events
* Zeitstempel-aktivierte Option
* Dimension-Flags (Lebenszyklus, Ort usw.)
* Klassifizierungen

Diese Werte werden in der übergeordneten Report Suite verwaltet und für die VRSs freigegeben, die zur gleichen übergeordneten Report Suite gehören.

Auf folgende Bereiche können Sie unabhängig von der übergeordneten Report Suite in der Adobe Mobile Services-Benutzeroberfläche zugreifen:

* Die Konfigurationsdatei
* Zielpunkte verwalten
* Link-Ziele verwalten
* Postbacks verwalten
* Nachrichten-Links
* Akquise

Mit einer VRS können Sie folgende Aufgaben ausführen:

* Datenzugriff beschränken

   Ein multinationales Unternehmen verfügt über eine App, die Daten für alle geografischen Standorte an eine Report Suite sendet. Das Unternehmen möchte jedoch den Zugriff so einschränken, dass Unternehmensbenutzer einer Region nicht auf die Daten einer anderen Region zugreifen können. Der Administrator des Unternehmens kann eine VRS erstellen, um die Benutzer nach Region zu unterteilen, und nur dem Unternehmensbenutzer Zugriff auf die VRS gewähren, der die Region verwaltet.

   Diese Einschränkung hindert Benutzer daran, Daten anzuzeigen, die nicht zu ihrer Region gehören. So muss beispielsweise ein Unternehmensbenutzer im EMEA-Raum nicht auf Daten aus der APAC-Region zugreifen können.

* Kontrolle von In-App-/Push-Nachrichten, Standort-Zielpunkten, Akquise und Postbacks, indem alle Daten nur an eine Report Suite gesendet werden.

   Ein multinationales Unternehmen möchte sämtliche Daten für alle geografischen Standorte an nur eine Report Suite senden. Das Unternehmen möchte jedoch, dass die jeweiligen Marketingteams der verschiedenen Regionen ihre In-App-/Push-Nachrichten selbst verwalten. Der Administrator des Unternehmens erstellt regionale VRSs und jedes Team kann seine eigene App basierend auf dieser VRS verwalten.

   Das regionale Team erstellt dann seine App mithilfe der Konfigurationsdatei aus dem VRS. Die Daten werden an die übergeordnete Report Suite gesendet, aber In-App-/Push-Nachrichten, Standort-Zielpunkte, Akquise und Postbacks werden in der App gesteuert, die über die VRS erstellt wurde.

## Virtual Report Suite in Adobe Analytics erstellen {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Nur Adobe Analytics-Administratoren können Virtual Report Suites in Adobe Analytics erstellen und ändern. Informationen zum Erstellen einer Virtual Report Suite finden Sie unter [Virtual Report Suites erstellen](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html?lang=de) in der Adobe Analytics-Dokumentation.

Jede VRS verfügt über eine eindeutige ID. Um die übergeordnete Report Suite-ID in der Benutzeroberfläche von Adobe Mobile Services anzuzeigen, klicken Sie auf der Seite „App-Einstellungen verwalten“ im Abschnitt **[!UICONTROL App-Informationen]** auf **[!UICONTROL Mehr Details]**.

In der Adobe Mobile Services-Benutzeroberfläche können Sie eine VRS verwenden, um eine App zu erstellen und Daten für eine bestimmte Gruppe in Ihrem Unternehmen zu segmentieren. So kann beispielsweise ein Geschäftsbenutzer in Spanien die Daten nicht sehen, die für einen Geschäftsbenutzer in Japan relevant sind.

>[!TIP]
>
>Sie können die Werte, die von der übergeordneten Report Suite übernommen wurden, nicht ändern.

Eine VRS ist eine serverseitige Segmentdefinition, die an eine übergeordnete Report Suite angehängt ist. Daher können Sie keine Datenerfassung an eine VRS durchführen, da das SDK Treffer nur an die übergeordnete Report Suite sendet, die wiederum die Treffer aufzeichnet.

## Virtual Report Suite in Adobe Mobile Services und Datenerfassung {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

In Adobe Mobile Services können Sie Apps basierend auf einer übergeordneten Report Suite oder einer Virtual Report Suite erstellen. Wenn Sie eine App basierend auf einer Virtual Report Suite erstellen, empfiehlt es sich, VRS-Segment und App-Definition aufeinander auszurichten.

>[!TIP]
>
>Push-Zertifikate sind auf App-Ebene in der Mobile Services-Benutzeroberfläche angehängt.

Um sicherzustellen, dass Ihre Push-Nachrichten korrekt gesendet werden, muss das Zielgruppensegment korrekt definiert sein. Weitere Informationen finden Sie unter [Zielgruppe: Zielgruppensegmente für Push-Nachrichten definieren und konfigurieren](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Zeitzonen verstehen {#section_498E1EED22D741C3BDED44F01FACA72A}

Die Zeitzonen-Eigenschaft auf der Seite „App-Einstellungen verwalten“ unterscheidet sich von der Zeitzonen-Eigenschaft, die Sie beim Erstellen der VRS in Adobe Analytics verwenden. Die Eigenschaft auf der Seite „App-Einstellungen verwalten“ wird von der übergeordneten Report Suite übernommen, die zum Senden von Daten an Adobe Analytics verwendet wird. Die Eigenschaft, die Sie beim Erstellen einer VRS in Adobe Analytics angeben, wird verwendet, um die Berichte in der Mobile Services-Benutzeroberfläche anzuzeigen. Diese Eigenschaft kann sich von der der übergeordneten Report Suite unterscheiden.

## Virtual Report Suite in Mobile Services-Benutzeroberfläche auswählen {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

Um beim Erstellen einer App eine VRS zu verwenden, wählen Sie die VRS auf der Seite App-Informationen aus der Dropdownliste **[!UICONTROL Report Suite]** aus. Diese Liste enthält übergeordnete und Virtual Report Suites.

>[!IMPORTANT]
>
>Um eine VRS aus der Liste auszuwählen, suchen Sie nach einer Option mit blauem Punkt und der Namenskonvention `vrs_` *`<company_name>`*`_`*`<unique name>`*  .

## Eigenschaften von Virtual Report Suites {#section_20ECE6243F664C4FB4347ADB4FF0458A}

Im Folgenden finden Sie die VRS-Eigenschaften:

>[!TIP]
>
>Die schreibgeschützten Eigenschaften werden von der übergeordneten Report Suite übernommen.

| Eigenschaft | Von der übergeordneten Report Suite übernommen | Bearbeitbar? | Hinweise |
|--- |--- |--- |--- |
| `target.clientCode` | Nein | Ja |  |
| `target.timeout` | Nein | Ja |  |
| `audienceManager.server` | Nein | Ja |  |
| `audienceManager.analyticsForwardingEnabled` | Ja | Ja |  |
| `audienceManager.timeout` | Nein | Ja |  |
| `acquisition.server` | Nein | Nein |  |
| `acquisition.appid` | Nein | Nein |  |
| `analytics.rsids` | Ja | Nein |  |
| `analytics.server` | Nein | Nein |  |
| `analytics.ssl` | Nein | Ja |  |
| `analytics.offlineEnabled` | Ja |  |  |
| `analytics.charset` | Ja | Nein |  |
| `analytics.lifecycleTimeout` | Nein | Ja | Sollte die übergeordnete Report Suite sein, wenn Benutzer nicht möchten, dass ihre Daten inkonsistent sind. |
| `analytics.privacyDefault` | Nein | Ja |  |
| `analytics.batchLimit` | Nein | Ja |  |
| `analytics.timezone` | Ja | Ja, wenn Sie die App zum ersten Mal erstellen. | Diese Zeitzonen-Eigenschaft wird zum Senden von Daten an Adobe Analytics verwendet und unterscheidet sich von der Zeitzonen-Eigenschaft, die beim Erstellen einer VRS festgelegt wird. |
| `analytics.timezoneOffset` | Ja | Nein |  |
| `analytics.referrerTimeout` | Nein | Ja |  |
| `analytics.backdateSessionInfo` | Ja | Ja |  |

## Zusätzliche Informationen {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

Im Folgenden finden Sie einige zusätzliche Informationen zu Virtual Report Suites:

* Weitere Informationen zu VRSs finden Sie unter [Virtual Report Suites - Übersicht](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-about.html?lang=de).
* Weitere Informationen zur Planung einer VRS-Implementierung finden Sie unter [Virtual Report Suite-Workflow](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).
