---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Lebenszyklus implementieren
solution: Marketing Cloud, Entwickler
title: Lebenszyklus implementieren
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Lebenszyklus implementieren{#implement-lifecycle}

Weitere Informationen zu den Metriken und Dimensionen, die nach der Implementierung des Lebenszyklus automatisch von der mobilen Bibliothek gemessen werden können, finden Sie unter [Lebenszyklusmetriken in Android](/help/android/metrics.md) oder [Lebenszyklus in iOS](/help/ios/metrics.md).

## iOS

Lebenszyklusmetriken werden in iOS automatisch erfasst.

## Android

Legen Sie im Unity-Skript den Anwendungskontext für das Android-SDK fest. Add the following code to the `Awake()` function of your FIRST scene:

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

Zum Erfassen der Lebenszyklusmetriken fügen Sie den folgenden Code zu allen Szenenskripten hinzu:

```java
void OnEnable()
 {
  ...
  ADBMobile.CollectLifecycleData (); 
  ...
 }
 
 void OnDisable()
 {
  ...
  ADBMobile.PauseCollectingLifecycleData (); 
  ...
 }
  
 void OnApplicationPause(bool isPaused) 
 {
  ...
  if (isPaused) {
   ADBMobile.PauseCollectingLifecycleData (); 
  }  
  else {
   ADBMobile.CollectLifecycleData(); 
  }
  ...
 }
```

