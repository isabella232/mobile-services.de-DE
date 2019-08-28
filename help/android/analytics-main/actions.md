---
description: Aktionen sind die Ereignisse in Ihrer Android-App, die Sie messen möchten.
seo-description: Aktionen sind die Ereignisse in Ihrer Android-App, die Sie messen möchten.
seo-title: App-Aktionen verfolgen
solution: Marketing Cloud, Analytics
title: App-Aktionen verfolgen
topic: Entwickler und Implementierung
uuid: fe 01 c 1 df-f 6 bb -4 b 32-b 3 ef -959 d 2 c 724 af 6
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# App-Aktionen verfolgen {#track-app-actions}

Aktionen sind die Ereignisse in Ihrer Android-App, die Sie messen möchten.

Jede Aktion weist mindestens eine zugehörige Metrik auf, die bei jedem Vorkommen des Ereignisses erhöht wird. So könnten Sie z. B. einen `trackAction`-Aufruf für jedes neue Abonnement, jeden Artikelaufruf oder jeden Levelabschluss senden. Aktionen werden nicht automatisch verfolgt. Sie müssen `trackAction` aufrufen, wenn ein zu verfolgendes Ereignis auftritt, und die Aktion dann einem benutzerdefinierten Ereignis zuordnen.

## Tracking actions {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Config File to your intellij IDEA oder Eclipse Project* in [Core Implementation and Lifecycle](/help/android/getting-started/dev-qs.md).

1. Importieren Sie die Bibliothek:

   ```java
   import com.adobe.mobile.*;
   ```

1. Wenn die zu verfolgende Aktion in Ihrer App auftritt, rufen Sie `trackAction` auf, um einen Treffer für diese Aktion zu senden:

   ```java
   Analytics.trackAction("myapp.ActionName", null);
   ```

1. Wählen Sie Ihre App in Adobe Mobile Services UI aus und klicken Sie auf **[!UICONTROL App-Verwaltungseinstellungen]**.
1. Klicken Sie auf **[!UICONTROL Variablen und Metriken verwalten]** und dann auf die Registerkarte **Benutzerdefinierte Metriken[!UICONTROL .]**

1. Weisen Sie den Kontextdatennamen, der in Ihrem Code definiert ist (z. B. `myapp.ActionName`), einem benutzerdefinierten Ereignis zu.

   ![](assets/map-event-context-data.png)

You can also set a prop to hold all action values by mapping a custom prop with a name like **[!UICONTROL Custom Actions]** and setting the value to `a.action`.

![](assets/map-custom-prop.png)

## Sending additional data {#section_3EBE813E54A24F6FB669B2478B5661F9}

Zusätzlich zum Aktionsnamen können Sie bei jedem Verfolgungsaktionsaufruf zusätzliche Kontextdaten senden:

```java
HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
exampleContextData.put("myapp.social.SocialSource", "Twitter"); 
Analytics.trackAction("myapp.SocialShare", exampleContextData);
```

Die Kontextdatenwerte müssen benutzerdefinierten Variablen in Adobe Mobile Services zugeordnet werden:

![](assets/map-variable-context-action.png)

## Action reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

| Schnittstelle | Bericht |
|--- |--- |
| Adobe Mobile Services | **[!UICONTROL Bericht Aktionspfade]**:  Zeigen Sie die Reihenfolge an, in der Aktionen in Ihrer App aufgetreten sind. Sie können auch auf **[!UICONTROL Anpassen]klicken, um die Aktionen in Rang- oder Trendansicht bzw. aufgeschlüsselt anzuzeigen, oder Sie nutzen Filter, um nur Aktionen für ein bestimmtes Segment anzuzeigen.** |
| Marketing Reports &amp; Analysen | **[!UICONTROL Bericht Benutzerspezifisches Ereignis]**:  Nachdem eine Aktion einem benutzerdefinierten Ereignis zugewiesen wurde, können Sie mobile Ereignisse ähnlich anzeigen wie alle anderen Analytics-Ereignisse. |
| Ad-hoc-Analysen | **[!UICONTROL Bericht Benutzerspezifisches Ereignis]**:  Nachdem eine Aktion einem benutzerdefinierten Ereignis zugewiesen wurde, können Sie mobile Ereignisse ähnlich anzeigen wie alle anderen Analytics-Ereignisse. |

