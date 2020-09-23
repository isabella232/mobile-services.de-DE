---
description: Die Android-SDK-Version 4.5 enthält eine neue Erweiterung von Android, die Ihnen das Erfassen der Nutzungsdaten von Ihrer Android Wearable App ermöglicht.
seo-description: Die Android-SDK-Version 4.5 enthält eine neue Erweiterung von Android, die Ihnen das Erfassen der Nutzungsdaten von Ihrer Android Wearable App ermöglicht.
seo-title: 'Android Wearables: Erste Schritte'
solution: Experience Cloud,Analytics
title: 'Android Wearables: Erste Schritte'
topic: Developer and implementation
uuid: bfe5d41e-b17c-4634-80ac-7a38671ecb81
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 100%

---


# Android Wearables: Erste Schritte{#android-wearables-getting-started}

Die Android-SDK-Version 4.5 enthält eine neue Erweiterung von Android, die Ihnen das Erfassen der Nutzungsdaten von Ihrer Android Wearable App ermöglicht.

## SDK für eine Handheld App (Android Studio) konfigurieren {#section_262237484EC44C58953891B105F0D000}

Weitere Informationen zum Importieren des SDK in Ihr Projekt finden Sie unter [Grundlegende Implementierung und Lebenszyklus](/help/android/getting-started/dev-qs.md).

1. Fügen Sie die Datei `ADBMobileConfig.json` in den Ordner assets des Projekts ein.
1. Fügen Sie die Datei `adobeMobileLibrary-*.jar` zum Ordner „libs“ hinzu oder stellen Sie sicher, dass im Projekt ein Verweis auf die Datei enthalten ist.

   >[!TIP]
   >
   >Möglicherweise müssen Sie das Gradle-Projekt synchronisieren, nachdem Sie die Datei `.jar` hinzugefügt haben.

1. Lassen Sie in der Methode `onCreate` zu, dass das SDK mithilfe von `Config.setContext` auf den Anwendungskontext zugreift:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main); 
   
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext()); 
   }
   ```

1. Fügen Sie der Datei `AndroidManifest.xml` den folgenden Code hinzu:

   ```java
       <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /> 
       <uses-permission android:name="android.permission.INTERNET" /> 
       <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
   
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. Stellen Sie sicher, dass Ihr Projekt die Google Play Services-Bibliothek enthält.
1. Implementieren Sie `WearableListenerService` oder fügen Sie den entsprechenden Code zu Ihrem `WearableListenerService` hinzu:

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onMessageReceived(MessageEvent messageEvent) { 
           super.onMessageReceived(messageEvent); 
       } 
   
       private GoogleApiClient mGoogleApiClient; 
   
       @Override 
       public void onCreate() { 
           super.onCreate(); 
           mGoogleApiClient = new GoogleApiClient.Builder(this) 
                   .addApi(Wearable.API) 
                   .build(); 
           mGoogleApiClient.connect(); 
       } 
       @Override 
       public void onDestroy() { 
           super.onDestroy(); 
           mGoogleApiClient.disconnect(); 
       } 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerHandheld.onDataChanged(dataEvents, mGoogleApiClient, this); 
       } 
   }
   ```

1. Fügen Sie `WearListenerService` der Datei `AndroidManifest.xml` hinzu:

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```

## SDK für eine Wearable App (Android Studio) konfigurieren {#section_2268EC03E20B4A228A28BDCFEA2E9AE4}

1. Führen Sie eine der folgenden Aufgaben aus:

   * Fügen Sie dieselbe Datei `ADBMobileConfig.json` in den Ordner „assets“ Ihres Wearable-Projekts ein.
   * Ändern Sie die Gradle-Konfiguration so, dass die Datei `ADBMobileConfig.json` im Ordner „assets“ der Handheld App verwendet wird:

      ```java
      android { 
      
          sourceSets { 
              main { 
                  assets.srcDirs = ['src/main/assets','../mobile/src/main/assets'] 
              } 
         } 
      }
      ```

1. Fügen Sie die Datei `adobeMobileLibrary-*.jar` zum Ordner „libs“ hinzu oder stellen Sie sicher, dass im Projekt ein Verweis auf die Datei enthalten ist.

   Möglicherweise müssen Sie das Gradle-Projekt synchronisieren, nachdem Sie die .jar-Datei hinzugefügt haben.

1. Lassen Sie in der Methode `onCreate` zu, dass das SDK mithilfe von `Config.setContext` auf den Anwendungskontext zugreift:

   ```java
   @Override 
   public void onCreate(Bundle savedInstanceState) { 
       super.onCreate(savedInstanceState); 
       setContentView(R.layout.main);      
       // Allow the SDK access to the application context 
       Config.setContext(this.getApplicationContext(), Config.ApplicationType.APPLICATION_TYPE_WEARABLE); 
   }
   ```

1. Fügen Sie folgenden Code zu `AndroidManifest.xml` hinzu:

   ```java
   <application> 
   ....... 
   <meta-data android:name="com.google.android.gms.version" 
               android:value="@integer/google_play_services_version" /> 
   </application>
   ```

1. Stellen Sie sicher, dass Ihr Projekt die Google Play Services-Bibliothek enthält.
1. Implementieren Sie `WearableListenerService` oder fügen Sie den entsprechenden Code zu Ihrem `WearableListenerService` hinzu:

   ```java
   public class WearListenerService extends WearableListenerService { 
   
       @Override 
       public void onDataChanged(com.google.android.gms.wearable.DataEventBuffer dataEvents) { 
           DataListenerWearable.onDataChanged(dataEvents); 
       } 
   
   }
   ```

1. Fügen Sie `WearListenerService` der Datei `AndroidManifest.xml` hinzu:

   ```java
   If you are using Google Play Services  < 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                   <action android:name="com.google.android.gms.wearable.BIND_LISTENER" /> 
               </intent-filter> 
       </service> 
   </application> 
   If you are using Google Play Services >= 8.2 
   <application> 
       ...... 
        <service 
               android:name=".WearListenerService" > 
               <intent-filter> 
                     <action android:name="com.google.android.gms.wearable.DATA_CHANGED" /> 
                    <data android:scheme="wear" android:host="*" android:pathPrefix="/abdmobile" /> 
               </intent-filter> 
       </service> 
   </application> 
   Please find more information from google's blog https://android-developers.googleblog.com/2016/04/deprecation-of-bindlistener.html. 
   Permalink Edit
   ```

