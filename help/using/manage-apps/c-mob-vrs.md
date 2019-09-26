---
description: Bei einer Virtual Report Suite (VRS) handelt es sich um eine Report Suite, die durch Anwenden einer oder mehrerer Segmentdefinitionen auf eine Report Suite erstellt wird. So können Benutzer ihre Daten in der Report Suite beibehalten und sie dennoch so verwalten, als befänden sie sich in separaten Report Suites.
seo-description: Bei einer Virtual Report Suite (VRS) handelt es sich um eine Report Suite, die durch Anwenden einer oder mehrerer Segmentdefinitionen auf eine Report Suite erstellt wird. So können Benutzer ihre Daten in der Report Suite beibehalten und sie dennoch so verwalten, als befänden sie sich in separaten Report Suites.
seo-title: Virtual Report Suites
title: Virtual Report Suites
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febbd
translation-type: tm+mt
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a

---


# Virtual report suites {#virtual-report-suites}

Bei einer Virtual Report Suite (VRS) handelt es sich um eine Report Suite, die durch Anwenden einer oder mehrerer Segmentdefinitionen auf eine Report Suite erstellt wird. This allows users to maintain their data in one report suite, but manage the data as if it was in separate report suites.

Apps, die VRSs verwenden, funktionieren genauso wie Apps, die eine normale Report Suite verwenden, mit Ausnahme der folgenden Funktionen:

* Verarbeitungsregeln
* eVars/Props/Listvars/Ereignisse
* Zeitstempel-aktivierte Option
* Dimensions-Flags (Lebenszyklus, Standort usw.)
* Classifications

Diese Werte werden in der übergeordneten Report Suite verwaltet und an die VRSs, die derselben übergeordneten Report Suite angehören, weitergegeben.

Die folgenden Bereiche können in der Benutzeroberfläche von Adobe Mobile Services unabhängig von der übergeordneten Report Suite aufgerufen werden:

* Konfigurationsdatei
* Zielpunkte verwalten
* Link-Ziele verwalten
* Postbacks verwalten
* Nachrichten-Links
* Akquise

Mit einer VRS können Sie die folgenden Aufgaben ausführen:

* Datenzugriff beschränken:

   Ein multinationales Unternehmen verfügt über eine App, die für alle geografischen Standorte Daten an eine Report Suite sendet. Das Unternehmen möchte jedoch den Zugriff so einschränken, dass Unternehmensbenutzer einer Region nicht auf die Daten einer anderen Region zugreifen können. Der Unternehmensadministrator kann eine VRS erstellen, um Benutzer nach Region zu segmentieren und die VRS nur dem Geschäftsbenutzer zuzulassen, der die Region verwaltet.

   Diese Einschränkung hindert Benutzer daran, Daten anzuzeigen, die nicht zu ihrer Region gehören. So muss beispielsweise ein Unternehmensbenutzer im EMEA-Raum nicht auf Daten aus der APAC-Region zugreifen können.

* Allow the control of in-app/push messaging, location POIs, acquisition, and postbacks with all data being sent to one report suite.

   Ein multinationales Unternehmen möchte sämtliche Daten für alle geografischen Standorte an nur eine Report Suite senden. Das Unternehmen möchte jedoch, dass die jeweiligen Marketingteams der verschiedenen Regionen ihre In-App-/Push-Nachrichten selbst verwalten. Der Administrator des Unternehmens erstellt regionale VRSs und jedes Team kann seine eigene App basierend auf dieser VRS verwalten.

   Das regionale Team erstellt dann seine App mithilfe der Konfigurationsdatei aus dem VRS. Die Daten werden an die übergeordnete Report Suite gesendet, aber In-App-/Push-Nachrichten, POIs, Akquise- und Postbacks werden in der App gesteuert, die über die VRS erstellt wurde.

## Create a virtual report suite in Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Only Adobe Analytics admins can create and modify virtual report suites in Adobe Analytics. To create a virtual report suite, see [Create virtual report suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html).

Jede VRS verfügt über eine eindeutige ID. Um die übergeordnete Report Suite-ID in der Benutzeroberfläche von Adobe Mobile Services anzuzeigen, klicken Sie auf der Seite "App-Einstellungen verwalten"im Abschnitt **[!UICONTROL App-Informationen]** auf **[!UICONTROL Mehr Details]**.

