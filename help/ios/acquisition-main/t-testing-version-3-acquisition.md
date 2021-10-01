---
description: Diese Informationen helfen Ihnen dabei, einen V3-Akquise-Kampagnenlink basierend auf einem Gerätefingerabdruck zu übertragen.
solution: Experience Cloud,Analytics
title: Testen der V3-Akquise
uuid: 89137ccf-4839-4b37-926e-303cf8e511a5
exl-id: 3cf66802-1f2c-428f-86ef-a9afc57e3470
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 100%

---

# V3-Akquise testen {#testing-v-acquisition}

Diese Informationen helfen Ihnen dabei, einen V3-Akquise-Kampagnenlink basierend auf einem Gerätefingerabdruck zu übertragen.

>[!IMPORTANT]
>
>Die V3-Akquise bezieht sich auf die Akquise-Links, die Sie mithilfe des Akquise-Builders auf der Adobe Mobile Services-Benutzeroberfläche erstellen. Um diese Funktion verwenden zu können, müssen Sie auf die iOS SDK-Version 4.6.0 oder höher aktualisieren.

Wenn sich die Mobile App noch nicht im App Store befindet, wählen Sie beim Erstellen des Links „Kampagne“ eine beliebige Mobile App als Ziel aus. Dies betrifft nur die App, zu der Sie der Akquise-Server weiterleitet, nachdem Sie auf den Akquise-Link geklickt haben, hat jedoch keine Auswirkungen auf die Fähigkeit, den Link zu testen.

1. Bearbeiten Sie die Aufgaben mit den Voraussetzungen unter [Mobile App Acquisition](/help/ios/acquisition-main/acquisition.md).
1. Navigieren Sie zu **[!UICONTROL Akquise-Builder]** auf der Adobe Mobile Services-Benutzeroberfläche und generieren Sie eine Akquise-Kampagnen-URL.

   Beispiel:

   ```
   https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```


   Wenn Sie im Akquise-Link sowohl auf die iOS- als auch auf die Android-App verweisen, nutzen Sie den Apple Store als standardmäßigen Store.
1. Öffnen Sie den generierten Link in einem Desktopbrowser und navigieren Sie zu `https://c00.adobe.com/v3/<appid>/end`.

   Es sollte `contextData` in der JSON-Antwort angezeigt werden:

   ```js
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.
   ```

   Wenn die Kontextdaten ( `contextData` ) nicht angezeigt werden oder Teile fehlen, stellen Sie sicher, dass die Akquise-URL das in [Akquise-Link manuell erstellen](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md) angegebene Format aufweist.
1. Stellen Sie sicher, dass die folgenden Einstellungen in Ihrer Konfigurationsdatei vorhanden sind:

   | Wenn | Wert |
   |--- |--- |
   | Akquise | Der Server sollte `c00.adobe.com` sein. *`appid`* sollte der *`appid`* in Ihrem Akquise-Link entsprechen. |
   | analytics | `referrerTimeout` sollte einen Wert größer als 0 aufweisen. |


1. (Bedingt) Wenn die Einstellung `ssl` in der Konfigurationsdatei Ihrer App „true“ lautet, sollten Sie Ihren Akquiselink zum Verwenden des HTTPS-Protokolls aktualisieren.
1. Klicken Sie auf dem Mobilgerät auf den generierten Link, auf dem Sie die App installieren möchten.

   Die Server von Adobe (`c00.adobe.com`) speichern den Fingerabdruck und nehmen eine Umleitung zum App-Store vor. Die App muss nicht für Testzwecke heruntergeladen werden.
1. Starten Sie die Anwendung erstmals auf demselben Mobilgerät, das Sie in Schritt 6 verwendet haben.

   Bei Bedarf können Sie die App löschen und erneut installieren.
1. (Optional) Sie können die Debugging-Protokollierung des SDK aktivieren, um zusätzliche Informationen zu erhalten.

   Wenn alles funktioniert, sollten Sie folgende Protokolle erhalten:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   Falls die Protokolle oben nicht angezeigt werden, sollten Sie sicherstellen, dass Sie die Schritte 4 und 5 abgeschlossen haben.

   Im Folgenden finden Sie einige Informationen zu möglichen Fehlern:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`
Netzwerkfehler.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      Die Antwort weist kein korrektes Format auf.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      In der Antwort ist kein `contextData`-Parameter enthalten.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` ist nicht in `contextData` vorhanden.

   * `Analytics - Acquisition referrer timed out`

      Fehler beim Abrufen der Antwort in der durch `referrerTimeout` definierten Zeit. Erhöhen Sie den Wert und versuchen Sie es erneut. Sie sollten auch sicherstellen, dass Sie den Akquise-Link vor der Installation der App geöffnet haben und dass Sie dasselbe Netzwerk verwenden, wenn Sie auf die URL klicken und die App öffnen.

      Beachten Sie die folgenden Informationen:

      * Der Akquiseserver bietet eine Zuordnungsübereinstimmung, die auf der IP-Adresse und den „user-agent“-Informationen basiert, die beim Klicken auf den Link (Schritt 6) und beim Start der App (Schritt 7) aufgezeichnet werden.

         Sie sollten sich im selben Netzwerk befinden, wenn Sie auf die URL klicken und wenn Sie die App öffnen.

      * Durch die Verwendung von HTTP-Überwachungstools können über die App gesendete Treffer überwacht werden, um die Verifizierung der Akquisezuordnung bereitzustellen.

         Es sollten eine Anfrage vom Typ `/v3/<appid>/start` und eine Anfrage vom Typ `/v3/<appid>/end` angezeigt werden, die an den Akquiseserver gesendet wurden. Variationen in „user-agent“ führen möglicherweise dazu, dass die Zuordnung fehlschlägt.

         >[!TIP]
         >
         >Vergewissern Sie sich, dass `https://c00.adobe.com/v3/<appid>/start` und `https://c00.adobe.com/v3/<appid>/end` über dieselben Werte für „user-agent“ verfügen.

      * Der Akquiselink und der Treffer aus dem SDK sollten dasselbe HTTP-/HTTPS-Protokoll verwenden.

         Wenn sie unterschiedliche Protokolle aufweisen (beispielsweise verwendet der Link HTTP und das SDK HTTPS), unterscheidet sich die IP-Adresse ggf. für jede Anforderung (bei einigen Betreibern), und die Zuordnung schlägt fehl.
