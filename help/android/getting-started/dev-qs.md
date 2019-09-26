---
description: Diese Information unterstützt Sie beim Implementieren der Android-Bibliothek und Erfassen von Lebenszyklusmetriken, wie z. B. Starts, Upgrades, Sitzungen, erreichte Benutzer usw.
keywords: android;library;mobile;sdk
seo-description: Diese Information unterstützt Sie beim Implementieren der Android-Bibliothek und Erfassen von Lebenszyklusmetriken, wie z. B. Starts, Upgrades, Sitzungen, erreichte Benutzer usw.
seo-title: Grundlegende Implementierung und Lebenszyklus
solution: Marketing Cloud,Analytics
title: Grundlegende Implementierung und Lebenszyklus
topic: Entwickler und Implementierung
uuid: af4d11ac-8245-46a0-9b3a-4a0a29cfbb2
translation-type: tm+mt
source-git-commit: c4da3599c858bfbccb7af954df75f94eb7d8e99a

---


# Core implementation and lifecycle {#core-implementation-and-lifecycle}

Diese Information unterstützt Sie beim Implementieren der Android-Bibliothek und Erfassen von Lebenszyklusmetriken, wie z. B. Starts, Upgrades, Sitzungen, erreichte Benutzer usw.

## SDK herunterladen {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>Zum Herunterladen des SDK müssen Sie Android 2.2 oder höher verwenden.

1. Führen Sie die Schritte in den folgenden Abschnitten aus, um eine Entwicklungsberichtssuite einzurichten und eine vorinstallierte Version der Konfigurationsdatei herunterzuladen:

   * [Report Suite erstellen](/help/android/getting-started/requirements.md)
   * [SDK herunterladen](/help/android/getting-started/requirements.md)

1. Laden Sie die `[Your_App_Name_]AdobeMobileLibrary-4.*-Android.zip` Datei herunter und dekomprimieren Sie sie und stellen Sie sicher, dass die folgenden Softwarekomponenten vorhanden sind:

   * `adobeMobileLibrary.jar`, die Bibliothek, die mit Android-Geräten und Simulatoren verwendet wird.

   * `ADBMobileConfig.json`: die SDK-Konfigurationsdatei, die für Ihre App angepasst ist.
   >[!IMPORTANT]
   >
   >If you download the SDK outside the Adobe Mobile services UI, the `ADBMobileConfig.json` file must be manually configured. If you are new to Analytics and the Mobile SDK, and you want to set up a development report suite and download a pre-populated version of the configuration file, see [Before You Start](/help/android/getting-started/requirements.md).

## Add the SDK and config file to your IntelliJ IDEA or Eclipse project {#section_B89510FBB4C646AEA73A185B966E54D3}

**IntelliJ IDEA project**

So fügen Sie das SDK und die Konfigurationsdatei zu Ihrem Projekt hinzu:

1. Add the `ADBMobileConfig.json` file to the `assets` folder in your project.

1. Klicken Sie im Bereich „Project Navigation“ (Projektnavigation) mit der rechten Maustaste auf das Projekt.
1. Wählen Sie **[!UICONTROL Moduleinstellungen öffnen]**.
1. Wählen Sie unter **[!UICONTROL Projekteinstellungen]** die Option **[!UICONTROL Bibliotheken]**.
1. Click the **[!UICONTROL +]** icon to add a new library.
1. Wählen Sie **[!UICONTROL Java]** und navigieren Sie zur Datei `adobeMobileLibrary.jar`.
1. Wählen Sie die Module aus, in denen Sie die Mobilbibliothek verwenden möchten.
1. Klicken Sie auf **[!UICONTROL Anwenden]** und anschließend auf **[!UICONTROL OK], um das Fenster Moduleinstellungen zu schließen.**

**Eclipse-Projekt**

So fügen Sie das SDK und die Konfigurationsdatei zu Ihrem Projekt hinzu:

