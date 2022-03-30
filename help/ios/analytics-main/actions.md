---
description: Aktionen sind die Ereignisse in Ihrer App, die Sie messen möchten. Jede Aktion weist mindestens eine zugehörige Metrik auf, die bei jedem Vorkommen des Ereignisses erhöht wird. So könnten Sie z. B. ein neues Abonnement, jeden Artikelaufruf oder jeden Abschluss einer Ebene verfolgen. Die entsprechenden Metriken für diese Ereignisse werden als Abonnements, gelesene Artikel und abgeschlossene Ebenen konfiguriert.
solution: Experience Cloud Services,Analytics
title: App-Aktionen verfolgen
topic-fix: Developer and implementation
uuid: 62017be1-5395-4d16-bde3-4c40a2c012d4
exl-id: ff317eff-1b8e-46e1-a305-a404979447cb
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 100%

---

# App-Aktionen verfolgen {#track-app-actions}

Aktionen sind die Ereignisse in Ihrer App, die Sie messen möchten. Jede Aktion weist mindestens eine zugehörige Metrik auf, die bei jedem Vorkommen des Ereignisses erhöht wird. So könnten Sie z. B. ein neues Abonnement, jeden Artikelaufruf oder jeden Abschluss einer Ebene verfolgen. Die entsprechenden Metriken für diese Ereignisse werden als Abonnements, gelesene Artikel und abgeschlossene Ebenen konfiguriert.

Aktionen werden nicht automatisch verfolgt. Möchten Sie ein Ereignis verfolgen, müssen Sie `trackAction` aufrufen.

## Aktionen verfolgen {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zum Projekt hinzufügen* im Abschnitt [Grundlegende Implementierung und Lebenszyklus](/help/ios/getting-started/dev-qs.md).
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
   >Wenn der Code, in den Sie diesen Aufruf einfügen, aktiv ist, während die App im Hintergrund ausgeführt wird, rufen Sie `trackActionFromBackground` anstelle von `trackAction` auf.

1. Wählen Sie Ihre App in der Benutzeroberfläche von Adobe Mobile Services aus und klicken Sie auf **[!UICONTROL App-Einstellungen verwalten]**.

1. Klicken Sie auf **[!UICONTROL Variablen und Metriken verwalten]** und dann auf die Registerkarte **[!UICONTROL Benutzerdefinierte Metriken]**.

1. Weisen Sie den Kontextdatennamen, der in Ihrem Code definiert ist (z. B. `a.action=myapp.ActionName`), einem benutzerdefinierten Ereignis zu.

   ![](assets/map-event-context-data.png)

Sie können auch eine Eigenschaft für alle Aktionswerte festlegen, indem Sie eine benutzerdefinierte Eigenschaft mit einem Namen wie **[!UICONTROL Benutzerdefinierte Aktionen]** zuordnen und den Wert auf `a.action` festlegen.

![](assets/map-custom-prop.png)

## Zusätzliche Daten senden {#section_3EBE813E54A24F6FB669B2478B5661F9}

Zusätzlich zum Aktionsnamen können Sie mit jedem trackAction-Aufruf zusätzliche Kontextdaten senden:

```objective-c
NSMutableDictionary *contextData = [NSMutableDictionary dictionary]; 
[contextData setObject:@"Twitter" forKey:@"myapp.social.SocialSource"]; 
[ADBMobile trackAction:@"myapp.SocialShare" data:contextData];
```

Die Kontextdatenwerte müssen benutzerdefinierten Variablen zugeordnet werden:

![](assets/map-variable-context-action.png)

## Hintergrundaktionen verfolgen {#section_AC13013F207D4FBAAF27E4412034251E}

Wenn Sie eine Aktion im Code verfolgen, der aktiv ist, während die App im Hintergrund ausgeführt wird, rufen Sie `trackActionFromBackground` anstelle von `trackAction` auf. Auch wenn `trackActionFromBackground` eine zusätzliche Logik enthält, um zu verhindern, dass Lebenszyklusaufrufe ausgelöst werden, wenn sie nicht ausgelöst werden sollen, sind die Parameter identisch.

## Aktionsberichte {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| Schnittstelle | Bericht |
|--- |--- |
| Adobe Mobile Services | Bericht **[!UICONTROL Aktionspfade]**: Zeigen Sie die Reihenfolge an, in der Aktionen in Ihrer App aufgetreten sind. Sie können auch auf **[!UICONTROL Anpassen]** klicken, um die Aktionen in Rang- oder Trendansicht bzw. aufgeschlüsselt anzuzeigen, oder Sie nutzen Filter, um nur Aktionen für ein bestimmtes Segment anzuzeigen. |
| Marketing Reports and Analytics | Bericht **[!UICONTROL Benutzerspezifisches Ereignis]**:  Nachdem eine Aktion einem benutzerdefinierten Ereignis zugewiesen wurde, können Sie mobile Ereignisse ähnlich anzeigen wie alle anderen Analytics-Ereignisse. |
| Ad-hoc-Analysen | Bericht **[!UICONTROL Benutzerspezifisches Ereignis]**: Nachdem eine Aktion einem benutzerdefinierten Ereignis zugewiesen wurde, können Sie mobile Ereignisse ähnlich anzeigen wie alle anderen Analytics-Ereignisse. |
