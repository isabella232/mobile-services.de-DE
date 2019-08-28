---
description: Zustände sind die verschiedenen Bildschirme oder Ansichten in der Anwendung. Sobald ein neuer Zustand in der Anwendung angezeigt wird (z. B. wenn ein Benutzer von der Startseite zum Newsfeed navigiert), sollte ein Verfolgungszustandsaufruf gesendet werden. In iOS wird ein Zustand in der Regel in der viewDidLoad-Methode jeder Ansicht verfolgt.
seo-description: Zustände sind die verschiedenen Bildschirme oder Ansichten in der Anwendung. Sobald ein neuer Zustand in der Anwendung angezeigt wird (z. B. wenn ein Benutzer von der Startseite zum Newsfeed navigiert), sollte ein Verfolgungszustandsaufruf gesendet werden. In iOS wird ein Zustand in der Regel in der viewDidLoad-Methode jeder Ansicht verfolgt.
seo-title: App-Zustände verfolgen
solution: Marketing Cloud, Analytics
title: App-Zustände verfolgen
topic: Entwickler und Implementierung
uuid: 12 cca 4 eb -1 f 15-4 cec-a 58 f -76 b 69 causf 99 d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# App-Zustände verfolgen {#track-app-states}

Zustände sind die verschiedenen Bildschirme oder Ansichten in der Anwendung. Sobald ein neuer Zustand in der Anwendung angezeigt wird (z. B. wenn ein Benutzer von der Startseite zum Newsfeed navigiert), sollte ein Verfolgungszustandsaufruf gesendet werden. In iOS wird ein Zustand in der Regel in der viewDidLoad-Methode jeder Ansicht verfolgt.

>[!TIP]
>
>To track states, make a call to `trackState`. Status werden nicht automatisch verfolgt.

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden *Sie unter SDK und Config File to your Project* in [Core Implementation and Lifecycle](/help/ios/getting-started/dev-qs.md).
1. Importieren Sie die Bibliothek.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Rufen Sie `trackState` auf, um einen Treffer für diese Statusansicht zu senden.

   ```objective-c
   [ADBMobile trackState:@"Login Screen"  
                    data:nil];
   ```

In Adobe Mobile Services wird der **[!UICONTROL State Name]** in der Variablen *`View State`gemeldet und für jeden*-Aufruf wird eine Ansicht aufgezeichnet. `trackState` In anderen Analytics-Oberflächen wird **[!UICONTROL Status anzeigen]** als **[!UICONTROL Seitenname]** und Statusansichten als Seitenansichten aufgeführt.

## Sending additional data {#section_CFDB4F944496401786A145C209AB387C}

In addition to the **[!UICONTROL State Name]**, you can send additional context data with each track action call:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"logged in" forKey:@"myapp.login.LoginStatus"]; 
[ADBMobile trackState:@"Home Screen" data:contextData];
```

Kontextdatenwerte müssen benutzerdefinierte Variablen zugeordnet werden:

![](assets/map-variable-context-state.png)

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

Status werden für gewöhnlich mithilfe eines Pfadsetzungsberichts angezeigt. Auf diese Weise können Sie sehen, wie Benutzer in Ihrer App navigieren und welche Status am häufigsten angezeigt werden.

|  |  |
|--- |--- |
| Adobe Mobile Services  | Der Bericht **[!UICONTROL Status anzeigen]:** Dieser Bericht basiert auf den Pfaden, die Benutzer in Ihrer Anwendung durchlaufen. A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics  | Status können überall dort angezeigt werden, wo auch Seiten angezeigt werden können, z. B. in den Berichten **Seiten**, **[!UICONTROL Seitenansichten]** oder **Pfad[!UICONTROL .]** |
| Ad-hoc-Analysen | Status können überall dort angezeigt werden, wo auch Seiten angezeigt werden, z. B. in der Dimension **Seite**, der Metrik **[!UICONTROL Seitenansichten]** und dem Bericht **Pfad[!UICONTROL .]** |
