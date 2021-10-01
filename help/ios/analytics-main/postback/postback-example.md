---
description: Definition und Quellcodebeispiele für die Funktion „Postbacks“.
solution: Experience Cloud,Analytics
title: Postback-Beispiel
topic-fix: Developer and implementation
uuid: 809c5646-7a80-40df-984b-0af89d854259
exl-id: 3ec5abf1-a406-48b6-91b1-fbcb0a9094ee
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 100%

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

Da sein Status `"MainMenu"` lautet, löst dieser Verfolgungsaufruf die oben aufgeführte Postback-Nachricht aus. Die URL ersetzt alle Vorlagenvariablen durch Werte aus dem Treffer. Angenommen, die vorherige Sitzung des Benutzers dauerte 132 Sekunden und der Nutzer verwendet aktuell Version 4.6.0 des iOS-SDK. Hier ein Beispiel für die resultierende URL:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-iOS&c27=cln,132`
