---
description: Status sind die verschiedenen Bildschirme oder Ansichten in der Anwendung.
seo-description: Status sind die verschiedenen Bildschirme oder Ansichten in der Anwendung.
seo-title: App-Zustände verfolgen
solution: Marketing Cloud, Analytics
title: App-Zustände verfolgen
topic: Entwickler und Implementierung
uuid: 69 c 99 d 05-5816-4 c 86-97 c 5-d 218 dc 26 c 129
translation-type: tm+mt
source-git-commit: 3cc97443fabcb9ae9e09b998801bbb57785960e0

---


# App-Zustände verfolgen {#track-app-states}

Status sind die verschiedenen Bildschirme oder Ansichten in der Anwendung.

Jedes Mal, wenn ein neuer Status in der Anwendung angezeigt wird (z. B. wenn ein Benutzer von der Startseite zum Newsfeed navigiert), wird ein `trackState`-Aufruf gesendet. Unter Android wird `trackState` für gewöhnlich jedes Mal aufgerufen, wenn eine neue Aktivität geladen wird.

## Tracking states {#section_380DF56C4EE4432A823940E4AE4C9E91}

1. Fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus.

   Weitere Informationen finden Sie unter *SDK und Config File to your intellij IDEA oder Eclipse Project* in [Core Implementation and Lifecycle](/help/android/getting-started/dev-qs.md).

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

The `"State Name"` is reported in the `View State` variable in Adobe Mobile services, and a view is recorded for each `trackState` call. In anderen Analytics-Schnittstellen `View State` wird berichtet und `Page Name``state views` erscheint als `page views`.

## Send additional data {#section_CFDB4F944496401786A145C209AB387C}

In addition to the `"State Name"`, you can send additional context data with each track action call:

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

## App state reporting {#section_0F6A54AB7A3F42C9BB042D86A0FC4630}

Status werden für gewöhnlich mithilfe eines Pfadsetzungsberichts angezeigt. Hier können Sie ermitteln, wie Benutzer durch Ihre App navigieren und welche Status am häufigsten angezeigt werden.

|  |  |
|--- |--- |
| Adobe Mobile Services  | Der Bericht **[!UICONTROL Status anzeigen]:** Dieser Bericht basiert auf den Pfaden, die Benutzer in Ihrer Anwendung durchlaufen. A sample path is  **[!UICONTROL Home]**  &gt;  **[!UICONTROL Settings]**  &gt; **[!UICONTROL Feed]**. |
| Adobe Analytics  | Status können überall dort angezeigt werden, wo auch Seiten angezeigt werden können, z. B. in den Berichten **Seiten**, **[!UICONTROL Seitenansichten]** oder **Pfad[!UICONTROL .]** |
| Ad-hoc-Analysen | Status können überall dort angezeigt werden, wo auch Seiten angezeigt werden, z. B. in der Dimension **Seite**, der Metrik **[!UICONTROL Seitenansichten]** und dem Bericht **Pfad[!UICONTROL .]** |


