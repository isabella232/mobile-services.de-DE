---
description: Dieses Thema enthält Informationen zur Fehlerbehebung bei Problemen, die während des Akquise-Tests auftreten können.
keywords: android;library;mobile;sdk
seo-description: Dieses Thema enthält Informationen zur Fehlerbehebung bei Problemen, die während des Akquise-Tests auftreten können.
seo-title: Fehlerbehebung bei Akquise-Tests
solution: Marketing Cloud,Analytics
title: Fehlerbehebung bei Akquise-Tests
topic: Entwickler und Implementierung
translation-type: tm+mt
source-git-commit: 97202c672d7349496f83b9ac0c365dd8b3e13eda

---


# Fehlerbehebung bei Akquise-Tests {#troubleshoot-acquisition-testing}

Dieses Thema enthält Informationen zur Fehlerbehebung bei Problemen, die während des Akquise-Tests auftreten können.

* Falls nicht anders angegeben, sollte die Datei ADBMobileConfig.json im `assets` Ordner abgelegt werden.

   Bei dem Namen wird zwischen Groß- und Kleinschreibung unterschieden. Verwenden Sie daher keine Groß- oder Kleinbuchstaben.

* Stellen Sie sicher, dass Sie von Ihrer Hauptaktivität aufgerufen `Config.setContext(this.getApplicationContext())` werden.

   Weitere Informationen finden Sie unter [Konfigurationsmethoden](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html).

* Stellen Sie sicher, dass die erforderlichen Berechtigungen für das Mobile SDK in der `AndroidManifest.xml` Datei vorhanden sind:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Wenn der Wert in der Datei ADMobileConfig.json auf 5 gesetzt `referrerTimeout` ist, müssen Sie die Installationsabsicht innerhalb von 5 Sekunden nach der Installation und dem ersten Start der Anwendung senden, um die am Installationshit angehängten Referrer-Informationen anzuzeigen.

   Für manuelle Tests wird empfohlen, den Wert `referrerTimeout` auf 10-15 Sekunden zu erhöhen, damit Sie genügend Zeit haben, die Referrer-Informationen zu senden, bevor der Installationshit verarbeitet wird.

* Führen Sie alle Schritte unter [Testen der Marketinglink-Akquise](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) aus und stellen Sie sicher, dass Sie den `adb shell` Befehl zuerst und dann ausführen:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Um die Referrer-Absicht korrekt zu verarbeiten, müssen Sie diese beiden Befehle unabhängig voneinander ausführen. Andernfalls `adb` werden die Referrer-Informationen doppelt entkommen, und die vom Empfänger empfangenen Daten sind unvollständig.

