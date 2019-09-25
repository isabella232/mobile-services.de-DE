---
description: Antworten auf häufig gestellte Fragen zu Adobe Mobile Services sowie allgemeine Funktionsbeschreibungen.
keywords: mobile
seo-description: Antworten auf häufig gestellte Fragen zu Adobe Mobile Services sowie allgemeine Funktionsbeschreibungen.
seo-title: Häufig gestellte Fragen
solution: Marketing Cloud,Analytics
title: Häufig gestellte Fragen
topic: Metriken
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Häufig gestellte Fragen {#frequently-asked-questions}

Die folgende Tabelle enthält eine Liste häufig gestellter Fragen zu Adobe Mobile Services:

## Adobe Mobile SDK {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### Wird das SDK häufig aktualisiert?

Ja, wir führen ständig Updates durch, um Ihnen SDKs mit dem größten Funktionsumfang, der besten Standardkonformität und der höchsten Sicherheit zu liefern. In der Regel veröffentlichen wir jeden Monat eine neue Version. Diese SDK-Updates können direkt ausgetauscht werden (für Version 4x), was die Implementierung erleichtert. Weitere Informationen zu unseren Updates finden Sie in den [Versionshinweisen](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html).

### Welche SDK-Version soll ich einsetzen?

Unsere aktuelle SDK-Version lautet 4.11. Weitere Informationen finden Sie in den [Versionshinweisen](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html).

### Wo kann ich die SDKs herunterladen?

Die SDKs für einzelne Mobilplattformen können unter "App-Einstellungen [verwalten"heruntergeladen werden](/help/using/c-manage-app-settings/c-manage-app-settings.md) .

### Wie konfiguriere ich die SDKs?

Nachdem Sie eine neue App-Report Suite erstellt haben, navigieren Sie zu "App-Einstellungen verwalten"und konfigurieren Sie alle erforderlichen Optionen auf der Seite mit den App-Informationen. Laden Sie nach dem Speichern Ihrer Konfiguration die benötigten SDKs unten auf der Seite „App-Einstellungen verwalten“ herunter. The SDK will come pre-configured with the options you have saved and can be found in the `ADBMobileConfig.json` file in the SDK package. If you change any SDK settings on the Manage App Settings page, make sure you re-download the SDK files or update your `ADBMobileConfig.json` file with the necessary changes.

### Unterstützen die Adobe Mobile SDKs IPv6 für iOS?

Die Adobe Mobile SDKs verwenden die standardmäßigen iOS- und Android-Netzwerkstapel. For iOS, the SDK uses NSURLSession (iOS versions 7+) and NSURLConnection (iOS versions 7 and later) which are fully compliant with IPv6. Developers who have built or use their own networking stack might want to review if there are other mitigating considerations. Im Folgenden finden Sie weitere Informationen von Apple:

*Wenn Sie eine clientseitige App mit High-Level-Netzwerk-APIs wie NSURLSession und den CFNetwork-Frameworks erstellen und eine Verbindung nach Namen herstellen, müssen Sie nichts ändern, damit Ihre App mit IPv6-Adressen funktioniert.* Weitere Informationen finden Sie unter [Unterstützende IPv6 DNS64/NAT64-Netzwerke](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1).


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### Was sind Lebenszyklusmetriken?

Lebenszyklusmetriken sind im Lieferumfang enthaltene Metriken, die automatisch erfasst werden, wenn das SDK zum ersten Mal in Ihrer App implementiert wird. Weitere Informationen finden Sie unter [Lebenszyklusmetriken (Android)](/help/android/metrics.md) und [Lebenszyklusmetriken (iOS)](/help/ios/metrics.md).

### Wie kann ich Fehler in Verarbeitungsregeln beheben?

Weitere Informationen finden Sie unter [Tipps und Tricks zu Verarbeitungsregeln](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html).

### Kann ich meine Analysedaten an mehrere Report Suites senden?

Ja. Die SDKs bieten die Möglichkeit, Daten an mehrere Adobe Analytics Report Suites zu senden. Um mithilfe einer Bildanfrage Daten in mehreren Report Suites zu erfassen, geben Sie im Feld **[!UICONTROL rsids]** unter dem Abschnitt **analytics[!UICONTROL der Datei „“ mehrere Report Suite-IDs ein, getrennt durch Kommas und ohne Leerzeichen.]**`ADBMobileConfig.json` Weitere Informationen finden Sie unter [ADBMobile JSON-Konfiguration](/help/ios/configuration/json-config/json-config.md).

### Wie unterscheiden sich Handybesuche von Starts?

