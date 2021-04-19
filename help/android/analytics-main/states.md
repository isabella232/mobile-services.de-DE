---
description: Status sind die verschiedenen Bildschirme oder Ansichten in der Anwendung.
seo-description: Status sind die verschiedenen Bildschirme oder Ansichten in der Anwendung.
seo-title: App-Zustände verfolgen
solution: Experience Cloud,Analytics
title: App-Zustände verfolgen
topic-fix: Developer and implementation
uuid: 69c99d05-5816-4c86-97c5-d218dc26c129
exl-id: ee1ea716-ee72-4c28-92cb-26df1327f5c6
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 100%

---

# App-Zustände verfolgen {#track-app-states}

Status sind die verschiedenen Bildschirme oder Ansichten in der Anwendung.

Jedes Mal, wenn ein neuer Status in der Anwendung angezeigt wird (z. B. wenn ein Benutzer von der Startseite zum Newsfeed navigiert), wird ein `trackState`-Aufruf gesendet. Unter Android wird `trackState` für gewöhnlich jedes Mal aufgerufen, wenn eine neue Aktivität geladen wird.

## Status verfolgen {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zu Ihrem IntelliJ IDEA- oder Eclipse-Projekt hinzufügen* in [Grundlegende Implementierung und Lebenszyklus](/help/android/getting-started/dev-qs.md).

1. Importieren Sie die Bibliothek:

   ```java
   import com.adobe.mobile.*;
   ```

1. Rufen Sie in der Funktion `onCreate` `trackState` auf, um einen Treffer für diese Statusansicht zu senden:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Adobe - track when this state loads 
       Analytics.trackState("State Name", null); 
   }
   ```

Der `"State Name"` wird dann in der Variablen `View State` in Adobe Mobile Services gemeldet und für jeden `trackState`-Aufruf wird eine Ansicht aufgezeichnet. In anderen Analytics-Schnittstellen wird `View State` als `Page Name` und `state views` als `page views` gemeldet.

## Zusätzliche Daten senden {#section_CFDB4F944496401786A145C209AB387C}

Zusätzlich zu `"State Name"` können Sie bei jedem Verfolgungsaktionsaufruf zusätzliche Kontextdaten senden:

```java
@Override 
public void onCreate(Bundle savedInstanceState) { 
    super.onCreate(savedInstanceState); 
    setContentView(R.layout.main); 
  
    // Adobe - track when this state loads 
    HashMap<String, Object> exampleContextData = new HashMap<String, Object>(); 
    exampleContextData.put("myapp.login.LoginStatus", "logged in"); 
    Analytics.trackState("Home Screen", exampleContextData); 
}
```

Die Kontextdatenwerte müssen benutzerdefinierten Variablen in Adobe Mobile Services zugeordnet werden:

![](assets/map-variable-context-state.png)

## App-Statusberichte {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

Status werden für gewöhnlich mithilfe eines Pfadsetzungsberichts angezeigt. Auf diese Weise können Sie sehen, wie Anwender in Ihrer App navigieren und welche Status am häufigsten angezeigt werden.

|  |  |
|--- |--- |
| Adobe Mobile Services | Der Bericht **[!UICONTROL Status anzeigen]**: Dieser Bericht basiert auf den Pfaden, die Benutzer in Ihrer Anwendung durchlaufen. Ein Beispielpfad ist  **[!UICONTROL Home]** > **[!UICONTROL Einstellungen]** > **[!UICONTROL Feed]**. |
| Adobe Analytics | Status können überall dort angezeigt werden, wo auch Seiten angezeigt werden können, z. B. in den Berichten **[!UICONTROL Seiten]**, **[!UICONTROL Seitenansichten]** oder **[!UICONTROL Pfad]**. |
| Ad-hoc-Analysen | Status können überall dort angezeigt werden, wo auch Seiten angezeigt werden, z. B. in der Dimension **[!UICONTROL Seite]**, der Metrik **[!UICONTROL Seitenansichten]** und dem Bericht **[!UICONTROL Pfad]**. |
