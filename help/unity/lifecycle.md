---
description: Metriken und Dimensionen messen, die automatisch mit der mobilen Bibliothek gemessen werden können
keywords: Unity
solution: Experience Cloud
title: Implementieren des Lebenszyklus
uuid: 7ff2c194-569c-42a6-922d-dccd2aa9eb8d
exl-id: eca0cebb-6c69-4b0f-b003-c7fc422d0383
translation-type: tm+mt
source-git-commit: b9ee49ba26d4726b1f97ef36f5c2e9923361b1ee
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 7%

---

# Implementieren des Lebenszyklus{#implement-lifecycle}

Weitere Informationen zu den Metriken und Dimensionen, die nach der Implementierung des Lebenszyklus automatisch von der mobilen Bibliothek gemessen werden können, finden Sie unter [Lebenszyklusmetriken in Android](/help/android/metrics.md) oder [Lebenszyklus in iOS](/help/ios/metrics.md).

## iOS

Lebenszyklusmetriken werden in iOS automatisch erfasst.

## Android

Im Unity-Skript legen Sie den Anwendungskontext für das Android-SDK fest. hinzufügen Sie den folgenden Code in die Funktion `Awake()` Ihrer ERSTEN Szene ein:

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
