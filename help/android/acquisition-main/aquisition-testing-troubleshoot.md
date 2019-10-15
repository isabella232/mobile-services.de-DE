---
description: Die folgenden Informationen helfen Ihnen bei der Fehlerbehebung von Problemen mit Akquise-Tests.
keywords: Android;Akquise;Test
seo-description: Die folgenden Informationen helfen Ihnen bei der Fehlerbehebung von Problemen mit Akquise-Tests.
seo-title: Fehlerbehebung beim Testen der Akquise
solution: Marketing Cloud,Analytics
title: Fehlerbehebung beim Testen der Akquise
translation-type: tm+mt
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# Fehlerbehebung beim Testen der Akquise {#aquistion-testing-troubleshooting}

Im Folgenden finden Sie einige Probleme, mit denen Sie beim Testen der Akquise konfrontiert sein könnten, sowie einige mögliche Lösungen:

* Wenn nicht anders angegeben, sollte die Datei ADBMobileConfig.json im Ordner assets abgelegt werden.

* Bei dem Namen wird zwischen Groß- und Kleinschreibung unterschieden. Geben Sie daher keinen Namen in Kleinbuchstaben an.

   Sie müssen sicherstellen, dass von der Hauptaktivität aufgerufen `Config.setContext(this.getApplicationContext())` wird. Weitere Informationen finden Sie unter [Konfigurationsmethoden](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html).

* In der angegebenen Datei AndroidManifest.xml fehlen einige Benutzerberechtigungen. Diese sind erforderlich, um Daten zu senden und Offline-Verfolgungsaufrufe aufzuzeichnen:

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Wenn in Ihrer Konfiguration das Timeout der verweisenden Stelle auf `referrerTimeout: 5`festgelegt ist, müssen Sie die Installationsabsicht in einem Zeitraum von 5 Sekunden nach der Installation und dem ersten Start der Anwendung senden, um die Informationen zur verweisenden Stelle am Installationshit anzuzeigen.

   Erhöhen Sie für manuelle Tests den Wert `referrerTimeout` auf 10-15 Sekunden, damit ausreichend Zeit zum Senden der Referrer-Informationen zur Verfügung steht, bevor der Installationshit verarbeitet wird.

* Es ist wichtig, dass Sie alle Schritte in der [Testing Marketing Link-Akquise](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) in der Reihenfolge ausführen und sicherstellen, dass Sie `adb` Shell und dann Folgendes ausführen:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Sie müssen diese beiden Befehle unabhängig ausführen, um die Absicht der verweisenden Stelle korrekt zu verarbeiten.  Andernfalls werden die Referrer-Informationen `adb` doppelt ignoriert, und die vom Rundfunkempfänger empfangenen Daten sind unvollständig.
