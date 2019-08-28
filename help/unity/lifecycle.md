---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Lebenszyklus implementieren
solution: Marketing Cloud, Entwickler
title: Lebenszyklus implementieren
uuid: 7 ff 2 c 194-569 c -42 a 6-922 d-dccd 2 aa 9 eb 8 d
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# Lebenszyklus implementieren{#implement-lifecycle}

Weitere Informationen zu Metriken und Dimensionen, die nach der Implementierung des Lebenszyklus automatisch von der mobilen Bibliothek gemessen werden können, finden Sie unter [Lebenszyklusmetriken in Android](/help/android/metrics.md) oder [Lebenszyklus in ios](/help/ios/metrics.md).

## iOS

Lebenszyklusmetriken werden automatisch in ios erfasst.

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

