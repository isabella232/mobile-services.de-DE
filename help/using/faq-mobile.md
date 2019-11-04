---
description: Antworten auf häufig gestellte Fragen zu Adobe Mobile Services sowie allgemeine Funktionsbeschreibungen.
keywords: mobile
seo-description: Antworten auf häufig gestellte Fragen zu Adobe Mobile Services sowie allgemeine Funktionsbeschreibungen.
seo-title: Häufig gestellte Fragen
solution: Experience Cloud,Analytics
title: Häufig gestellte Fragen
topic: Metriken
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
translation-type: ht
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Häufig gestellte Fragen {#frequently-asked-questions}

Die folgende Tabelle enthält eine Liste häufig gestellter Fragen zu Adobe Mobile Services:

## Adobe Mobile SDK {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### Wird das SDK häufig aktualisiert?

Ja, wir führen ständig Updates durch, um Ihnen SDK mit dem größten Funktionsumfang, der besten Standardkonformität und der höchsten Sicherheit zu liefern. In der Regel veröffentlichen wir jeden Monat eine neue Version. Diese SDK-Updates können direkt ausgetauscht werden (für Version 4x), was die Implementierung erleichtert. Weitere Informationen zu unseren Updates finden Sie in den [Versionshinweisen](https://docs.adobe.com/content/help/de-DE/release-notes/experience-cloud/current.html).

### Welche SDK-Version soll ich einsetzen?

Unsere aktuelle SDK-Version lautet 4.11. Weitere Informationen finden Sie in den [Versionshinweisen](https://docs.adobe.com/content/help/de-DE/release-notes/experience-cloud/current.html).

### Wo kann ich die SDK herunterladen?

Die SDK für einzelne mobile Plattformen können im Abschnitt [App-Einstellungen verwalten](/help/using/c-manage-app-settings/c-manage-app-settings.md) heruntergeladen werden.

### Wie konfiguriere ich die SDK?

Nachdem Sie eine neue App Report Suite erstellt haben, navigieren Sie zu „App-Einstellungen verwalten“ und konfigurieren Sie die erforderlichen Optionen auf der Seite „App-Informationen“. Laden Sie nach dem Speichern Ihrer Konfiguration die benötigten SDK unten auf der Seite „App-Einstellungen verwalten“ herunter. Das SDK wird mit den von Ihnen gespeicherten Optionen vorkonfiguriert und befindet sich im SDK-Paket in der Datei `ADBMobileConfig.json`. Falls Sie SDK-Einstellungen auf der Seite „App-Einstellungen verwalten“ ändern, müssen Sie die SDK-Dateien erneut herunterladen oder Ihre Datei `ADBMobileConfig.json` mit den erforderlichen Änderungen aktualisieren.

### Unterstützen die Adobe Mobile SDK IPv6 für iOS?

Die Adobe Mobile SDK verwenden die standardmäßigen iOS- und Android-Netzwerkstapel. Das SDK verwendet für iOS NSURLSession (iOS Versionen 7+) und NSURLConnection (iOS Versionen 7 und höher), die vollständig IPv6-konform sind. Entwickler, die eigene Netzwerkstapel erstellt haben bzw. verwenden, sollten gegebenenfalls prüfen, ob es weitere Auffangmöglichkeiten gibt. Im Folgenden finden Sie weitere Informationen von Apple:

*Wenn Sie eine clientseitige App schreiben, die High-Level-Netzwerk-APIs wie NSURLSession und die CFNetwork-Frameworks verwendet, und eine Verbindung nach Name hergestellt wird, sollten keine Änderungen erforderlich sein, damit Ihre App mit IPv6-Adressen funktioniert.* Weitere Informationen finden Sie unter [Unterstützende IPv6 DNS64/NAT64-Netzwerke](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1).


## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### Was sind Lebenszyklusmetriken?

Lebenszyklusmetriken sind im Lieferumfang enthaltene Metriken, die automatisch erfasst werden, wenn das SDK zum ersten Mal in Ihrer App implementiert wird. Weitere Informationen finden Sie unter. [Lebenszyklusmetriken (Android)](/help/android/metrics.md) und [Lebenszyklusmetriken (iOS)](/help/ios/metrics.md).

### Wie kann ich Fehler in Verarbeitungsregeln beheben?

Weitere Informationen finden Sie unter [Tipps und Tricks zu Verarbeitungsregeln](https://docs.adobe.com/content/help/de-DE/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html).

### Kann ich meine Analysedaten an mehrere Report Suites senden?

Ja. Die SDK bieten die Möglichkeit, Daten an mehrere Adobe Analytics Report Suites zu senden. Um mithilfe einer Bildanfrage Daten in mehreren Report Suites zu erfassen, geben Sie im Feld **[!UICONTROL rsids]** unter dem Abschnitt **[!UICONTROL analytics]** der Datei `ADBMobileConfig.json` mehrere Report Suite-IDs ein, getrennt durch Kommas und ohne Leerzeichen. Weitere Informationen finden Sie unter [ADBMobile JSON-Konfiguration](/help/ios/configuration/json-config/json-config.md).

### Wie unterscheiden sich Handybesuche von Starts?

Ein Start wird durch das SDK gemessen, wenn ein Benutzer die App zum ersten Mal öffnet oder nach Überschreiten des festgelegten Timeout-Werts erneut öffnet. In der Regel beträgt der Timeout-Wert 5 Minuten (300 Sekunden). Zu finden ist der Wert im Feld **[!UICONTROL lifecycleTimeout]** in der Datei `ADBMobileConfig.json`. Ein Besuch ist eine serverseitige Kalkulation durch Adobe Analytics auf Grundlage der ersten und letzten Datentreffer, die vom SDK gesendet wurden, ohne dass ein Besuchs-Timeout überschritten wurde. Sitzungs-Timeouts für eine Report Suite werden in der Regel auf 30 Minuten festgelegt. Obwohl Besuche aus klassischen Webanalysen stammen, bieten diese Treffer wertvolle Einblicke dahingehend, wie Benutzer Ihre App aufrufen und verlassen.

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

### Warum erhalte ich eine Fehlermeldung mit dem eingegebenen In-App-, Push- oder Marketinglink-Namen?

Sie können nicht ein und denselben Namen für In-App-Nachrichten, Push-Nachrichten oder Marketinglinks in verschiedenen Apps verwenden, die dieselbe übergeordnete Report Suite oder VRS verwenden. Um dieses Problem zu beheben, geben Sie einfach einen anderen Namen für Ihre In-App-Nachricht, Push-Nachricht oder Ihren Marketinglink ein.

## Ort {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### Gibt es eine Beschränkung für die Anzahl meiner Zielpunkte (POIs)?

Es gelten keine bestimmten Beschränkungen. Für optimale Performance und aufgrund des begrenzten Arbeitsspeichers der Benutzergeräte empfiehlt es sich jedoch, maximal 5.000 Zielpunkte zu erstellen bzw. hochzuladen.

## Akquise {#section_B37F1129CD5843E890D0E54179455357}

### Kann ich In-App-Aktivitäten Kampagnen zuordnen?

Ja. Adobe Mobile Services unterstützen Sie dabei, Marketingtricks zu erstellen, mit denen Sie den Traffic zu Ihren Apps fördern und vorantreiben können, und Akquisekampagnen mit In-App-Analysen und -Konversionen zu verbinden. Weitere Informationen finden Sie in [Akquise](/help/using/acquisition-main/acquisition-main.md).

### Wie kann ich Links einrichten, um neue App-Benutzer zu erfassen und zu verfolgen?

Sie können Marketinglinks erstellen, die Benutzer zum Download von Apps im Apple App Store und in Google Play weiterleiten. Mit diesen Links können Sie den Downloads Ihre Erfolgsereignisse zuordnen. Weitere Informationen finden Sie unter [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).