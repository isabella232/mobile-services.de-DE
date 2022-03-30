---
description: Diese Informationen helfen Ihnen beim Verwenden von App Transport Security (ATS), einem neuen Satz an Sicherheitsanforderungen für iOS 9.
solution: Experience Cloud Services,Analytics
title: App Transport Security
topic-fix: Developer and implementation
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
exl-id: 2fe94e76-06d6-4ad1-95ba-193ae3df4d58
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 100%

---

# App Transport Security {#app-transport-security}

Diese Informationen helfen Ihnen beim Verwenden von App Transport Security (ATS), einem neuen Satz an Sicherheitsanforderungen für iOS 9.

Ab iOS 9 führte Apple „App Transport Security“ ein, einen Satz von Anforderungen, die den Best Practices für sichere Verbindungen entsprechen. Weitere Informationen finden Sie unter *NSAppTransportSecurity* in [Schlüsselreferenz zur Informationseigenschaftsliste](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/).

Damit Version 4.7 oder neuere Versionen des Adobe Mobile-SDK problemlos mit ATS zusammenarbeiten können, müssen Sie die SSL-Aktivierungsoption auf der Seite App-Verwaltungseinstellungen verwenden. Weitere Informationen finden Sie unter [App-Einstellungen verwalten](/help/using/c-manage-app-settings/c-manage-app-settings.md) oder [ADBMobile JSON-Konfiguration](/help/ios/configuration/json-config/json-config.md).

In Adobe Mobile Services werden durch Aktivieren der Option **[!UICONTROL HTTPS verwenden]** auf der Seite „App-Verwaltungseinstellungen verwalten“ alle Treffer aus Analytics, Audience Manager, Target und dem Identity-Dienst für Adobe Experience Platform über HTTPS gesendet.

Alternativ können Sie die folgenden Server in Ihrer „Zulassungsliste“ platzieren:

| Produkt | Anleitung |
|--- |--- |
| Analytics | Wenn Sie Ihren Analytics-Server zulassen möchten, fügen Sie Ihre Verfolgungsserverdomäne Ihrer info.plist-Datei als Ausnahmedomäne für ATS hinzu.  Die Verfolgungsserverdomäne finden Sie im Abschnitt Analytics der `ADBMobileConfig.json`-Datei oder im Abschnitt Analytics auf der Seite App-Verwaltungseinstellungen. |
| Audience Manager | Ihre Audience Manager-Domäne finden Sie in den Servereigenschaften des audienceManager-Objekts in Ihrer `ADBMobileConfig.json`-Datei.  Wenn Sie Audience Manager in Ihrer App verwenden und SSL nicht aktiviert ist, fügen Sie diesen Server in Ihrer `Info.plist`-Datei als Ausnahmedomäne für ATS hinzu. |
| Target | Sie können Ihren Target-Endpunkt Ihrer Info.plist-Datei als Ausnahmedomäne für ATS hinzufügen.  Wenn Sie Ihren Target-Endpunkt finden möchten, suchen Sie `clientCodeproperty` im Zielobjekt Ihrer `ADBMobileConfig.json`-Datei. Ihr Endpunkt lautet `https://{clientCode}.tt.omtrdc.net`.  Wenn Ihr `clientCodeproperty` beispielsweise `"myCompany"` ist, lautet der Endpunkt `https://myCompany.tt.omtrdc.net`. |
| Identity-Dienst für Adobe Experience Platform | Sie können den Experience Cloud-Server in Ihrer `Info.plist`-Datei als Ausnahmedomäne für ATS hinzufügen. Diese Domain lautet `dpm.demdex.net`. |
| Mobile Services: Akquise | Nehmen Sie den Akquiseserver in der Datei `Info.plist` als Ausnahmedomäne in die Zulassungsliste auf. Diese Domain lautet `c00.adobe.com`. |
| Mobile Services: In-App-Nachrichten | Wenn Sie In-App-Nachrichten verwenden, müssen Sie eventuell Einträge für ATS für jede URL, die Sie verwenden und die nicht HTTPS ist, in die Ausnahme-Domain hinzufügen. Diese Liste umfasst gehostete Bilder und alle URLs, die in Ihren benutzerdefinierten Vollbildnachrichten-HTML-Code eingebettet sind.  Weitere Informationen zum Einrichten der Ausnahmedomäne in einer `info.plist`-Datei finden Sie in der Zeile *NSExceptionDomains* in *Tabelle 2: Primärschlüssel des App Transport Security-Wörterbuchs*. Weitere Informationen finden Sie in *Tabelle 3: Wörterbuchschlüssel für Ausnahmedomänen* in [Schlüsselreferenz der Informationseigenschaftsliste](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/). |

>[!TIP]
>
>Diese Überlegungen wirken sich auf die Verbindungen aus, die vom Adobe Mobile SDK hergestellt werden, und wirken sich nicht auf die Webansicht oder andere Verbindungen aus, die von Ihrer App hergestellt werden.
