---
description: Die folgenden Anweisungen helfen Ihnen dabei, mit einem Marketing-Link auf einem Android-Gerät eine Hin&Zurück-Abfrage einer Akquise-Kampagne durchzuführen.
keywords: Android;Bibliothek;Mobile;SDK
seo-description: Die folgenden Anweisungen helfen Ihnen dabei, mit einem Marketinglink auf einem Android-Gerät eine Hin&Zurück-Abfrage einer Akquise-Kampagne durchzuführen.
seo-title: Marketinglink-Akquise testen
solution: Experience Cloud,Analytics
title: Marketing-Link-Akquise testen
topic-fix: Developer and implementation
uuid: d0933dcc-8fc3-4f60-987f-7a54559aacf5
exl-id: 86fdaef7-5b6c-4e9d-a470-df66c96f2e9d
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 100%

---

# Marketinglink-Akquise testen {#testing-marketing-link-acquisition}

Die folgenden Anweisungen helfen Ihnen dabei, mit einem Marketing-Link auf einem Android-Gerät eine Hin&amp;Zurück-Abfrage einer Akquise-Kampagne durchzuführen.

Wenn die App noch nicht in Google Play vorhanden ist, können Sie beim Erstellen des Marketinglinks eine beliebige App als Ziel auswählen. Dies wirkt sich nur auf die App aus, zu der der Akquise-Server die Umleitung vornimmt, nachdem Sie auf den Akquise-Link geklickt haben, nicht aber auf die Fähigkeit, den Akquise-Link zu testen. Zeichenfolgenparameter der Abfrage werden an den Google Play Store übergeben, der bei der Installation im Zuge einer Kampagnenübertragung an die App übergeben wird. Für die Tests zur Akquise von Hin&amp;Zurück-Abfragen mobiler Apps ist die Simulation dieser Art von Übertragungen erforderlich.

Vor jedem Testlauf muss die App neu installiert bzw. müssen ihre Daten in den **[!UICONTROL Einstellungen]** gelöscht werden. So wird gewährleistet, dass die anfänglichen Lebenszyklusmetriken mit den Abfragezeichenfolgen-Parametern der Kampagne gesendet werden, wenn die App zum ersten Mal gestartet wird.

