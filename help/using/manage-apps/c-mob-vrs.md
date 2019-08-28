---
description: Bei einer Virtual Report Suite (VRS) handelt es sich um eine Report Suite, die durch Anwenden einer oder mehrerer Segmentdefinitionen auf eine Report Suite erstellt wird. So können Benutzer ihre Daten in der Report Suite beibehalten und sie dennoch so verwalten, als befänden sie sich in separaten Report Suites.
seo-description: Bei einer Virtual Report Suite (VRS) handelt es sich um eine Report Suite, die durch Anwenden einer oder mehrerer Segmentdefinitionen auf eine Report Suite erstellt wird. So können Benutzer ihre Daten in der Report Suite beibehalten und sie dennoch so verwalten, als befänden sie sich in separaten Report Suites.
seo-title: Virtual Report Suites
title: Virtual Report Suites
uuid: 3 f 467 cad -43 e 7-4 cd 0-889 b -89 f 8 c 61 febbd
translation-type: tm+mt
source-git-commit: 814c99695f538160ae28484ca8e2a92f5b24bb1a

---


# Virtual report suites {#virtual-report-suites}

Bei einer Virtual Report Suite (VRS) handelt es sich um eine Report Suite, die durch Anwenden einer oder mehrerer Segmentdefinitionen auf eine Report Suite erstellt wird. Dadurch können Benutzer ihre Daten in einer Report Suite verwalten, die Daten jedoch so verwalten, als wäre sie in separaten Report Suites enthalten.

Apps, die mit RS arbeiten, funktionieren genauso wie Apps, die eine normale Report Suite verwenden, mit Ausnahme der folgenden Funktionen:

* Verarbeitungsregeln
* eVars/Props/Listvars/Ereignisse
* Option für Zeitstempel aktivieren
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

Eine VRS kann Ihnen dabei helfen, die folgenden Aufgaben auszuführen:

* Datenzugriff beschränken:

   Ein multinationales Unternehmen verfügt über eine App, die für alle geografischen Standorte Daten an eine Report Suite sendet. Das Unternehmen möchte jedoch den Zugriff so einschränken, dass Unternehmensbenutzer einer Region nicht auf die Daten einer anderen Region zugreifen können. Der Administrator des Unternehmens kann eine VRS erstellen, um Benutzer nach Region zu segmentieren und die VRS nur dem Geschäftsbenutzer zu erteilen, der die Region verwaltet.

   Diese Einschränkung hindert Benutzer daran, Daten anzuzeigen, die nicht zu ihrer Region gehören. So muss beispielsweise ein Unternehmensbenutzer im EMEA-Raum nicht auf Daten aus der APAC-Region zugreifen können.

* Zulassen der Kontrolle über In-App-/Push-Nachrichten, Standorthinhalte, Akquise und Postbacks mit allen Daten, die an eine Report Suite gesendet werden.

   Ein multinationales Unternehmen möchte sämtliche Daten für alle geografischen Standorte an nur eine Report Suite senden. Das Unternehmen möchte jedoch, dass die jeweiligen Marketingteams der verschiedenen Regionen ihre In-App-/Push-Nachrichten selbst verwalten. Der Administrator des Unternehmens erstellt regionale VRSs und jedes Team kann seine eigene App basierend auf dieser VRS verwalten.

   Das regionale Team erstellt dann seine App mithilfe der Konfigurationsdatei aus dem VRS. Die Daten werden an die übergeordnete Report Suite gesendet, aber In-App-/Push-Nachrichten, Location-pois, Akquise und Postbacks werden in der App gesteuert, die von der VRS erstellt wurde.

## Create a virtual report suite in Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Nur Adobe Analytics-Administratoren können Virtual Report Suites in Adobe Analytics erstellen und ändern. To create a virtual report suite, see [Create virtual report suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html).

Jede VRS verfügt über eine eindeutige ID. Um die übergeordnete Report Suite-ID in der Benutzeroberfläche von Adobe Mobile Services anzuzeigen, klicken Sie auf der Seite App-Einstellungen verwalten im Abschnitt **[!UICONTROL App-Informationen]** **[!UICONTROL auf Mehr Details]**.

In der Adobe Mobile Services-Benutzeroberfläche können Sie eine VRS verwenden, um eine App sowie Segmentdaten für eine bestimmte Gruppe in Ihrer Organisation zu erstellen. So kann beispielsweise ein Benutzer in Spanien nicht auf die Daten der Unternehmensbenutzer in Japan zugreifen.

>[!TIP]
>
>Die Werte, die aus der übergeordneten Report Suite übernommen werden, können nicht geändert werden.

Eine VRS ist eine serverseitige Segmentdefinition, die an eine übergeordnete Report Suite angehängt ist. Deshalb können Sie in einer VRS keine Daten erfassen, da das SDK Treffer nur an die übergeordnete Report Suite sendet, die diese Treffer aufzeichnet.

## Virtual report suite in Adobe Mobile Services and data collection {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

In Adobe Mobile Services können Sie eine App basierend auf einer übergeordneten Report Suite oder einer Virtual Report Suite erstellen. Wenn Sie eine App basierend auf einer Virtual Report Suite erstellen, empfiehlt es sich, VRS-Segment und App-Definition aufeinander auszurichten.

>[!TIP]
>
>Push-Zertifizierungen werden auf der App-Ebene in der Mobile Services-Benutzeroberfläche angehängt.

Um zu gewährleisten, dass Ihre Push-Nachrichten ordnungsgemäß gesendet werden, muss das Zielgruppensegment korrekt definiert sein. Weitere Informationen finden Sie unter [Zielgruppe: Zielgruppensegmente für Push-Nachrichten definieren und konfigurieren](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Understanding time zones {#section_498E1EED22D741C3BDED44F01FACA72A}

Die Zeitzoneneigenschaft auf der Seite App-Einstellungen verwalten unterscheidet sich von der Zeitzoneneigenschaft, die Sie zum Erstellen der VRS in Adobe Analytics verwenden. Die Eigenschaft auf der Seite „App-Einstellungen verwalten“ wird von der übergeordneten Report Suite übernommen, die zum Senden von Daten an Adobe Analytics verwendet wird. Die Eigenschaft, die Sie beim Erstellen der VRS in Adobe Analytics angeben, wird zum Anzeigen der Berichte in der Mobile Services-Benutzeroberfläche verwendet und kann sich von der übergeordneten Report Suite unterscheiden.

## Select a virtual report suite in the Mobile Services UI {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

Um beim Erstellen einer App eine VRS zu verwenden, wählen Sie die VRS auf der Seite **App-Informationen aus der DropdownlisteReport Suite** aus. Diese Liste enthält übergeordnete und Virtual Report Suites.

>[!IMPORTANT]
>
>To select a VRS from the list, locate an option with the blue dot and the `vrs_` *`<company_name>`* `_` *`<unique name>`* naming convention.

## Virtual Report Suite properties {#section_20ECE6243F664C4FB4347ADB4FF0458A}

Im Folgenden finden Sie die VRS-Eigenschaften:

>[!TIP]
>
>Die schreibgeschützten Eigenschaften werden von der übergeordneten Report Suite übernommen.

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

Hier finden Sie einige weitere Informationen zu Virtual Report Suites:

* Weitere Informationen zu VRSs finden Sie unter [Virtual Report Suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-about.html).
* For more information about planning a VRS implementation, see [Virtual report suite workflow](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).