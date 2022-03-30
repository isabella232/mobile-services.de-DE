---
description: Die folgenden Informationen helfen Ihnen dabei, eine Hin&Zurück-Abfrage für einen Legacy-Akquise-Kampagnenlink auf einem Android-Gerät durchzuführen.
keywords: Android;Bibliothek;Mobile;SDK
solution: Experience Cloud Services,Analytics
title: Testen der Legacy-Akquise
topic-fix: Developer and implementation
uuid: bb7ace96-68eb-4f43-b3cf-af80730b9cee
exl-id: 43e3b24e-e8bc-407c-b788-5ab85e459a90
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 100%

---

# Testen der Legacy-Akquise {#testing-legacy-acquisition}

Die folgenden Informationen helfen Ihnen dabei, eine Hin&amp;Zurück-Abfrage für einen Legacy-Akquise-Kampagnenlink auf einem Android-Gerät durchzuführen.

Wenn die App noch nicht in Google Play vorhanden ist, können Sie beim Erstellen des Kampagnen-Links eine beliebige App als Ziel auswählen. Dies wirkt sich nur auf die App aus, zu der der Akquise-Server die Umleitung vornimmt, nachdem Sie auf den Akquise-Link geklickt haben, nicht aber auf die Fähigkeit, den Akquise-Link zu testen. Zeichenfolgenparameter der Abfrage werden an den Google Play Store übergeben, der bei der Installation im Zuge einer Kampagnenübertragung an die App übergeben wird. Für die Tests zur Akquise von Hin&amp;Zurück-Abfragen mobiler Apps ist die Simulation dieser Art von Übertragungen erforderlich.

Vor jedem Testlauf muss die App neu installiert bzw. müssen ihre Daten in den **[!UICONTROL Einstellungen]** gelöscht werden. So wird gewährleistet, dass die anfänglichen Lebenszyklusmetriken mit den Abfragezeichenfolgen-Parametern der Kampagne gesendet werden, wenn die App zum ersten Mal gestartet wird.

1. Generieren Sie in der Mobile Services UI eine URL für eine bestehende Akquise-Kampagne.

   Weitere Informationen finden Sie unter [Verwenden von Legacy-Akquise-Links](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).
1. Verbinden Sie das Gerät mit einem Computer, starten Sie ADB Shell und rufen Sie dann die Anwendung auf dem Gerät auf.
1. Senden Sie einen Broadcast im folgenden Format:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. Führen Sie die folgenden Schritte aus:
   1. Ersetzen Sie `com.example.adobetesttapp.com` durch den Reverse-DNS-Eintrag Ihrer Anwendung.
   1. Aktualisieren Sie die Empfängerreferenz mit der Empfängerreferenz für den Standort des Kampagnen-Trackings in Ihrer App.
   1. Ersetzen Sie die Werte für `utm_source`, `utm_medium`, `utm_term`, `utm_content`, `utm_campaign` usw. durch die richtigen Werte.

Bei erfolgreicher Übertragung wird eine Antwort wie die folgende angezeigt:

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

Sie werden auch eine Bildanforderung sehen, die an die Datenerfassungs-Server von Adobe gesendet wurde. Wenn das SDK die gesamte Zeitdauer des Referrer-Timeouts (wie in Schritt 1 festgelegt) mit einer Bildanforderung ohne Kampagne wartet, ist die Übertragung fehlgeschlagen.
