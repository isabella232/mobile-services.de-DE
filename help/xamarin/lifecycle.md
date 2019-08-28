---
description: Informationen, die Ihnen dabei helfen, Lebenszyklusmetriken für Android zu implementieren. Lebenszyklusmetriken werden für iOS automatisch gesammelt.
keywords: Xamarin
seo-description: Informationen, die Ihnen dabei helfen, Lebenszyklusmetriken für Android zu implementieren. Lebenszyklusmetriken werden für iOS automatisch gesammelt.
seo-title: Lebenszyklus implementieren
solution: Marketing Cloud, Entwickler
title: Lebenszyklus implementieren
uuid: 6 dccc 12 e -8 b 77-4231-9 c 74-d 47 bc 0 ac 93 ba
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Implement lifecycle {#implement-lifecycle}

Anhand dieser Informationen können Sie Lebenszyklusmetriken für Android implementieren.

>[!TIP]
>
>Lebenszyklusmetriken werden für iOS automatisch gesammelt.

For the metrics and dimensions that can be measured automatically by the mobile library after lifecycle is implemented, see [Lifecycle Metrics](/help/ios/metrics.md).

## iOS

In ios werden Lebenszyklusmetriken automatisch erfasst.

## Android

Legen Sie in Ihrer Hauptaktivität den Anwendungskontext für das Android-SDK fest.

```java
protected override void OnCreate (Bundle bundle) 
{
    ... 
    Config.SetContext (Application.Context); 
    ... 
}
```

Implementieren Sie in jeder Aktivität Lebenszyklusaufrufe.

```java
protected override void OnResume()
{
    ...
    Config.CollectLifecycleData (this);
    ...
}
protected override void OnPause() 
{
    ...
    Config.PauseCollectingLifecycleData ();
    ...
}
```
