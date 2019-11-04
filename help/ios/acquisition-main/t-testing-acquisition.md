---
description: Diese Informationen helfen Ihnen dabei, einen alten Akquise-Kampagnenlink basierend auf einem Gerätefingerabdruck zu übertragen.
seo-description: Diese Informationen helfen Ihnen dabei, einen alten Akquise-Kampagnenlink basierend auf einem Gerätefingerabdruck zu übertragen.
seo-title: Testen der Legacy-Akquise
solution: Experience Cloud,Analytics
title: Testen der Legacy-Akquise
uuid: e0591f4a-e26b-4fe4-97c1-a6831a926fa5
translation-type: ht
source-git-commit: 06144a1695ac40ce984656491456968888f9e96e

---


# Testen der Legacy-Akquise{#testing-legacy-acquisition}

Diese Informationen helfen Ihnen dabei, einen alten Akquise-Kampagnenlink basierend auf einem Gerätefingerabdruck zu übertragen.

Wenn die mobile App noch nicht in Google Play vorhanden ist, können Sie beim Erstellen des Kampagnenlinks eine beliebige mobile App als Ziel auswählen. Dies wirkt sich nur darauf aus, zu welcher App der Akquiseserver die Umleitung vornimmt, nachdem Sie auf den Akquiselink geklickt haben, nicht aber auf die Fähigkeit, den Akquiselink zu testen.

1. Gehen Sie zu **[!UICONTROL Verwenden von Legacy-Akquise-Links]** in Adobe Mobile Services und generieren Sie eine Akquise-Kampagnen-URL.

   Weitere Informationen finden Sie unter [Verwenden von Legacy-Akquise-Links](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).

1. Klicken Sie auf dem Mobilgerät, auf dem Sie die App installieren, auf den generierten Link.

   Die Server von Adobe (`c00.adobe.com`) speichern den Fingerabdruck und nehmen eine Umleitung zum App-Store vor. Die App muss nicht für Testzwecke heruntergeladen werden.

1. Starten Sie auf demselben Mobilgerät, das Sie in Schritt 2 verwendet haben, die Anwendung das erste Mal.

   Die einfachste Möglichkeit, sicherzustellen, dass dies passiert, besteht darin, die App zu löschen und erneut zu installieren.

Beachten Sie die folgenden Informationen:

* Der Akquiseserver bietet eine Zuordnungsübereinstimmung, die auf der IP-Adresse und den „user-agent“-Informationen basiert, die beim Klicken auf den Link (Schritt 2) und beim Start der App (Schritt 3) aufgezeichnet werden.
* Durch die Verwendung von HTTP-Überwachungstools können über die App gesendete Treffer überwacht werden, um die Verifizierung der Akquisezuordnung bereitzustellen.

>[!TIP]
>
>Variationen in „user-agent“ führen möglicherweise dazu, dass die Zuordnung fehlschlägt.
