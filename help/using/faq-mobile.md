---
description: Antworten auf häufig gestellte Fragen zu Adobe Mobile Services sowie allgemeine Funktionsbeschreibungen.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: Häufig gestellte Fragen
topic-fix: Metrics
uuid: 62a9241c-2ada-483a-a594-b023916cb0b6
exl-id: d7dfc36e-56f0-498a-ad50-93fee90cb6ff
source-git-commit: dbe3af75010fbf5195a3f93fc43cb696aaa32b65
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 96%

---

# Häufig gestellte Fragen {#frequently-asked-questions}

Die folgende Tabelle enthält eine Liste häufig gestellter Fragen zu Adobe Mobile Services:

## Adobe Mobile SDK {#section_9C2181F7B39A4BEB8EE6BCEFCF14C72F}

### Welche SDK-Version soll ich einsetzen?

Unsere aktuellen SDKs beziehen sich auf Version 4.11. Weitere Informationen finden Sie unter [Versionshinweise](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=de).

### Wo kann ich die SDK herunterladen?

Die SDK für einzelne mobile Plattformen können im Abschnitt [App-Einstellungen verwalten](/help/using/c-manage-app-settings/c-manage-app-settings.md) heruntergeladen werden.

### Wie konfiguriere ich die SDK?

Nachdem Sie eine neue App Report Suite erstellt haben, navigieren Sie zu „App-Einstellungen verwalten“ und konfigurieren Sie die erforderlichen Optionen auf der Seite „App-Informationen“. Laden Sie nach dem Speichern Ihrer Konfiguration die benötigten SDK unten auf der Seite „App-Einstellungen verwalten“ herunter. Das SDK wird mit den von Ihnen gespeicherten Optionen vorkonfiguriert und befindet sich im SDK-Paket in der Datei `ADBMobileConfig.json`. Falls Sie SDK-Einstellungen auf der Seite „App-Einstellungen verwalten“ ändern, müssen Sie die SDK-Dateien erneut herunterladen oder Ihre Datei `ADBMobileConfig.json` mit den erforderlichen Änderungen aktualisieren.

### Unterstützen die Adobe Mobile SDK IPv6 für iOS?

Die Adobe Mobile SDK verwenden die standardmäßigen iOS- und Android-Netzwerkstapel. Das SDK verwendet für iOS NSURLSession (iOS Versionen 7+) und NSURLConnection (iOS Versionen 7 und höher), die vollständig IPv6-konform sind. Entwickler, die eigene Netzwerkstapel erstellt haben bzw. verwenden, sollten gegebenenfalls prüfen, ob es weitere Auffangmöglichkeiten gibt. Im Folgenden finden Sie weitere Informationen von Apple:

