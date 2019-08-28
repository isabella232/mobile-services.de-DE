---
description: Aktionen sind die Ereignisse in der App, die Sie messen möchten. Jede Aktion weist mindestens eine zugehörige Metrik auf, die bei jedem Vorkommen des Ereignisses erhöht wird. Sie möchten zum Beispiel möglicherweise jedes neue Abonnement, jedes Anzeigen eines Artikels und jeden Abschluss einer Stufe verfolgen. Die entsprechenden Metriken für die Ereignisse werden als Abonnements, gelesene Artikel und abgeschlossene Stufe konfiguriert.
seo-description: Aktionen sind die Ereignisse in der App, die Sie messen möchten. Jede Aktion weist mindestens eine zugehörige Metrik auf, die bei jedem Vorkommen des Ereignisses erhöht wird. Sie möchten zum Beispiel möglicherweise jedes neue Abonnement, jedes Anzeigen eines Artikels und jeden Abschluss einer Stufe verfolgen. Die entsprechenden Metriken für die Ereignisse werden als Abonnements, gelesene Artikel und abgeschlossene Stufe konfiguriert.
seo-title: App-Aktionen verfolgen
solution: Marketing Cloud, Analytics
title: App-Aktionen verfolgen
topic: Entwickler und Implementierung
uuid: 62017 be 1-5395-4 d 16-bde 3-4 c 40 a 2 c 012 d 4
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# App-Aktionen verfolgen {#track-app-actions}

Aktionen sind die Ereignisse in der App, die Sie messen möchten. Jede Aktion weist mindestens eine zugehörige Metrik auf, die bei jedem Vorkommen des Ereignisses erhöht wird. Sie möchten zum Beispiel möglicherweise jedes neue Abonnement, jedes Anzeigen eines Artikels und jeden Abschluss einer Stufe verfolgen. Die entsprechenden Metriken für die Ereignisse werden als Abonnements, gelesene Artikel und abgeschlossene Stufe konfiguriert.

Aktionen werden nicht automatisch verfolgt. Möchten Sie ein Ereignis verfolgen, müssen Sie `trackAction` aufrufen.

## Tracking actions {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden *Sie unter SDK und Config File to your Project* in [Core Implementation and Lifecycle](/help/ios/getting-started/dev-qs.md).
1. Importieren Sie die Bibliothek.

   ```objective-c
   #import "ADBMobile.h"
   ```

1. Wenn die zu verfolgende Aktion in Ihrer App auftritt, rufen Sie `trackAction` auf, um einen Treffer für diese Aktion zu senden.

   ```objective-c
   [ADBMobile trackAction:@"myapp.ActionName"  
                     data:nil];
   ```

   >[!TIP]
   >
   >If the code where you are adding this call might run while the app is in the background, call `trackActionFromBackground` instead of `trackAction`.

1. In the Adobe Mobile services UI, select your app and click **[!UICONTROL Manage App Settings]**.

1. Klicken Sie auf **[!UICONTROL Variablen und Metriken verwalten]** und dann auf die Registerkarte **Benutzerdefinierte Metriken[!UICONTROL .]**

1. Weisen Sie den Kontextdatennamen, der in Ihrem Code definiert ist (z. B. `a.action=myapp.ActionName`), einem benutzerdefinierten Ereignis zu.

   ![](assets/map-event-context-data.png)

You can also set a prop to hold all action values by mapping a custom prop with a name like **[!UICONTROL Custom Actions]** and setting the value to `a.action`.

![](assets/map-custom-prop.png)

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Zusätzlich zum Aktionsnamen können Sie mit jedem trackAction-Aufruf zusätzliche Kontextdaten senden:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"Twitter" forKey:@"myapp.social.SocialSource"]; 
[ADBMobile trackAction:@"myapp.SocialShare" data:contextData];
```

Kontextdatenwerte müssen benutzerdefinierte Variablen zugeordnet werden:

![](assets/map-variable-context-action.png)

## Tracking background actions {#section_AC13013F207D4FBAAF27E4412034251E}

Wenn Sie eine Aktion im Code verfolgen, der aktiv ist, während die App im Hintergrund ausgeführt wird, rufen Sie `trackActionFromBackground` anstelle von `trackAction` auf. Auch wenn `trackActionFromBackground` eine zusätzliche Logik enthält, um zu verhindern, dass Lebenszyklusaufrufe ausgelöst werden, wenn sie nicht ausgelöst werden sollen, sind die Parameter identisch.

## Action reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| Schnittstelle | Bericht |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL Bericht Aktionspfade]**: Zeigen Sie die Reihenfolge an, in der Aktionen in Ihrer App aufgetreten sind. Sie können auch auf **[!UICONTROL Anpassen]klicken, um die Aktionen in Rang- oder Trendansicht bzw. aufgeschlüsselt anzuzeigen, oder Sie nutzen Filter, um nur Aktionen für ein bestimmtes Segment anzuzeigen.** |
| Marketing Reports &amp; Analysen | **[!UICONTROL Bericht Benutzerspezifisches Ereignis]**:  Nachdem eine Aktion einem benutzerdefinierten Ereignis zugewiesen wurde, können Sie mobile Ereignisse ähnlich anzeigen wie alle anderen Analytics-Ereignisse. |
| Ad-hoc-Analysen | **[!UICONTROL Bericht Benutzerspezifisches Ereignis]**: Nachdem eine Aktion einem benutzerdefinierten Ereignis zugewiesen wurde, können Sie mobile Ereignisse ähnlich anzeigen wie alle anderen Analytics-Ereignisse. |