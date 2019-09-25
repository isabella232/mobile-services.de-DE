---
description: Im Folgenden finden Sie Informationen dazu, was genau Postbacks sind und wie sie funktionieren.
keywords: android;library;mobile;sdk
seo-description: Im Folgenden finden Sie Informationen dazu, was genau Postbacks sind und wie sie funktionieren.
seo-title: Postback-Beispiel
solution: Marketing Cloud, Analytics
title: Postback-Beispiel
topic: Entwickler und Implementierung
uuid: 8010cd00-d42b-4e16-8403-692fab2550f1
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# Postbacks example {#postbacks-example}

You can use this information to help you understand what postbacks are and how they work.

>[!CAUTION]
>
>Dieses Beispiel dient nur zu Informationszwecken. Die Datei `ADBMobileConfig.json` sollte in der Adobe Mobile-Benutzeroberfläche konfiguriert und nicht manuell verändert werden. Eine manuelle Änderung der Konfigurationsdatei kann zu Problemen führen, wenn Sie die Konfiguration von Remote-Nachrichten aktiviert haben.

## `ADBMobileConfig.json` definition {#section_8751E8176F3546C09420341A39758AFF}

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

## Code sample {#section_D063DE82976D4EDEA97E804BD1C4718F}

```js
HashMap<String, Object> contextData = new HashMap<String, Object>(); 
contextData.put("user.name", "bob"); 
contextData.put("user.zip", "90210"); 
Analytics.trackState("MainMenu", contextData);
```

Because its state is `“MainMenu”`, this tracking call triggers the above postback message. Die URL ersetzt alle Vorlagenvariablen durch Werte aus dem Treffer. Wenn man davon ausgeht, dass die vorherige Sitzung des Benutzers 132 Sekunden lang war und dieser Benutzer mit Android SDK Version 4.6.0 arbeitet, sieht die resultierende URL wie folgt aus:

`https://my.server.com/?user=bob&zip=90210&c16=4.6.0-AN&c27=cln,132`
