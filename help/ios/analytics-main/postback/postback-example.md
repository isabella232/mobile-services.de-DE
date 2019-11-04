---
description: Definition und Quellcodebeispiele für die Funktion „Postbacks“.
seo-description: Definition und Quellcodebeispiele für die Funktion „Postbacks“.
seo-title: Postback-Beispiel
solution: Experience Cloud,Analytics
title: Postback-Beispiel
topic: Entwickler und Implementierung
uuid: 809c5646-7a80-40df-984b-0af89d854259
translation-type: ht
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postback-Beispiel {#postback-example}

Definition und Quellcodebeispiele für die Funktion „Postbacks“.

>[!CAUTION]
>
>Dieses Beispiel dient lediglich Informationszwecken. Die Datei `ADBMobileConfig.json` sollte in der Adobe Mobile-Benutzeroberfläche konfiguriert und nicht manuell verändert werden. Eine manuelle Änderung der Konfigurationsdatei kann zu Problemen führen, wenn Sie die Konfiguration von Remote-Nachrichten aktiviert haben.

## ADBMobileConfig.json-Definition {#section_0F6EC001AB6D488E815F50C7F5DA022E}

```js
"messages": [ 
    { 
        "messageId": "79ae37c9-89b9-465e-af7f-d3351771f1dc", 
        "template": "callback", 
        "payload": {  
            "templateurl": "https://my.server.com/?user={user.name}&zip={user.zip}&c16={%sdkver%}&c27=cln,{a.PrevSessionLength}", 
            "templatebody": "c2RrdmVyPXslc2RrdmVyJX0mY2I9eyVjYWNoZWJ1c3QlfSZjbGllbnRJZD17bi5jbGllbnQuaWR9JnRzPXsldGltZXN0YW1wVSV9JnRzej17JXRpbWVzdGFtcFolfQ==", 
            "contenttype": "application/x-www-form-urlencoded",  
            "timeout": 4 
        }, 
        "showOffline": true, 
        "showRule": "always", 
        "endDate": 2524730400, 
        "startDate": 0, 
        "audiences": [], 
        "triggers": [ 
            { 
                "key": "pageName", 
                "matches": "eq", 
                "values": [ 
                    "MainMenu" 
                ] 
            } 
        ] 
    } 
] 
```

## Codebeispiel {#section_8169B88A2C634CB788DA574EE8C4B1DC}

```objective-c
NSDictionary *contextData = @{@"user.name":@"bob", @"user.zip":@"90210"}; 
[ADBMobile trackState:@"MainMenu" data:contextData];
```

Da sein Status `“MainMenu”` lautet, löst dieser Verfolgungsaufruf die oben aufgeführte Postback-Nachricht aus. Die URL ersetzt alle Vorlagenvariablen durch Werte aus dem Treffer. Angenommen, die vorherige Sitzung des Benutzers dauerte 132 Sekunden und der Nutzer verwendet aktuell Version 4.6.0 des iOS-SDK. Hier ein Beispiel für die resultierende URL:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`
