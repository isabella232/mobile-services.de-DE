---
description: Mithilfe dieser Informationen können Sie ermitteln, wie Abstürze verfolgt werden und wie Sie am besten mit fälschlich gemeldeten Abstürzen umgehen.
seo-description: Mithilfe dieser Informationen können Sie ermitteln, wie Abstürze verfolgt werden und wie Sie am besten mit fälschlich gemeldeten Abstürzen umgehen.
seo-title: App-Abstürze verfolgen
solution: Experience Cloud,Analytics
title: App-Abstürze verfolgen
topic-fix: Developer and implementation
uuid: 3ab98c14-ccdf-4060-ad88-ec07c1c6bf07
exl-id: d8d59b4e-0231-446d-9ba1-8a9809be9c61
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 100%

---

# Nachverfolgen von App-Abstürzen {#track-app-crashes}

Mithilfe dieser Informationen können Sie ermitteln, wie Abstürze verfolgt werden und wie Sie am besten mit fälschlich gemeldeten Abstürzen umgehen.

>[!TIP]
>
>App-Abstürze werden als Teil der Lebenszyklusmetriken verfolgt. Bevor Sie Abstürze verfolgen können, fügen Sie die Bibliothek zu Ihrem Projekt hinzu und implementieren Sie den Lebenszyklus. Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zu Ihrem IntelliJ IDEA- oder Eclipse-Projekt hinzufügen* in [Grundlegende Implementierung und Lebenszyklus](/help/android/getting-started/dev-qs.md).

Wenn die Lebenszyklusmetriken implementiert sind, wird `Config.collectLifecycleData` in der Methode `OnResume` jeder Aktivität aufgerufen. In der Methode `onPause` wird `Config.pauseCollectingLifeCycleData` aufgerufen.

In `pauseCollectingLifeCycleData` wird eine Markierung gesetzt, um die ordnungsgemäße Beendigung anzuzeigen. Wenn die App erneut gestartet oder wieder aufgenommen wird, überprüft `collectLifecycleData` diese Markierung. Wenn die App laut Flag-Status nicht ordnungsgemäß beendet wurde, werden mit dem nächsten Aufruf `a.CrashEvent`-Kontextdaten gesendet und es wird ein Absturzereignis gemeldet.

Um präzise Absturzberichte zu gewährleisten, müssen Sie `pauseCollectingLifeCycleData` in der Methode `onPause` jeder Aktivität aufrufen. Um zu verstehen, warum dies wichtig ist, sehen Sie hier den Android-Aktivitätslebenszyklus:

![](assets/android-lifecycle.png)

Weitere Informationen zum Android-Aktivitätslebenszyklus finden Sie unter [Aktivitäten](https://developer.android.com/guide/components/activities.html).

*Diese Darstellung des Android-Lebenszyklus wurde [vom Android Open Source Project erstellt und veröffentlicht](https://source.android.com/) und wird gemäß [Creative Commons 2.5 Attribution License](https://creativecommons.org/licenses/by/2.5/) verwendet.*

## Wie kann es passieren, dass fälschlicherweise ein Absturz gemeldet wird?

1. Wenn Sie mit einer IDE debuggen, z. B. mit Android Studio, und die App von der IDE aus erneut startet, während sich die App im Vordergrund befindet, führt dies zu einem Absturz.

   >[!TIP]
   >
   >Sie können solche Abstürze vermeiden, indem Sie die App im Hintergrund ausführen, bevor Sie sie erneut über die IDE starten.

1. Wenn die letzte Vordergrundaktivität Ihrer App in den Hintergrund versetzt wird, `Config.pauseCollectingLifecycleData();` in `onPause` nicht aufgerufen wird und Ihre App manuell geschlossen oder vom Betriebssystem beendet wird, kommt es beim nächsten Start zu einem Absturz.

## Wie gehe ich mit Fragmenten um?

Fragmente verfügen über App-Lebenszyklusereignisse, die Aktivitäten ähnlich sind. Ein Fragment kann jedoch nicht aktiv sein, ohne mit einer Aktivität verbunden zu sein.

>[!IMPORTANT]
>
>Sie müssen sich auf die Lebenszyklusereignisse verlassen, mit denen die enthaltenen Aktivitäten Ihren Code ausführen können. Dies erfolgt über die übergeordnete Ansicht des Fragments.

## (Optional) Lebenszyklus-Rückrufe für Aktivitäten implementieren

Seit API-Version 14 erlaubt Android globale Lebenszyklus-Rückrufe für Aktivitäten. Weitere Informationen dazu finden Sie unter [Application](https://developer.android.com/reference/android/app/Application).

Sie können diese Rückrufe verwenden, um sicherzustellen, dass alle Aktivitäten `collectLifecycleData()` und `pauseCollectingLifecycleData()` ordnungsgemäß aufrufen. Sie benötigen diesen Code nur in Ihrer Hauptaktivität und anderen Aktivitäten, in der Ihre App möglicherweise gestartet wird:

```js
import com.adobe.mobile.Config; 
  
public class MainActivity extends Activity { 
... 
    @Override 
    protected void onCreate(Bundle savedInstanceState) { 
        super.onCreate(savedInstanceState); 
        setContentView(R.layout.activity_main); 
  
        getApplication().registerActivityLifecycleCallbacks(new Application.ActivityLifecycleCallbacks() { 
            @Override 
            public void onActivityResumed(Activity activity) { 
                Config.setContext(activity.getApplicationContext()); 
                Config.collectLifecycleData(activity); 
            } 
  
            @Override 
            public void onActivityPaused(Activity activity) {     
                Config.pauseCollectingLifecycleData(); 
            } 
    
            // the following methods aren't needed for our lifecycle purposes, but are required to be implemented 
            // by the ActivityLifecycleCallbacks object 
            @Override 
            public void onActivityCreated(Activity activity, Bundle savedInstanceState) {} 
            @Override 
            public void onActivityStarted(Activity activity) {} 
            @Override 
            public void onActivityStopped(Activity activity) {} 
            @Override 
            public void onActivitySaveInstanceState(Activity activity, Bundle outState) {} 
            @Override 
            public void onActivityDestroyed(Activity activity) {} 
        }); 
    } 
... 
}
```

Um mithilfe von `Config.collectLifecycleData(Activity activity`, `Map<String`, `Object> contextData)` zusätzliche Kontextdaten mit Ihrem Lebenszyklusaufruf zu senden, müssen Sie die Methode `onResume` für diese Aktivität überschreiben und sicherstellen, dass Sie `super.onResume()` aufrufen, nachdem Sie manuell `collectLifecycleData` aufgerufen haben.

```js
@Override 
protected void onResume() { 
    HashMap<String, Object> cdata = new HashMap<>(); 
    cdata.put("someKey", "someValue"); 
    Config.collectLifecycleData(this, cdata); 
  
    super.onResume(); 
}
```