Ein Start wird durch das SDK gemessen, wenn ein Benutzer die App zum ersten Mal öffnet oder nach Überschreiten des festgelegten Timeout-Werts erneut öffnet. The typical timeout is 5 minutes (300 seconds) in **[!UICONTROL lifecycleTimeout]** field, which is located in the `ADBMobileConfig.json` file. Ein Besuch ist eine serverseitige Kalkulation durch Adobe Analytics auf Grundlage der ersten und letzten Datentreffer, die vom SDK gesendet wurden, ohne dass ein Besuchs-Timeout überschritten wurde. Sitzungs-Timeouts für eine Report Suite werden in der Regel auf 30 Minuten festgelegt. Obwohl Besuche aus klassischen Webanalysen stammen, bieten diese Treffer wertvolle Einblicke dahingehend, wie Benutzer Ihre App aufrufen und verlassen.

## Messaging {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### Gibt es für Push-Benachrichtigungen eine Größenbeschränkung oder andere Beschränkungen?

Für Push-Benachrichtigungen gilt ein Grenzwert von 140 Zeichen. Es gibt keine Beschränkung der Anzahl der gesendeten oder geplanten Benachrichtigungen oder der Häufigkeit, mit der Benachrichtigungen gesendet werden.

### Werden für Push-Benachrichtigungen benutzerdefinierte Nutzlasten unterstützt?

Ja, wir unterstützen eine benutzerdefinierte Push-Nutzlast, die in JSON kodiert werden kann. Android- und iOS-Nutzlasten sind auf 4 KB bzw. 2 KB beschränkt. Diese Nutzlasten werden über eine Push- oder eine lokale Benachrichtigung an die App gesendet. Weitere Informationen finden Sie unter [Erlebnis: Push-Nachricht](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Gibt es Größenbeschränkungen für In-App-Nachrichten?

In Adobe Mobile Services erstellte In-App-Nachrichten, die veröffentlicht und aktiv sind, werden auf einem Server gehostet, auf dem eine Größenbeschränkung von 15 MB pro App-Report Suite gilt. Diese Beschränkung gilt für bei Adobe gehostete Inhalte und Ressourcen. Es gibt aber keine Beschränkungen für Ressourcen, auf die In-App-Nachrichten auf anderen Hosts oder innerhalb der App verweisen können.

### Kann ich für In-App-Nachrichten meine eigenen HTMLs verwenden?

Ja, wir unterstützen benutzerdefinierte HTMLs für In-App-Nachrichten. Weitere Informationen finden Sie unter [Erlebnis: In-App-Nachricht](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

### Welche Auslöser kann ich verwenden, um Push- oder In-App-Benachrichtigungen zu senden?

Marketingexperten können beliebige Analytics-Daten oder -Ereignisse nutzen, die als Auslöser für die Anzeige von In-App-Nachrichten gesendet werden. In-App-Nachrichten verwenden Auslöser, die lokal auf dem Gerät auftreten. Wenn mehrere Auslöser ausgewählt werden, müssen alle Auslöser in demselben Treffer auftreten, damit die Nachricht angezeigt wird. Weitere Informationen finden Sie unter [Erlebnis: In-App-Nachricht](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

Push-Nachrichten werden unter Verwendung von bereits bestehenden Adobe Analytics-Segmenten oder von benutzerdefinierten Segmenten gesendet, die über bereits erfasste historische Analytics-Daten erstellt wurden. Weitere Informationen finden Sie unter [Erlebnis: Push-Nachricht](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Warum erhalte ich eine Fehlermeldung mit dem von mir eingegebenen In-App-, Push- oder Marketing-Link-Namen?

Sie können nicht ein und denselben Namen für In-App-Nachrichten, Push-Nachrichten oder Marketinglinks in verschiedenen Apps verwenden, die dieselbe übergeordnete Report Suite oder VRS verwenden. To resolve this issue, enter another name for your in-app message, push message, or Marketing Link.

## Position {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### Gibt es eine Grenze für die Anzahl der Interessensgebiete (POI), die ich haben kann?

Es gelten keine bestimmten Beschränkungen. Für optimale Performance und aufgrund des begrenzten Arbeitsspeichers der Benutzergeräte empfiehlt es sich jedoch, maximal 5.000 Zielpunkte zu erstellen bzw. hochzuladen.

## Akquise {#section_B37F1129CD5843E890D0E54179455357}

### Kann ich In-App-Aktivitäten Kampagnen zuordnen?

Ja. Adobe Mobile Services unterstützen Sie dabei, Marketingtricks zu erstellen, mit denen Sie den Traffic zu Ihren Apps fördern und vorantreiben können, und Akquisekampagnen mit In-App-Analysen und -Konversionen zu verbinden. Weitere Informationen finden Sie unter [Akquise](/help/using/acquisition-main/acquisition-main.md).

### Wie kann ich Links einrichten, um neue App-Benutzer zu erfassen und zu verfolgen?

Sie können Marketing-Links erstellen, über die Benutzer Anwendungen aus dem Apple App Store und aus Google Play herunterladen können. Mit diesen Links können Sie den Downloads Ihre Erfolgsereignisse zuordnen. Weitere Informationen finden Sie unter [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).