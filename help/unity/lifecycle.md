---
description: Metriken und Dimensionen messen, die automatisch von der mobilen Bibliothek gemessen werden können
keywords: Unity
solution: Experience Cloud Services
title: Implementieren des Lebenszyklus
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
exl-id: eca0cebb-6c69-4b0f-b003-c7fc422d0383
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 7%

---

# Implementieren des Lebenszyklus{#implement-lifecycle}

Weitere Informationen zu den Metriken und Dimensionen, die nach der Implementierung des Lebenszyklus automatisch von der mobilen Bibliothek gemessen werden können, finden Sie unter [Lebenszyklusmetriken in Android](/help/android/metrics.md) oder [Lebenszyklus in iOS](/help/ios/metrics.md).

## iOS

Lebenszyklusmetriken werden automatisch in iOS erfasst.

## Android

In Ihrem Unity-Skript legen Sie den Anwendungskontext für das Android-SDK fest. Fügen Sie den folgenden Code zum `Awake()` Funktion Ihrer FIRST-Szene:

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
