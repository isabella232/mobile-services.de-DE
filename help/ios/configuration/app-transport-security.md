---
description: Diese Informationen helfen Ihnen beim Verwenden von App Transport Security (ATS), einem neuen Satz an Sicherheitsanforderungen für iOS 9.
seo-description: Diese Informationen helfen Ihnen beim Verwenden von App Transport Security (ATS), einem neuen Satz an Sicherheitsanforderungen für iOS 9.
seo-title: App Transport Security
solution: Marketing Cloud,Analytics
title: App Transport Security
topic: Entwickler und Implementierung
uuid: e9ee13cf-9802-492e-8b11-95f028e34e61
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# App Transport Security {#app-transport-security}

Diese Informationen helfen Ihnen beim Verwenden von App Transport Security (ATS), einem neuen Satz an Sicherheitsanforderungen für iOS 9.

Ab iOS 9 führte Apple „App Transport Security“ ein, einen Satz von Anforderungen, die den Best Practices für sichere Verbindungen entsprechen. Weitere Informationen finden Sie unter *NSAppTransportSecurity* in der [Information Property List Key Reference](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/).

Damit Version 4.7 oder neuere Versionen des Adobe Mobile-SDK problemlos mit ATS zusammenarbeiten können, müssen Sie die SSL-Aktivierungsoption auf der Seite App-Verwaltungseinstellungen verwenden. For more information, see Manage App Settings or ADBMobile JSON Config.[](/help/using/c-manage-app-settings/c-manage-app-settings.md)[](/help/ios/configuration/json-config/json-config.md)

In Adobe Mobile Services, by selecting the **[!UICONTROL Use HTTPS]** option in the Manage App Settings page, all hits from Analytics, Audience Manager, Target, and Adobe Experience Platform Identity Services are sent via HTTPS.

As an alternative, you can whitelist service the following servers:

| Produkt | Anleitung |
|--- |--- |
| Analytics | Wenn Sie Ihren Analytics-Server auf die Positivliste setzen möchten, fügen Sie Ihre Verfolgungsserverdomäne Ihrer info.plist-Datei als Ausnahmedomäne für ATS hinzu.  Die Verfolgungsserverdomäne finden Sie im Abschnitt Analytics der `ADBMobileConfig.json`-Datei oder im Abschnitt Analytics auf der Seite App-Verwaltungseinstellungen. |
| Audience Manager | Ihre Audience Manager-Domäne finden Sie in den Servereigenschaften des audienceManager-Objekts in Ihrer `ADBMobileConfig.json`-Datei.  Wenn Sie Audience Manager in Ihrer App verwenden und SSL nicht aktiviert ist, fügen Sie diesen Server in Ihrer `Info.plist`-Datei als Ausnahmedomäne für ATS hinzu. |
| Target | Sie können Ihren Target-Endpunkt Ihrer Info.plist-Datei als Ausnahmedomäne für ATS hinzufügen.  Wenn Sie Ihren Target-Endpunkt finden möchten, suchen Sie `clientCodeproperty` im Zielobjekt Ihrer `ADBMobileConfig.json`-Datei. Your endpoint will be `https://{clientCode}.tt.omtrdc.net`.  For example, if your `clientCodeproperty` is `“myCompany”`, your endpoint will be `https://myCompany.tt.omtrdc.net`. |
| Adobe Experience Platform Identity Service | Sie können den Experience Cloud-Server in Ihrer `Info.plist`-Datei als Ausnahmedomäne für ATS hinzufügen. This domain is `dpm.demdex.net`. |
| Mobile Services: Akquise | Nehmen Sie den Akquiseserver in der Datei `Info.plist` als Ausnahmedomäne in die Whitelist auf. This domain is `c00.adobe.com`. |
| Mobile Services: In-App-Nachrichten | Wenn Sie In-App-Nachrichten verwenden, müssen Sie möglicherweise Einträge in der Ausnahmendomäne für ATS für jede URL hinzufügen, die Sie verwenden und die kein HTTPS aufweist. Diese Liste umfasst gehostete Bilder und alle URLs, die in Ihren benutzerdefinierten Vollbildnachrichten-HTML-Code eingebettet sind.  For more detail on setting up exceptions domain in an  file, see the NSExceptionDomains row in Table 2: App Transport Security dictionary primary keys. `info.plist`**** Also see Table 3  Exception domains dictionary keys in Information Property List Key Reference.**[](https://developer.apple.com/library/prerelease/ios/technotes/App-Transport-Security-Technote/) |

>[!TIP]
>
>Diese Überlegungen wirken sich auf die Verbindungen aus, die vom Adobe Mobile SDK hergestellt werden, und wirken sich nicht auf die Webansicht oder andere Verbindungen aus, die von Ihrer App hergestellt werden.

