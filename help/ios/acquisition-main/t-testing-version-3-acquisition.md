---
description: Diese Informationen helfen Ihnen dabei, einen V3-Akquise-Kampagnenlink basierend auf einem Gerätefingerabdruck zu übertragen.
seo-description: Diese Informationen helfen Ihnen dabei, einen V3-Akquise-Kampagnenlink basierend auf einem Gerätefingerabdruck zu übertragen.
seo-title: Testen der V3-Akquise
solution: Marketing Cloud, Analytics
title: Testen der V3-Akquise
uuid: 89137 ccf -4839-4 b 37-926 e -303 cf 8 e 511 a 5
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Testing V3 acquisition{#testing-v-acquisition}

Diese Informationen helfen Ihnen dabei, einen V3-Akquise-Kampagnenlink basierend auf einem Gerätefingerabdruck zu übertragen.

>[!IMPORTANT]
>
>Die Akquise von V 3 bezieht sich auf die Akquise-Links, die Sie mit dem Akquise-Builder in der Benutzeroberfläche von Adobe Mobile Services erstellen. Zum Verwenden dieses Features müssen Sie ein Upgrade von iOS-SDK-Version 4.6.0 oder höher vornehmen.

Wenn die mobile App noch nicht im App-Store vorhanden ist, wenn Sie den Kampagnenlink erstellen, sollten Sie eine beliebige mobile App als Ziel auswählen. Dies wirkt sich nur auf die App aus, zu der Sie vom Akquiseserver umgeleitet werden, nachdem Sie auf den Akquiselink geklickt haben. Dies wirkt sich jedoch nicht auf die Fähigkeit zum Testen des Links aus.

1. Führen Sie die erforderlichen Schritte in der [Mobile App-Akquise aus](/help/ios/acquisition-main/acquisition.md).
1. Navigate to the **[!UICONTROL Acquisition Builder]** in the Adobe Mobile Services UI and generate an acquisition campaign URL.

   Beispiel:

   ```
   https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```


   Verwenden Sie den Apple-Store als standardmäßigen Store, sofern Sie im Akquiselink sowohl auf iOS- als auch auf Android-Apps verweisen.
1. Open the generated link in a desktop browser and go to `https://c00.adobe.com/v3/<appid>/end`.

   Es sollte `contextData` in der JSON-Antwort angezeigt werden:

   ```js
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.
   ```

   If you do not see `contextData`, or some of it is missing, ensure that the acquisition URL follows the format that is specified in [Create Acquisition Link Manually](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md).
1. Stellen Sie sicher, dass die folgenden Einstellungen in Ihrer Konfigurationsdatei vorhanden sind:

   | Wenn | Wert |
   |--- |--- |
   | Akquise | The server should be  `c00.adobe.com`. *`appid`* sollte mit dem *`appid`* in Ihrem Akquise-Link übereinstimmen. |
   | analytics | `referrerTimeout` sollte einen Wert größer als 0 aufweisen. |


1. (Bedingt) Wenn die Einstellung `ssl` in der Konfigurationsdatei Ihrer App „true“ lautet, sollten Sie Ihren Akquiselink zum Verwenden des HTTPS-Protokolls aktualisieren.
1. Klicken Sie auf den generierten Link vom Mobilgerät, auf dem Sie die App installieren möchten.

   Die Server von Adobe (`c00.adobe.com`) speichern den Fingerabdruck und nehmen eine Umleitung zum App-Store vor. Die App muss nicht für Testzwecke heruntergeladen werden.
1. Starten Sie die Anwendung erstmals auf demselben Mobilgerät, das Sie in Schritt 6 verwendet haben.

   Bei Bedarf können Sie die App löschen und erneut installieren.
1. (Optional) Sie können die Debugging-Protokollierung des SDK aktivieren, um zusätzliche Informationen zu erhalten.

   Wenn alles richtig funktioniert, sollten die folgenden Protokolle angezeigt werden:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   Falls die obigen Protokolle nicht angezeigt werden, sollten Sie sicherstellen, dass Sie die Schritte 4 und 5 abgeschlossen haben.

   Im Folgenden finden Sie einige Informationen zu möglichen Fehlern:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`
Netzwerkfehler.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      Die Antwort weist kein korrektes Format auf.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      In der Antwort ist kein `contextData`-Parameter enthalten.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` ist nicht enthalten `contextData`.

   * `Analytics - Acquisition referrer timed out`

      Fehler beim Abrufen der Antwort in der durch `referrerTimeout` definierten Zeit. Erhöhen Sie den Wert und versuchen Sie es erneut. Sie sollten darüber hinaus sicherstellen, dass Sie den Akquiselink geöffnet haben, bevor Sie die App installieren, und dass Sie dasselbe Netzwerk verwenden, wenn Sie auf die URL klicken und die App öffnen.

      Beachten Sie die folgenden Informationen:

      * Der Akquiseserver bietet eine Zuordnungsübereinstimmung, die auf der IP-Adresse und den „user-agent“-Informationen basiert, die beim Klicken auf den Link (Schritt 6) und beim Start der App (Schritt 7) aufgezeichnet werden.

         Sie sollten sich im selben Netzwerk befinden, wenn Sie auf die URL klicken und wenn Sie die App öffnen.

      * Durch die Verwendung von HTTP-Überwachungstools können über die App gesendete Treffer überwacht werden, um die Verifizierung der Akquisezuordnung bereitzustellen.

         You should see one `/v3/<appid>/start` request and one `/v3/<appid>/end` request sent to the acquisition server. Variationen in „user-agent“ führen möglicherweise dazu, dass die Zuordnung fehlschlägt.

         >[!TIP]
         >
         >Stellen Sie sicher `https://c00.adobe.com/v3/<appid>/start` , dass und `https://c00.adobe.com/v3/<appid>/end` dieselben Benutzeragenten-Werte vorhanden sind.

      * Der Akquiselink und der Treffer aus dem SDK sollten dasselbe HTTP-/HTTPS-Protokoll verwenden.

         Wenn sie unterschiedliche Protokolle aufweisen (beispielsweise verwendet der Link HTTP und das SDK HTTPS), unterscheidet sich die IP-Adresse ggf. für jede Anforderung (bei einigen Betreibern) und die Zuordnung schlägt fehl.
