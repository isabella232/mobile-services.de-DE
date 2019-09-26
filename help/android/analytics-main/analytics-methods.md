---
description: Im Folgenden finden Sie eine Liste von Adobe Analytics-Methoden, die durch die Android-Bibliothek bereitgestellt werden.
keywords: android;library;mobile;sdk
seo-description: Im Folgenden finden Sie eine Liste von Adobe Analytics-Methoden, die durch die Android-Bibliothek bereitgestellt werden.
seo-title: Analytics-Methoden
solution: Marketing Cloud, Analytics
title: Analytics-Methoden
topic: Entwickler und Implementierung
uuid: ac7c640e-9dcc-4724-b561-019cc025d5a7
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Analytics methods {#analytics-methods}

Im Folgenden finden Sie eine Liste von Adobe Analytics-Methoden, die durch die Android-Bibliothek bereitgestellt werden.

The SDK currently supports multiple Adobe Experience Cloud Solutions], including Analytics], Target], Audience Manager], and the Adobe Experience Platform Identity Service]. Methoden erhalten je nach Lösung unterschiedliche Präfixe, z. B. `analytics` bei Experience Cloud ID-Methoden.

Jede der folgenden Methoden wird verwendet, um Daten an Ihre Adobe Analytics Report Suite zu senden:

* **trackState**

   Verfolgt einen App-Status mit optionalen Kontextdaten. States are the views that are available in your app, such as `home dashboard`, `app settings`, `cart`, and so on. Diese Statusangaben sind mit den Seiten in einer Website vergleichbar, und `trackState`-Aufrufe inkrementieren die Seitenansichten.

   If `state` is empty, `app name app version (build)` is displayed in reports. Wenn dieser Wert in einem Bericht auftritt, müssen Sie `state` in jedem `trackState`-Aufruf festlegen.

   >[!TIP]
   >
   >Dies ist der einzige Verfolgungsaufruf, durch den die Seitenansichten inkrementiert werden.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public staticvoidtrackState(Stringstate, Map<String,Object> contextData);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.trackState("loginScreen",null);
      ```

* **trackAction
Tracks an action in your app.**

   Actions that you want to measure, such as `logons`, `banner taps`, `feed subscriptions`, and other metrics, that occur in your app.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      publicstaticvoidtrackAction(Stringstate,Map<String,Object> contextData);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Analytics.trackAction("heroBannerTouched",null);
      ```

* **getTrackingIdentifier** Gibt die automatisch generierte Besucher-ID für Analytics zurück.

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

   Sends the current latitude, longitude, and location in a defined point of interest. Weitere Informationen finden Sie unter [Geografischer Standort und Zielpunkte](/help/android/location/geo-poi.md).

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

   Pass in `contextData` to update the context data that is associated with the `action`. The `data` that is passed in is appended to the existing data for the action, and if the same key is already defined for `action`, overwrites the data.

   >[!TIP]
   >
   >Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void trackTimedActionUpdate(Stringaction,Map <String,Object> contextData); 
      ```

   * Here is a code sample for this method:

      ```java
      HashMap cdata = new HashMap<String Object> (); 
      cdata.put("quantity",3); 
      Analytics.trackTimedActionUpdate("cartToCheckout", cdata);
      ```

* **trackTimed&#x200B;ActionEnd**

   Beendet eine zeitgesteuerte Aktion. Wenn Sie `block` angeben, können Sie auf die endgültigen Zeitwerte zugreifen und `data` verändern, bevor Sie den endgültigen Treffer senden.

   >[!TIP]
   >
   >If you provide `block`, you must return `true` to send a hit. Passing `null` for `block` sends the final hit.

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