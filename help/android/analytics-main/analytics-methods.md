---
description: Im Folgenden finden Sie eine Liste von Adobe Analytics-Methoden, die durch die Android-Bibliothek bereitgestellt werden.
keywords: Android;Bibliothek;Mobile;SDK
seo-description: Im Folgenden finden Sie eine Liste von Adobe Analytics-Methoden, die durch die Android-Bibliothek bereitgestellt werden.
seo-title: Analytics-Methoden
solution: Experience Cloud,Analytics
title: Analytics-Methoden
topic: Entwickler und Implementierung
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
translation-type: ht
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

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
      public staticvoidtrackState(Stringstate, Map<String,Object> contextData);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.trackState("loginScreen",null);
      ```

* **trackAction**
Verfolgt eine Aktion in der App.

   Aktionen, die Sie messen möchten, wie z. B. `logons`, `banner taps`, `feed subscriptions` und andere Metriken, die in Ihrer App auftreten.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      publicstaticvoidtrackAction(Stringstate,Map<String,Object> contextData);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.trackAction("heroBannerTouched",null);
      ```

* **getTrackingIdentifier**
Gibt die automatisch erzeugte Besucher-ID für Analytics zurück.

   Diese appspezifische, Unique Visitor-ID wird beim ersten Start generiert, gespeichert und dann fortlaufend weiterverwendet. Die ID wird auch bei App-Upgrades beibehalten und nur entfernt, wenn die App deinstalliert wird.

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
      public static void trackLocation(Location location, Map<String,Object> contextData); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.trackLocation(userLocation, null);
      ```

* **trackLifetime&#x200B;ValueIncrease**

   Erhöht den Lebenszeitwert des Benutzers um `amount`.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      publicstaticvoidtrackLifetimeValueIncrease(BigDecimalamount,Map<String,Object>contextData);
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
   publicstaticvoidtrackTimedActionStart(Stringaction,Map<String,Object>contextData);
   ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.trackTimedActionStart("cartToCheckout",null)
      ```


* **trackTimed&#x200B;ActionUpdate**

   Übergeben Sie diesen Wert in `contextData`, um die Kontextdaten zu aktualisieren, die der `action` zugewiesen sind. Die übergebenen Daten (`data`) werden an die vorhandenen Daten für die Aktion angehängt und wenn der Schlüssel bereits für `action` definiert ist, werden die Daten überschrieben.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void trackTimedActionUpdate(Stringaction,Map <String,Object> contextData); 
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
      public static void trackTimedActionEnd(Stringaction,TimedActionBlock<Boolean> logic); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.trackTimedActionEnd("cartToCheckout",new
      Analytics.TimedActionBlock<Boolean>(){
        @Override
        public Booleancall(long inAppDuration,long totalDuration, Map<String,
      Object> contextData) {
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
      voidsendQueuedHits()
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.sendQueuedHits();
      ```

* **getQueueSize**

   Gibt die Anzahl der in der Offline-Warteschlange gespeicherten Verfolgungsaufrufe an.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      long getQueueSize()
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      long queueSize = Analytics.getQueueSize(); 
      ```

* **clearQueue**

   Löscht alle Treffer aus der Offline-Warteschlange.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      voidclearQueue()
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.clearQueue();
      ```

      >[!WARNING]
      >
      > Gehen Sie beim manuellen Löschen der Warteschlange vorsichtig vor. Dieser Vorgang kann nicht rückgängig gemacht werden.