1. Add the `ADBMobileConfig.json` file to the `assets` folder in your project.
1. In **[!UICONTROL Eclipse IDE]**, right-click the project name.
1. Click  **[!UICONTROL Build Path]** &gt; **[!UICONTROL Add External Archives]**.
1. Auswählen `adobeMobileLibrary.jar`.
1. Klicken Sie auf **[!UICONTROL Öffnen]**.
1. Right-click the project again and select **[!UICONTROL Build Path]** &gt; **[!UICONTROL Configure Build Path]**.
1. Stellen Sie sicher, dass auf der Registerkarte **[!UICONTROL Sortieren und exportieren]** **`adobeMobileLibrary.jar`ausgewählt ist.**

## Add app permissions {#section_2EAF73ABF6424647B219A63B33B02CD5}

Die AppMeasurement-Bibliothek erfordert folgende Berechtigungen, um Daten zu senden und Offline-Verfolgungsaufrufe aufzuzeichnen:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Ergänzen Sie die Datei `AndroidManifest.xml` im Projektverzeichnis der Anwendung um die folgenden Zeilen, um diese Berechtigungen hinzuzufügen:

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## Set the application context {#set-application-context}

Der folgende Code sollte der `onCreate` Methode Ihrer Hauptaktivität hinzugefügt werden:

```java
   @Override
   public void onCreate(BundlesavedInstanceState){
     super.onCreate(savedInstanceState)
     setContentView(R.layout.main);
     Config.setContext(this.getApplicationContext());
   }
````

## Implement lifecycle metrics {#section_BA686C09021F474AADDE8690BBB910F7}

Nachdem Sie den Lebenszyklus aktiviert haben, wird bei jedem Start Ihrer App ein Treffer gesendet, um Starts, Upgrades, Sitzungen, erreichte Benutzer und viele andere Metriken zu messen. Weitere Informationen finden Sie unter  [Lebenszyklusmetriken](/help/android/metrics.md).

**Führen Sie die folgenden Schritte in jeder Aktivität Ihrer Anwendung aus:**

1. Importieren Sie die Bibliothek:

   ```java
   import com.adobe.mobile.*;
   ```

1. Starten Sie in der Funktion `onResume` die Erfassung der Lebenszyklusdaten:

   ```java
   @Override 
   public void onResume() { 
       Config.collectLifecycleData(this); 
       // -or- Config.collectLifecycleData(this, contextData); 
   }
   ```

1. Halten Sie in der Funktion `onPause` die Erfassung der Lebenszyklusdaten an:

   ```java
   @Override 
   public void onPause() { 
       Config.pauseCollectingLifecycleData(); 
   }
   ```

>[!IMPORTANT]
>
>Sie müssen diese Aufrufe jeder Aktivität hinzufügen, um eine genaue Absturzberichterstattung sicherzustellen. Weitere Informationen finden Sie unter Abstürze [verfolgen von Apps](/help/android/analytics-main/crashes.md).

## Include additional data with lifecycle calls

Um beim Lebenszyklusmetrik-Aufrufen zusätzliche Daten hinzuzufügen, übergeben Sie einen zusätzlichen Parameter mit Kontextdaten an `collectLifecycleData`:

```java
@Override 
public void onResume() {
    HashMap<String, Object> contextData = new HashMap<String, Object>(); 
    contextData.put("myapp.category", "Game"); 
    Config.collectLifecycleData(this, contextData); 
}
```

Zusätzliche Kontextdatenwerte, die mit `collectLifecycleData` gesendet werden, müssen benutzerdefinierten Variablen in Adobe Mobile Services zugeordnet sein:

![](assets/map-variable-lifecycle.png)

Andere Lebenszyklusmetriken werden automatisch erfasst. Weitere Informationen finden Sie unter  [Lebenszyklusmetriken](/help/android/metrics.md).

## Nächste Schritte {#section_BF709684E1DD40EA9169BC1D0D4B37C2}

Führen Sie die folgenden Aufgaben durch:

* [App-Zustände verfolgen](/help/android/analytics-main/states.md)
* [App-Aktionen verfolgen](/help/android/analytics-main/actions.md)

