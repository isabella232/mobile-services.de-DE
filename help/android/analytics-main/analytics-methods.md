---
description: Im Folgenden finden Sie eine Liste von Adobe Analytics-Methoden, die durch die Android-Bibliothek bereitgestellt werden.
keywords: Android;Bibliothek;Mobile;SDK
solution: Experience Cloud,Analytics
title: Analytics-Methoden
topic-fix: Developer and implementation
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
exl-id: 7914d13e-40a2-4ae2-b759-2660817c2058
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 100%

---

# Analytics-Methoden {#analytics-methods}

Im Folgenden finden Sie eine Liste von Adobe Analytics-Methoden, die durch die Android-Bibliothek bereitgestellt werden.

Das SDK unterstützt zurzeit mehrere Adobe Experience Cloud-Lösungen, einschließlich Analytics, Target, Audience Manager und Identity-Dienst für Adobe Experience Platform. Methoden erhalten je nach Lösung unterschiedliche Präfixe, z. B. `analytics` bei Experience Cloud ID-Methoden.

Jede der folgenden Methoden wird verwendet, um Daten an Ihre Adobe Analytics Report Suite zu senden:

* **trackState**

   Verfolgt einen App-Status mit optionalen Kontextdaten. Die Statusangaben entsprechen den verfügbaren Ansichten in der App, z. B. `home dashboard`, `app settings` und `cart`. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `trackState`-Aufrufe inkrementieren die Seitenansichten.

   Wenn `state` leer ist, wird in Berichten `app name app version (build)` angezeigt. Wenn dieser Wert in einem Bericht auftritt, müssen Sie `state` in jedem `trackState`-Aufruf festlegen.

   >[!TIP]
   >
   >Dies ist der einzige Verfolgungsaufruf, bei dem die Seitenansichten inkrementiert werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void trackState(String state, Map<String, Object> contextData);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.trackState("loginScreen", null);
      ```

* **trackAction**
Verfolgt eine Aktion in der App.

   Aktionen, die Sie messen möchten, wie z. B. `logons`, `banner taps`, `feed subscriptions` und andere Metriken, die in Ihrer App auftreten.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void trackAction(String state, Map<String, Object> contextData);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.trackAction("heroBannerTouched", null);
      ```

* **getTrackingIdentifier**
Gibt die automatisch erzeugte Besucher-ID für Analytics zurück.

   Hierbei handelt es sich um eine App-spezifische Unique-Visitor-ID, die beim ersten Start generiert und ab diesem Zeitpunkt gespeichert und verwendet wird. Die ID bleibt zwischen App-Upgrades erhalten und wird entfernt wenn die App deinstalliert wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static String getTrackingIdentifier();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      String trackingId = Analytics.getTrackingIdentifier();
      ```

* **trackLocation**

   Sendet den aktuellen Längen- und Breitengrad und den Standort in einem definierten Zielpunkt. Weitere Informationen finden Sie unter [Geostandort und Zielpunkte](/help/android/location/geo-poi.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void trackLocation(Location location, Map<String, Object> contextData);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.trackLocation(userLocation, null);
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Erhöht den Lebenszeitwert des Benutzers um `amount`.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void trackLifetimeValueIncrease(BigDecimal amount, Map<String, Object> contextData);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.trackLifetimeValueIncrease(new BigDecimal(30), null);
      ```

* **trackTimed&#x200B;ActionStart**

   Startet eine zeitgesteuerte Aktion mit dem Namen `action`.

   Wenn Sie diese Methode für eine bereits gestartete Methode aufrufen, wird die vorherige zeitgesteuerte Aktion überschrieben.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

   ```java
   public static void trackTimedActionStart(String action, Map<String, Object> contextData);
   ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.trackTimedActionStart("cartToCheckout", null)
      ```


* **trackTimed&#x200B;ActionUpdate**

   Übergeben Sie diesen Wert in `contextData`, um die Kontextdaten zu aktualisieren, die der `action` zugewiesen sind. Die übergebenen Daten ( `data` ) werden an die vorhandenen Daten für die Aktion angehängt und wenn der Schlüssel bereits für `action` definiert ist, werden die Daten überschrieben.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void trackTimedActionUpdate(String action, Map<String, Object> contextData);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      HashMap cdata = new HashMap<String Object> ();
      cdata.put("quantity",3);
      Analytics.trackTimedActionUpdate("cartToCheckout", cdata);
      ```

* **trackTimed&#x200B;ActionEnd**

   Beendet eine zeitgesteuerte Aktion. Wenn Sie `block` angeben, können Sie auf die endgültigen Zeitwerte zugreifen und `data` verändern, bevor Sie den endgültigen Treffer senden.

   >[!TIP]
   >
   >Wenn Sie `block` angeben, müssen Sie `true` zurückgeben, um einen Treffer zu senden. Wenn Sie `null` für `block` übergeben, wird der endgültige Treffer gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void trackTimedActionEnd(String action, TimedActionBlock<Boolean> logic);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.trackTimedActionEnd("cartToCheckout",new
      Analytics.TimedActionBlock<Boolean>(){
          @Override
          public Boolean call(long inAppDuration, long totalDuration, Map<String, Object> contextData) {
              contextData.put("price", 49.95);
              return true;
          }
      });
      ```

* **sendQueuedHits**

   **Erfordert SDK 4.1.**

   Diese Methode zwingt die Bibliothek dazu, alle Treffer in der Offline-Warteschlange zu senden – unabhängig von der Anzahl der Treffer in der Warteschlange.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void sendQueuedHits();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.sendQueuedHits();
      ```

* **getQueueSize**

   Gibt die Anzahl der in der Offline-Warteschlange gespeicherten Verfolgungsaufrufe an.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static long getQueueSize();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      long queueSize = Analytics.getQueueSize();
      ```

* **clearQueue**

   Löscht alle Treffer aus der Offline-Warteschlange.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void clearQueue();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.clearQueue();
      ```

      >[!WARNING]
      >
      > Gehen Sie beim manuellen Löschen der Warteschlange vorsichtig vor. Dieser Vorgang kann nicht rückgängig gemacht werden.

* **processReferrer**

   Verarbeitet Referrer-Kampagnendaten aus dem Google Play Store für die spätere Verwendung.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void processReferrer(final Context context, final Intent intent);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.processReferrer(getApplicationContext(), intent);
      ```

* **processGooglePlayInstallReferrerUrl**

   >[!IMPORTANT]
   >
   > Diese API ist ab SDK Version 4.18.0 verfügbar.

   Ruft Akquise-Daten von der angegebenen Google Play-Install-Referrer-URL ab.

   Die von dieser API erfassten Daten werden bei einer an Analytics übermittelten Installation gesendet; sie sind in Adobe Data Callback verfügbar.

   Wenn Referrer-Daten bereits vom SDK erfasst wurden, führt ein Aufruf dieser Methode zu einem „no-op“.

   Informationen zum Abrufen der Referrer-URL finden Sie in der Google-Dokumentation: https://developer.android.com/google/play/installreferrer/library.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void processGooglePlayInstallReferrerUrl(final String referrerUrl);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.processGooglePlayInstallReferrerUrl(referrerUrl);
      ```
