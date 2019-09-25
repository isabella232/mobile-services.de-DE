---
description: Informationen, die Ihnen dabei helfen, Lebenszyklusmetriken für Android zu implementieren. Lebenszyklusmetriken werden für iOS automatisch gesammelt.
keywords: Xamarin
seo-description: Informationen, die Ihnen dabei helfen, Lebenszyklusmetriken für Android zu implementieren. Lebenszyklusmetriken werden für iOS automatisch gesammelt.
seo-title: Implement lifecycle
solution: Marketing Cloud, Entwickler
title: Lebenszyklus implementieren
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
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

Unter iOS werden Lebenszyklusmetriken automatisch erfasst.

## Android

In your main activity, set the application context for the Android SDK.

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
