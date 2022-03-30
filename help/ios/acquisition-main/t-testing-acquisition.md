---
description: Diese Informationen helfen Ihnen dabei, einen alten Akquise-Kampagnenlink basierend auf einem Gerätefingerabdruck zu übertragen.
solution: Experience Cloud Services,Analytics
title: Testen der Legacy-Akquise
uuid: e0591f4a-e26b-4fe4-97c1-a6831a926fa5
exl-id: 431dc400-952a-4515-9d14-ba2efef4b2c4
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 100%

---

# Testen der Legacy-Akquise {#testing-legacy-acquisition}

Diese Informationen helfen Ihnen dabei, einen alten Akquise-Kampagnenlink basierend auf einem Gerätefingerabdruck zu übertragen.

Wenn die App noch nicht in Google Play vorhanden ist, können Sie beim Erstellen des Kampagnen-Links eine beliebige App als Ziel auswählen. Dies wirkt sich nur darauf aus, zu welcher App der Akquiseserver die Umleitung vornimmt, nachdem Sie auf den Akquiselink geklickt haben, nicht aber auf die Fähigkeit, den Akquiselink zu testen.

1. Navigieren Sie zu **[!UICONTROL Veraltete Akquiselinks verwenden]** in Adobe Mobile Services und generieren Sie eine Akquisekampagnen-URL.

   Weitere Informationen finden Sie unter [Verwenden von Legacy-Akquise-Links](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).

1. Klicken Sie auf dem Mobilgerät, auf dem Sie die App installieren, auf den generierten Link.

   Die Server von Adobe (`c00.adobe.com`) speichern den Fingerabdruck und nehmen eine Umleitung zum App-Store vor. Die App muss nicht für Testzwecke heruntergeladen werden.

1. Starten Sie auf demselben Mobilgerät, das Sie in Schritt 2 verwendet haben, die Anwendung das erste Mal.

   Die einfachste Möglichkeit, dies sicherzustellen, besteht darin, die App zu löschen und erneut zu installieren.

Beachten Sie die folgenden Informationen:

* Der Akquise-Server bietet eine Zuordnungsübereinstimmung, die auf IP-Adressen- und „user-agent“-Informationen basiert, die beim Klicken auf den Link (Schritt 2) und beim Start der Mobile App (Schritt 3) aufgezeichnet werden.
* Durch die Verwendung von HTTP-Überwachungstools können über die App gesendete Treffer überwacht werden, um die Verifizierung der Akquisezuordnung bereitzustellen.

>[!TIP]
>
>Variationen in „user-agent“ führen möglicherweise dazu, dass die Zuordnung fehlschlägt.
