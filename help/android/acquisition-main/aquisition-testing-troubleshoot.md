---
description: Die folgenden Informationen helfen Ihnen bei der Fehlerbehebung bei Problemen mit der Akquise-Prüfung.
keywords: android; Akquise; wird getestet
seo-description: Die folgenden Informationen helfen Ihnen bei der Fehlerbehebung bei Problemen mit der Akquise-Prüfung.
seo-title: Fehlerbehebung für Akquise-Tests
solution: Marketing Cloud, Analytics
title: Fehlerbehebung für Akquise-Tests
translation-type: tm+mt
source-git-commit: da8798d7ee1f05dcade31cced5404d78c9cf360a

---


# Fehlerbehebung für Akquise-Tests {#aquistion-testing-troubleshooting}

Im Folgenden finden Sie einige Probleme, die Sie beim Testen der Akquise und bei einigen möglichen Lösungen auftreten können:

* Falls nicht anders angegeben, sollte die Datei "adbmobileconfig. json" im Assets-Ordner untergebracht werden.

* Bei dem Namen muss die Groß-/Kleinschreibung beachtet werden. Geben Sie daher keinen Namen in Kleinbuchstaben ein.

   Sie müssen sicherstellen, dass `Config.setContext(this.getApplicationContext())` der Aufruf aus der Hauptaktivität erfolgt. Weitere Informationen finden Sie unter [Konfigurationsmethoden](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html).

* In der bereitgestellten AndroidManifest.xml fehlen einige Benutzerberechtigungen, die zum Senden von Daten und zur Aufzeichnung von Offline-Verfolgungsaufrufen erforderlich sind:

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Wenn der Referrer-Timeout in Ihrer Konfiguration auf `referrerTimeout: 5`festgelegt ist, bedeutet dies, dass Sie die Installation in einem fünfzweiten Zeitrahmen senden müssen, nachdem die Anwendung installiert und zum ersten Mal gestartet wurde, um die an den Treffer-Treffer angehängten Referrer-Informationen anzuzeigen.

   Erhöhen Sie für manuelle Tests die `referrerTimeout` Werte von 10 bis 15 Sekunden, damit die verweisenden Stellen ausreichend Zeit erhalten, bevor der Installationstreffer verarbeitet wird.

* Es ist wichtig, alle Schritte unter ["Testen von Marketing Link-Akquisen](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) " auszuführen und sicherzustellen, dass Shell und anschließend `adb` die folgenden ausgeführt werden:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Sie müssen diese beiden Befehle unabhängig ausführen, um die Referrer-Intention korrekt zu verarbeiten. Andernfalls `adb` werden die Referrer-Informationen doppelt gesperrt und die vom Empfänger empfangenen Daten sind unvollständig.