1. Führen Sie die erforderlichen Aufgaben in [App-Akquise](/help/android/acquisition-main/acquisition.md) aus und stellen Sie sicher, dass Sie den Broadcast-Empfänger für `INSTALL_REFERRER` ordnungsgemäß implementiert haben.
1. Klicken Sie in der Adobe Mobile Services-Benutzeroberfläche auf **[!UICONTROL Akquise]** > **[!UICONTROL Marketing Links Builder]** und generieren Sie eine Akquise-Marketinglink-URL, die Google Play als Ziel für Android-Geräte festlegt.

   Weitere Informationen finden Sie unter [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

   Beispiel:

   `https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Öffnen Sie den generierten Link auf dem Android-Gerät.

   Sie sollten auf eine Seite umgeleitet werden, deren URL folgendem Beispiel ähnelt:

   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Kopieren Sie die eindeutige ID hinter `utm_content%3D`.

   Im vorherigen Beispiel lautet die ID `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

   Wenn Sie die eindeutige ID nicht auf dem Gerät abrufen können, führen Sie auf dem Desktop folgenden `CURL`-Befehl aus, um die eindeutige URL aus der Antwortzeichenfolge abzurufen.

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" <Your Marketing Link>`

   Beispiel:

   `curl -A "Mozilla/5.0 (Linux; Android 5.0.2; SAMSUNG SM-T815Y Build/LRX22G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.133 Safari/537.36" https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=573e5bb3248a501360c2890b`

1. Erstellen Sie einen Akquise-Endlink mithilfe der eindeutigen URL aus Schritt 3. Verwenden Sie hierfür folgendes Format:

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`

   Beispiel, `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Öffnen Sie den Link in einem Browser.

   Sie sollten die Kontextdaten ( `contextData` ) in der JSON-Antwort sehen:

   ```
   {"fingerprint":"44b2f88a062df7e727c047f006deb9971304617b","endCallbacks":["***"],"timestamp":1464301282,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData": 
   {"a.launch.campaign.trackingcode":"trymttvm","a.referrer.campaign.name":"Android Demo","a.referrer.campaign.trackingcode":"trymttvm"} 
   ,"adobeData":{"unique_id":"9a2be52764a8db125c29a8c10f3b1b3d5d8ed915","deeplinkid":"57476c26072932ec6d3a470b"}}.
   ```

1. Wiederholen Sie Schritt 3, um eine neue eindeutige URL zu erhalten.
1. Stellen Sie sicher, dass die folgenden Einstellungen in Ihrer Konfigurationsdatei vorhanden sind:

   | Wenn | Wert |
   |--- |--- |
   | Akquise | Der Server sollte `c00.adobe.com` sein und *`appid`* sollte der `appid` in Ihrem Akquise-Link entsprechen. |
   | analytics | Legen Sie für Testzwecke das Zeitlimit des Werbers so fest, dass ausreichend Zeit (mindestens 60 Sekunden) zum manuellen Durchführen des Versands zur Verfügung steht. Sie können die ursprüngliche Zeitlimiteinstellung nach dem Test wiederherstellen. |

1. Verbinden Sie das Gerät mit einem Computer, deinstallieren Sie die App und installieren Sie sie anschließend erneut.
1. Starten Sie ADB Shell und rufen Sie die Anwendung auf dem Gerät auf.

   ```
   adb shell
   ```

1. Senden Sie einen Broadcast mithilfe des folgenden `adb`-Befehls:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"
   ```

1. Ersetzen Sie `com.adobe.android` durch den Paketnamen Ihrer Anwendung, ändern Sie die Empfängerreferenz zum Standort des Kampagnenverfolgungs-Empfängers in Ihrer App und ersetzen Sie die Werte für `utm_content`.

   Wenn der Broadcast erfolgreich ist, sollten Sie eine Antwort ähnlich der folgenden erhalten:

   ```
   Broadcasting: Intent 
   { act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) } 
   Broadcast completed: result=0 
   ```

1. (Optional) Sie können die Debugging-Protokollierung des SDK aktivieren, um zusätzliche Informationen zu erhalten.

   Wenn alles funktioniert, sollten Sie folgende Protokolle erhalten:

   ```
   "Analytics - Received referrer information(<referrer content>)" 
   "Analytics - Trying to fetch referrer data from (acquisition end url)"; 
   "Analytics - Received Referrer Data(<A JSON Response>)"
   ```

   Falls diese Protokolle nicht angezeigt werden, sollten Sie sicherstellen, dass Sie die Schritte 6 bis 10 abgeschlossen haben.

   Die folgende Tabelle enthält weitere Informationen zu möglichen Fehlern:

   | Fehler | Beschreibung |
   |--- |--- |
   | Analytics - Unable to decode response(`<string>`). | Die Antwort ist falsch formatiert. |
   | Analytics - Unable to parse response (`a JSON Response`). | Die JSON-Zeichenfolge ist falsch formatiert. |
   | Analytics - Unable to parse acquisition service response (no `contextData` parameter in response). | In der Antwort ist kein `contextData`-Parameter enthalten. |
   | Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name` ist nicht in contextData vorhanden. |
   | Analytics - Acquisition referrer timed out. | Die Antwort konnte nicht in der durch `referrerTimeout` festgelegten Zeit abgerufen werden. Erhöhen Sie den Wert und versuchen Sie es erneut.  Sie sollten auch sicherstellen, dass Sie den Akquise-Link geöffnet haben, bevor Sie die App installieren. |

Berücksichtigen Sie folgende Informationen:

* Hits, die von der App gesendet werden, können mithilfe von HTTP-Überwachungstools überwacht werden, um die Akquise-Zuordnung zu überprüfen.
* Weitere Informationen zu `INSTALL_REFERRER`-Broadcasts finden Sie unter [Testen der Google Play-Kampagnenmessung](https://developers.google.com/analytics/solutions/testing-play-campaigns) im Google Developers-Handbuch.
* Sie können das bereitgestellte Java-Tool `acquisitionTest.jar` verwenden, um die eindeutige ID abzurufen und den Installations-Referrer-Broadcast durchzuführen. So erhalten Sie die Informationen aus den Schritten 3 bis 10.

**Installation des Java-Tools**

So installieren Sie das Java-Tool:

1. Laden Sie die Datei [`acquistionTester.zip`](../assets/acquisitionTester.zip) herunter.
1. Extrahieren Sie die JAR-Datei.

   Sie können die JAR-Datei in der Befehlszeile ausführen.

Beispiel:

```
java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
```

Die Marketinglinks werden serverseitig mit einer zehnminütigen Ablaufzeit zwischengespeichert. Wenn Sie Änderungen an Markierungslinks vornehmen, warten Sie etwa 10 Minuten, bis die Änderungen wirksam werden, bevor Sie die Verknüpfungen erneut verwenden.