*Wenn Sie eine clientseitige App schreiben, die High-Level-Netzwerk-APIs wie NSURLSession und die CFNetwork-Frameworks verwendet, und eine Verbindung nach Name hergestellt wird, sollten keine Änderungen erforderlich sein, damit Ihre App mit IPv6-Adressen funktioniert.* Weitere Informationen finden Sie unter [Unterstützende IPv6 DNS64/NAT64-Netzwerke](https://developer.apple.com/library/content/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/UnderstandingandPreparingfortheIPv6Transition/UnderstandingandPreparingfortheIPv6Transition.html#__/apple_ref/doc/uid/TP40010220-CH213-SW1).

## Adobe Analytics {#section_78EC9D83791F477AAED678720CEBA9F6}

### Was sind Lebenszyklusmetriken?

Lebenszyklusmetriken sind vorkonfigurierte Metriken, die automatisch erfasst werden, wenn das SDK zum ersten Mal in Ihrer App implementiert wird.

### Wie kann ich Fehler in Verarbeitungsregeln beheben?

Siehe [Verarbeitungsregeln - Tipps und Tricks](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules-tips.html) in der Adobe Analytics-Dokumentation.

### Kann ich meine Analysedaten an mehrere Report Suites senden?

Ja. Die SDK bieten die Möglichkeit, Daten an mehrere Adobe Analytics Report Suites zu senden. Um mithilfe einer Bildanfrage Daten in mehreren Report Suites zu erfassen, geben Sie im Feld **[!UICONTROL rsids]** unter dem Abschnitt **[!UICONTROL analytics]** der Datei `ADBMobileConfig.json` mehrere Report Suite-IDs ein, getrennt durch Kommas und ohne Leerzeichen.

### Inwiefern unterscheiden sich die Besuche auf Mobilgeräten von den Starts?

Ein Start wird vom SDK gemessen, wenn ein Benutzer die App zum ersten Mal öffnet oder zur App zurückkehrt, nachdem er die App länger als den angegebenen Zeitüberschreitungswert verlassen hat. In der Regel beträgt der Timeout-Wert 5 Minuten (300 Sekunden). Zu finden ist der Wert im Feld **[!UICONTROL lifecycleTimeout]** in der Datei `ADBMobileConfig.json`. Ein Besuch ist eine Server-seitige Berechnung von Adobe Analytics und basiert auf den ersten und letzten Datentreffern, die vom SDK gesendet werden, ohne dass ein Besuch-Timeout überschritten wird. In der Regel werden Sitzungs-Timeouts für eine Report Suite auf 30 Minuten eingestellt. Obwohl Besuche von herkömmlichen Web-Analysen stammen, bieten diese Treffer trotzdem wertvolle Einblicke, wie Benutzer Ihre App aufrufen und verlassen.

## Messaging {#section_5EFDD2B2EBA543C09902FF979C89F2EC}

### Gibt es Größen- oder andere Beschränkungen bei Push-Benachrichtigungen?

Push-Benachrichtigungen sind auf 140 Zeichen beschränkt. Es gibt keine Beschränkungen, wie viele Benachrichtigungen gesendet oder geplant werden können oder wie oft Benachrichtigungen gesendet werden.

### Unterstützen Sie benutzerdefinierte Payloads für Push-Benachrichtigungen?

Ja, wir bieten eine benutzerdefinierte Push-Payload, die in JSON kodiert werden kann. Android- und iOS-Payloads sind auf 4 KB bzw. 2 KB beschränkt. Diese Payloads werden über eine Push- oder eine lokale Benachrichtigung an die App gesendet. Weitere Informationen finden Sie unter [Erlebnis: Push-Nachricht](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Gibt es Größenbeschränkungen für In-App-Nachrichten?

Veröffentlichte und aktive In-App-Nachrichten, die in Adobe Mobile Services erstellt wurden, werden auf einem Server mit einer Größenbeschränkung von 15 MB pro App-Report Suite gehostet. Diese Einschränkung gilt zwar für mit Adobe gehostete Inhalte und Ressourcen, es gibt jedoch keine Einschränkungen hinsichtlich der Ressourcen, auf die die In-App-Nachricht auf anderen Hosts oder in der App verweisen kann.

### Kann ich für In-App-Nachrichten meinen eigenen HTML-Code verwenden?

Ja, wir unterstützen benutzerdefiniertes HTML für Ihre In-App-Nachrichten. Weitere Informationen finden Sie unter [Erlebnis: In-App-Nachricht](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

### Welche Auslöser kann ich verwenden, um Push-Benachrichtigungen oder In-App-Nachrichten zu senden?

Marketing-Experten können beliebige gesendete Analytics-Daten oder -Ereignisse als Auslöser auswählen, um In-App-Nachrichten anzuzeigen. In-App-Nachrichten verwenden Auslöser, die lokal auf dem Gerät auftreten. Wenn mehrere Auslöser ausgewählt sind, müssen alle Auslöser im selben Treffer auftreten, damit die Nachricht angezeigt wird. Weitere Informationen finden Sie unter [Erlebnis: In-App-Nachricht](/help/using/in-app-messaging/t-in-app-message/c-experience-in-app-message.md).

Push-Nachrichten werden unter Verwendung von bereits bestehenden Adobe Analytics-Segmenten oder von benutzerdefinierten Segmenten gesendet, die über bereits erfasste historische Analytics-Daten erstellt wurden. Weitere Informationen finden Sie unter [Erlebnis: Push-Nachricht](/help/using/in-app-messaging/t-create-push-message/c-experience-push-message.md).

### Warum erhalte ich eine Fehlermeldung mit dem eingegebenen In-App-, Push- oder Marketinglink-Namen?

Sie können nicht ein und denselben Namen für In-App-Nachrichten, Push-Nachrichten oder Marketinglinks in verschiedenen Apps verwenden, die dieselbe übergeordnete Report Suite oder VRS verwenden. Um dieses Problem zu beheben, geben Sie einfach einen anderen Namen für Ihre In-App-Nachricht, Push-Nachricht oder Ihren Marketinglink ein.

## Standort {#section_01208FE3B7764E0DADDCB9AD9E1FCD87}

### Gibt es eine Beschränkung für die Anzahl meiner Zielpunkte (POIs)?

Es gelten keine bestimmten Beschränkungen. Für optimale Performance und aufgrund des begrenzten Arbeitsspeichers der Benutzergeräte empfiehlt es sich jedoch, maximal 5.000 Zielpunkte zu erstellen bzw. hochzuladen.

## Akquise {#section_B37F1129CD5843E890D0E54179455357}

### Kann ich In-App-Aktivitäten Kampagnen zuordnen?

Ja. Mit Adobe Mobile Services können Sie Marketing-Tricks entwickeln, mit denen Sie den Traffic zu Ihren Apps fördern und steigern und Akquisekampagnen mit In-App-Analysen und Konversionen verbinden können. Weitere Informationen finden Sie in [Akquise](/help/using/acquisition-main/acquisition-main.md).

### Wie kann ich Links einrichten, um neue App-Benutzer zu erfassen und zu verfolgen?

Sie können Marketinglinks erstellen, die Benutzer zum Download von Apps im Apple App Store und in Google Play weiterleiten. Mit diesen Links können Sie den Downloads Ihre Erfolgsereignisse zuordnen. Weitere Informationen finden Sie unter [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).
