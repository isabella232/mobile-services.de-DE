---
description: Informationen zur Implementierung von Lebenszyklusmetriken für Android. Lebenszyklusmetriken werden automatisch für iOS erfasst.
keywords: Xamarin
solution: Experience Cloud
title: Implementieren des Lebenszyklus
uuid: 6dccc12e-8b57-4231-9c74-d47bc0ac93ba
exl-id: c76e63d1-48a5-4831-85d5-f3d3e9798a43
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 7%

---

# Implementieren des Lebenszyklus {#implement-lifecycle}

Diese Informationen helfen Ihnen bei der Implementierung von Lebenszyklusmetriken für Android.

>[!TIP]
>
>Lebenszyklusmetriken werden automatisch für iOS erfasst.

Informationen zu den Metriken und Dimensionen, die nach der Implementierung des Lebenszyklus automatisch von der mobilen Bibliothek gemessen werden können, finden Sie unter [Lebenszyklusmetriken](/help/ios/metrics.md).

## iOS

Unter iOS werden Lebenszyklusmetriken automatisch erfasst.

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
