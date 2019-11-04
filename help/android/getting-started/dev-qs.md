---
description: Diese Information unterstützt Sie beim Implementieren der Android-Bibliothek und Erfassen von Lebenszyklusmetriken, wie z. B. Starts, Upgrades, Sitzungen, erreichte Benutzer usw.
keywords: Android;Bibliothek;Mobile;SDK
seo-description: Diese Information unterstützt Sie beim Implementieren der Android-Bibliothek und Erfassen von Lebenszyklusmetriken, wie z. B. Starts, Upgrades, Sitzungen, erreichte Benutzer usw.
seo-title: Grundlegende Implementierung und Lebenszyklus
solution: Experience Cloud,Analytics
title: Grundlegende Implementierung und Lebenszyklus
topic: Entwickler und Implementierung
uuid: af4d11ac-8245-46a0-9b3a-4a0a29cfbbb2
translation-type: ht
source-git-commit: c4da3599c858bfbccb7af954df75f94eb7d8e99a

---


# Grundlegende Implementierung und Lebenszyklus {#core-implementation-and-lifecycle}

Diese Information unterstützt Sie beim Implementieren der Android-Bibliothek und Erfassen von Lebenszyklusmetriken, wie z. B. Starts, Upgrades, Sitzungen, erreichte Benutzer usw.

## SDK herunterladen {#section_99FE1A17A36D4A2C943939023CF6265C}

>[!IMPORTANT]
>
>Um das SDK herunterzuladen, müssen Sie Android 2.2 oder höher verwenden.

1. Führen Sie die Schritte in den folgenden Abschnitten aus, um eine Entwicklungsberichtssuite einzurichten und eine vorinstallierte Version der Konfigurationsdatei herunterzuladen:

   * [Report Suite erstellen](/help/android/getting-started/requirements.md)
   * [SDK herunterladen](/help/android/getting-started/requirements.md)

1. Laden Sie die Datei `[Your_App_Name_]AdobeMobileLibrary-4.*-Android.zip` herunter und dekomprimieren Sie sie. Stellen Sie sicher, dass die folgenden Softwarekomponenten vorhanden sind:

   * `adobeMobileLibrary.jar`: die Bibliothek, die mit Android-Geräten und Simulatoren verwendet wird.

   * `ADBMobileConfig.json`: die SDK-Konfigurationsdatei, die für Ihre App angepasst ist.
   >[!IMPORTANT]
   >
   >Wenn Sie das SDK außerhalb der Adobe Mobile Services-Benutzeroberfläche herunterladen, muss die Datei `ADBMobileConfig.json` manuell konfiguriert werden. Wenn Sie mit Analytics und dem Mobile SDK noch nicht vertraut sind und eine Entwicklungsberichtssuite einrichten und eine vorinstallierte Version der Konfigurationsdatei herunterladen möchten, lesen Sie [Vorbereitung](/help/android/getting-started/requirements.md).

## SDK und Konfigurationsdatei zu Ihrem IntelliJ IDEA- oder Eclipse-Projekt hinzufügen {#section_B89510FBB4C646AEA73A185B966E54D3}

**IntelliJ IDEA-Projekt**

So fügen Sie das SDK und die Konfigurationsdatei zu Ihrem Projekt hinzu:

1. Fügen Sie die Datei `ADBMobileConfig.json` in den Ordner `assets` Ihres Projekts ein.

1. Klicken Sie im Bereich „Project Navigation“ (Projektnavigation) mit der rechten Maustaste auf das Projekt.
1. Wählen Sie **[!UICONTROL Moduleinstellungen öffnen]**.
1. Wählen Sie unter **[!UICONTROL Projekteinstellungen]** die Option **[!UICONTROL Bibliotheken]**.
1. Klicken Sie auf **[!UICONTROL +]**, um eine neue Bibliothek hinzuzufügen.
1. Wählen Sie **[!UICONTROL Java]** und navigieren Sie zur Datei `adobeMobileLibrary.jar`.
1. Wählen Sie die Module aus, in denen Sie die Mobilbibliothek verwenden möchten.
1. Klicken Sie auf **[!UICONTROL Anwenden]** und anschließend auf **[!UICONTROL OK]**, um das Fenster Moduleinstellungen zu schließen.

**Eclipse-Projekt**

So fügen Sie das SDK und die Konfigurationsdatei zu Ihrem Projekt hinzu:

1. Fügen Sie die Datei `ADBMobileConfig.json` in den Ordner `assets` Ihres Projekts ein.
1. Klicken Sie in **[!UICONTROL Eclipse IDE]** mit der rechten Maustaste auf den Projektnamen.
1. Klicken Sie auf **[!UICONTROL Pfad aufbauen]** &gt; **[!UICONTROL Externe Archive hinzufügen]**.
1. Select `adobeMobileLibrary.jar`.
1. Klicken Sie auf **[!UICONTROL Öffnen]**.
1. Klicken Sie erneut mit der rechten Maustaste auf das Projekt und wählen Sie dann **[!UICONTROL Pfad aufbauen]** &gt; **[!UICONTROL Pfadaufbau konfigurieren]** aus.
1. Stellen Sie sicher, dass auf der Registerkarte **[!UICONTROL Sortieren und exportieren]** **`adobeMobileLibrary.jar`** ausgewählt ist.

## App-Berechtigungen hinzufügen {#section_2EAF73ABF6424647B219A63B33B02CD5}

Die AppMeasurement-Bibliothek erfordert folgende Berechtigungen, um Daten zu senden und Offline-Verfolgungsaufrufe aufzuzeichnen:

* `INTERNET`
* `ACCESS_NETWORK_STATE`

Ergänzen Sie die Datei `AndroidManifest.xml` im Projektverzeichnis der Anwendung um die folgenden Zeilen, um diese Berechtigungen hinzuzufügen:

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

## App-Kontext festlegen {#set-application-context}

Der folgende Code sollte der `onCreate`-Methode Ihrer Hauptaktivität hinzugefügt werden:

```java
   @Override
   public void onCreate(BundlesavedInstanceState){
     super.onCreate(savedInstanceState)
     setContentView(R.layout.main);
     Config.setContext(this.getApplicationContext());
   }
````

## Lebenszyklusmetriken implementieren {#section_BA686C09021F474AADDE8690BBB910F7}

Nachdem Sie den Lebenszyklus aktiviert haben, wird bei jedem Start Ihrer App ein Treffer gesendet, um Starts, Upgrades, Sitzungen, erreichte Benutzer und viele andere Metriken zu messen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

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
>Sie müssen diese Aufrufe zu jeder Aktivität hinzufügen, um präzise Absturzberichte zu gewährleisten. Weitere Informationen finden Sie unter [App-Abstürze verfolgen](/help/android/analytics-main/crashes.md).

## Zusätzliche Daten zu Lebenszyklusaufrufen hinzufügen

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

Andere Lebenszyklusmetriken werden automatisch erfasst. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

## Nächste Schritte {#section_BF709684E1DD40EA9169BC1D0D4B37C2}

Führen Sie die folgenden Aufgaben durch:

* [App-Zustände verfolgen](/help/android/analytics-main/states.md)
* [App-Aktionen verfolgen](/help/android/analytics-main/actions.md)

