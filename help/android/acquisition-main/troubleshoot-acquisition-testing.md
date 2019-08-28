---
description: Dieses Thema enthält Informationen zur Fehlerbehebung bei Problemen, die bei der Akquise-Prüfung auftreten könnten.
keywords: android; library; mobile; sdk
seo-description: Dieses Thema enthält Informationen zur Fehlerbehebung bei Problemen, die bei der Akquise-Prüfung auftreten könnten.
seo-title: Fehlerbehebung bei Akquise-Tests
solution: Marketing Cloud, Analytics
title: Fehlerbehebung bei Akquise-Tests
topic: Entwickler und Implementierung
translation-type: tm+mt
source-git-commit: 97202c672d7349496f83b9ac0c365dd8b3e13eda

---


# Fehlerbehebung bei Akquise-Tests {#troubleshoot-acquisition-testing}

Dieses Thema enthält Informationen zur Fehlerbehebung bei Problemen, die bei der Akquise-Prüfung auftreten könnten.

* Andernfalls sollte die Datei adbmobileconfig. json im `assets` Ordner platziert werden.

   Bei dem Namen muss die Groß- und Kleinschreibung beachtet werden. Verwenden Sie also keine Großbuchstaben oder Kleinbuchstaben.

* Stellen Sie `Config.setContext(this.getApplicationContext())` sicher, dass Sie aus Ihrer Hauptaktivität aufgerufen werden.

   Weitere Informationen finden Sie unter [Konfigurationsmethoden](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html).

* Stellen Sie sicher, dass die erforderlichen Berechtigungen für das mobile SDK in der `AndroidManifest.xml` Datei vorhanden sind:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Wenn die `referrerTimeout` Datei "admobileconfig. json «auf 5 gesetzt ist, müssen Sie die Installation innerhalb eines Zeitraums von 5 Sekunden senden, nachdem die Anwendung zum ersten Mal installiert und gestartet wurde, um die an den Treffer-Treffer angehängten Referrer-Informationen anzuzeigen.

   Für manuelle Tests wird empfohlen, dass Sie die `referrerTimeout` Werte von 10 bis 15 Sekunden erhöhen, damit Sie genügend Zeit haben, die verweisenden Stellen zu senden, bevor der Installationstreffer verarbeitet wird.

* Führen Sie alle Schritte unter ["Test Marketing Link-Akquise testen" aus](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) und stellen Sie sicher, dass Sie den `adb shell` Befehl zuerst ausführen und dann Folgendes ausführen:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Um die Referrer-Intention korrekt zu verarbeiten, müssen Sie diese beiden Befehle unabhängig ausführen. Andernfalls `adb` werden die Referrer-Informationen doppelt abgeglichen und die vom Empfänger empfangenen Daten sind unvollständig.

