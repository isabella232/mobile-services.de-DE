---
description: 'null'
keywords: Unity
seo-description: 'null'
seo-title: Implementieren des Lebenszyklus
solution: Experience Cloud
title: Implementieren des Lebenszyklus
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 11%

---


# Implementieren des Lebenszyklus{#implement-lifecycle}

Weitere Informationen zu den Metriken und Dimensionen, die nach der Implementierung des Lebenszyklus automatisch von der mobilen Bibliothek gemessen werden können, finden Sie unter [Lebenszyklusmetriken in Android](/help/android/metrics.md) oder [Lebenszyklus in iOS](/help/ios/metrics.md).

## iOS

Lebenszyklusmetriken werden in iOS automatisch erfasst.

## Android

Im Unity-Skript legen Sie den Anwendungskontext für das Android-SDK fest. hinzufügen Sie den folgenden Code in die `Awake()` Funktion Ihrer ERSTEN Szene ein:

```java
void Awake()
 {
  ...
  ADBMobile.SetContext();
  ...
 }
```

Um Lebenszyklusmetriken zu erfassen, fügen Sie allen Szenenskripten den folgenden Code hinzu:

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