In der Adobe Mobile Services-Benutzeroberfläche können Sie eine VRS verwenden, um eine App sowie Segmentdaten für eine bestimmte Gruppe in Ihrer Organisation zu erstellen. So kann beispielsweise ein Benutzer in Spanien nicht auf die Daten der Unternehmensbenutzer in Japan zugreifen.

>[!TIP]
>
>Die Werte, die von der übergeordneten Report Suite geerbt werden, können nicht geändert werden.

Eine VRS ist eine serverseitige Segmentdefinition, die an eine übergeordnete Report Suite angehängt ist. Deshalb können Sie in einer VRS keine Daten erfassen, da das SDK Treffer nur an die übergeordnete Report Suite sendet, die diese Treffer aufzeichnet.

## Virtual report suite in Adobe Mobile Services and data collection {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

In Adobe Mobile Services, you can create an app based on a parent report suite or a virtual report suite. Wenn Sie eine App basierend auf einer Virtual Report Suite erstellen, empfiehlt es sich, VRS-Segment und App-Definition aufeinander auszurichten.

>[!TIP]
>
>Push certifications are attached at the app level in the Mobile Services UI.

Um zu gewährleisten, dass Ihre Push-Nachrichten ordnungsgemäß gesendet werden, muss das Zielgruppensegment korrekt definiert sein. Weitere Informationen finden Sie unter [Zielgruppe: Zielgruppensegmente für Push-Nachrichten definieren und konfigurieren](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Understanding time zones {#section_498E1EED22D741C3BDED44F01FACA72A}

Die Zeitzoneneigenschaft auf der Seite "App-Einstellungen verwalten"unterscheidet sich von der Zeitzoneneigenschaft, mit der Sie die VRS in Adobe Analytics erstellen. Die Eigenschaft auf der Seite „App-Einstellungen verwalten“ wird von der übergeordneten Report Suite übernommen, die zum Senden von Daten an Adobe Analytics verwendet wird. Die Eigenschaft, die Sie beim Erstellen der VRS in Adobe Analytics angeben, wird zur Anzeige der Berichte in der Mobile Services-Benutzeroberfläche verwendet und kann sich von der übergeordneten Report Suite unterscheiden.

## Select a virtual report suite in the Mobile Services UI {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

Um beim Erstellen einer App eine VRS zu verwenden, wählen Sie die VRS auf der Seite **App-Informationen aus der DropdownlisteReport Suite** aus. Diese Liste enthält übergeordnete und Virtual Report Suites.

>[!IMPORTANT]
>
>To select a VRS from the list, locate an option with the blue dot and the `vrs_` *`<company_name>`* `_` *`<unique name>`* naming convention.

## Virtual Report Suite properties {#section_20ECE6243F664C4FB4347ADB4FF0458A}

Im Folgenden finden Sie die VRS-Eigenschaften:

>[!TIP]
>
>The read-only properties are inherited from the parent report suite.

| Eigenschaft | Wird von der übergeordneten Report Suite übernommen | Kann bearbeitet werden? | Hinweise |
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
| `analytics.lifecycleTimeout` | Nein | Ja | Sollte der übergeordneten Report Suite entsprechen, wenn die Daten nicht uneinheitlich sein sollen. |
| `analytics.privacyDefault` | Nein | Ja |  |
| `analytics.batchLimit` | Nein | Ja |  |
| `analytics.timezone` | Ja | Ja, wenn Sie die App zuerst erstellen. | Diese Zeitzonen-Eigenschaft wird verwendet, um Daten an Adobe Analytics zu senden. Sie unterscheidet sich von der Zeitzonen-Eigenschaft, die beim Erstellen einer VRS festgelegt wird. |
| `analytics.timezoneOffset` | Ja | Nein |  |
| `analytics.referrerTimeout` | Nein | Ja |  |
| `analytics.backdateSessionInfo` | Ja | Ja |  |

## Zusätzliche Informationen {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

Hier einige zusätzliche Informationen zu Virtual Report Suites:

* Weitere Informationen zu VRSs finden Sie unter [Virtual Report Suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-about.html).
* For more information about planning a VRS implementation, see [Virtual report suite workflow](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).