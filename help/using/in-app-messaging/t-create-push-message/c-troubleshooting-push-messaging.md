---
description: Mithilfe dieser Informationen können Probleme mit Push-Nachrichten behoben werden.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: Fehlerbehebung für Push-Nachrichten
topic-fix: Metrics
uuid: c7be4ab7-0cfe-4296-84a8-01412f4fd93f
exl-id: 56feb8e1-e196-4b70-8240-6e41581ca602
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 100%

---

# Fehlerbehebung für Push-Nachrichten {#troubleshooting-push-messaging}

Mithilfe dieser Informationen können Probleme mit Push-Nachrichten behoben werden.

## Warum gibt es beim Senden von Push-Nachrichten manchmal Verzögerungen?

Folgende Verzögerungen können bei Push-Nachrichten für Mobile Services auftreten:

* **Warten auf einen Analytics-Treffer**

   Jede Report Suite verfügt über eine Einstellung, die festlegt, wann eingehende Analytics-Treffer verarbeitet werden sollen. Standardmäßig geschieht dies einmal pro Stunde.

   Die eigentliche Verarbeitung von Analytics-Treffern kann bis zu 30 Minuten dauern, in der Regel sind es jedoch 15 bis 20 Minuten. Beispielsweise verarbeitet eine Report Suite Treffer jede Stunde. Wenn Sie die erforderliche Verarbeitungszeit von maximal 30 Minuten berücksichtigen, kann es bis zu 90 Minuten dauern, bis ein eingehender Treffer für eine Push-Nachricht verfügbar ist. Wenn ein Benutzer die App um 9:01 Uhr gestartet hat, wird der Treffer in der Mobile Services-Benutzeroberfläche als neuer eindeutiger Benutzer zwischen 10:15 und 10:30 Uhr angezeigt.

* **Warten auf den Push-Dienst**

   Der Push-Dienst (APNS oder GCM) versendet die Nachricht möglicherweise nicht sofort. Zwar sind sie ungewöhnlich, jedoch wurden bereits Wartezeiten von 5–10 Minuten festgestellt. Informationen dazu, ob die Push-Nachricht gesendet wurde, finden Sie in der **[!UICONTROL Berichtsansicht]** der Push-Nachricht. Suchen Sie dort in der Tabelle **[!UICONTROL Nachrichtenverlauf]** nach der Nachricht und ermitteln Sie die Anzahl **[!UICONTROL Veröffentlicht]**.

   >[!TIP]
   >
   >Die Push-Dienste garantieren nicht, dass eine Nachricht gesendet wird. Weitere Informationen zur Zuverlässigkeit der Dienste finden Sie in der entsprechenden Dokumentation:
   >
   >* **APNS**: [Servicequalität](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5)
   >* **FCM**: [Lebensdauer einer Nachricht](https://firebase.google.com/docs/cloud-messaging/concept-options#lifetime)


## Warum ist mein Android-GCM-API-Schlüssel ungültig?

* **Ungültiger API-Schlüssel**

   Ihr API-Schlüssel ist möglicherweise aus den folgenden Gründen ungültig:

   * Der von Ihnen angegebene API-Schlüssel ist kein Server-Schlüssel mit dem richtigen GCM-API-Schlüsselwert.
   * Der Serverschlüssel hat die IPs zugelassen und hindert die Server von Adobe am Senden einer Push-Nachricht.

* **Bestimmen der Gültigkeit des API-Schlüssels**

   Führen Sie den folgenden Befehl aus, um die Gültigkeit Ihres API-Schlüssels zu ermitteln:

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   Ein zurückgegebener 401-HTTP-Statuscode bedeutet, dass Ihr API-Schlüssel ungültig ist. Andernfalls wird Folgendes angezeigt:

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   Sie können auch die Gültigkeit eines Registrierungstokens überprüfen, indem Sie `"ABC"` durch das entsprechende Token ersetzen.

## Warum funktioniert mein APNS-Zertifikat nicht?

Ihr APNS-Zertifikat ist möglicherweise aus den folgenden Gründen ungültig:

* Möglicherweise verwenden Sie ein Sandbox-Zertifikat anstelle des Produktionszertifikats.
* Sie verwenden ein neues Produktions-/Sandbox-Zertifikat, das nicht unterstützt wird.
* Sie verwenden eine `.p8`-Datei anstelle einer `.p12`-Datei.

## Beheben von Push-Nachrichtenfehlern

Das folgende Beispiel zeigt, wie Sie einen Push-Fehler bei der Verwendung einer VRS beheben können.

Der folgende Kunde verfügt über zwei iOS-Apps:

* App-Name: FotoShop_app_iOS
   * Übergeordnete RSID: AllAdobe FotoShop_apps
   * VRSID: FotoShop_iOS_app_SF
   * VRSID-Definitionssegment: `a.appid contains "PhotoShop_iOS_app_SF"`
* App-Name: FotoShop_app_iOS
   * Übergeordnete RSID: AllAdobe FotoShop_apps
   * RSID: PhotoShop_iOS_app_LA
   * VRSID-Definitionssegment: `a.os contains "iOS"`

In diesem Beispiel erhalten wie erwartet alle Benutzer der *PhotoShop_iOS_app_SF-App* diese Push-Nachricht, wenn ein Photoshop-Mitarbeiter eine Push-Nachricht an die *PhotoShop_iOS_app_SF*-App sendet. Wenn der Mitarbeiter jedoch eine Nachricht an die *PhotoShop_iOS_app_LA*-App sendet, wird die Nachricht aufgrund des falschen VRSID-Definitionssegments (`iOS` anstatt `a.os contains "PhotoShop_iOS_app_LA"`) an **alle** iOS-Benutzer unter *AllAdobe PhotoShop_apps* gesendet. Obwohl die Nachricht auch an die Benutzer von *PhotoShop_iOS_app_LA* gesendet wird, sorgt sie dafür, dass die Push-IDs für *PhotoShop_iOS_app_SF*-Benutzer auf die Sperrliste gesetzt werden, da die *PhotoShop_iOS_app_SF*-App über ein anderes Zertifikat verfügt. Wenn das Segment als `a.os contains "PhotoShop_iOS_app_LA"` definiert worden wäre, wäre die Nachricht nur an *PhotoShop_iOS_app_LA*-Benutzer gesendet worden.

Wenn die Push-IDs für *PhotoShop_iOS_app_SF* mit dem *PhotoShop_IOS_app_LA*-Push-Zertifikat übergeben werden, werden sie als `invalid` zurückgegeben.

>[!CAUTION]
>
>Wenn Sie eine Push-Nachricht für eine App erstellen, die eine VRS verwendet, und auf **[!UICONTROL Speichern und Senden]** klicken, wird ein Warnhinweis angezeigt, um Sie daran zu erinnern, dass jede aufgeführte App über ein gültiges Zertifikat verfügen **muss**. Wenn nicht **alle** Apps über ein gültiges Zertifikat verfügen, werden Ihre Zielgruppensegmente möglicherweise auf unbestimmte Zeit auf die Sperrliste gesetzt, sodass Sie betroffenen Benutzern künftig keine Push-Nachrichten mehr senden können. Weitere Informationen zu Zielgruppensegmenten finden Sie unter [Zielgruppe: Zielgruppenoptionen für Push-Nachrichten definieren und konfigurieren](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).
