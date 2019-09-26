---
description: Mithilfe dieser Informationen können Sie die integrierten Berichte durch Hinzufügen zusätzlicher Filter (Segmente) anpassen.
keywords: mobile
seo-description: Mithilfe dieser Informationen können Sie die integrierten Berichte durch Hinzufügen zusätzlicher Filter (Segmente) anpassen.
seo-title: Filter zu Berichten hinzufügen
solution: Marketing Cloud,Analytics
title: Filter zu Berichten hinzufügen
topic: Berichte, Metriken
uuid: 19c395cc-2e07-4588-825b-f2f8b10a87c1
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Add filters to reports{#add-filters-to-reports}

Mithilfe dieser Informationen können Sie die integrierten Berichte durch Hinzufügen zusätzlicher Filter (Segmente) anpassen.

>[!IMPORTANT]
>
>Mobile app metrics are also available in marketing reports &amp; analytics, ad hoc analysis, data warehouse, and other Analytics reporting interfaces. Wenn eine Aufschlüsselung oder ein Berichtstyp in Adobe Mobile nicht zur Verfügung steht, kann er mithilfe einer anderen Berichtsschnittstelle generiert werden.

Im folgenden Beispiel passen wir den Bericht **[!UICONTROL Benutzer und Sitzungen]an, die Anweisungen gelten jedoch für alle Berichte.**

1. Öffnen Sie Ihre App und klicken Sie auf **Nutzung** &gt; **[!UICONTROL Benutzer und Sitzungen]**.

   ![](assets/customize1.png)

   Dieser Bericht enthält einen kompletten zeitlichen Überblick über unsere App-Nutzer. Allerdings werden hier Metriken sowohl für iOS- als auch für Android-Versionen in der gleichen Report Suite erfasst. Wir können die Benutzer nach ihrem mobilen Betriebssystem segmentieren, indem wir der Metrik „Benutzer“ einen benutzerdefinierten Filter hinzufügen.

1. Click **[!UICONTROL Customize]**.

   ![](assets/customize2.png)

1. Under **[!UICONTROL Users]**, click **[!UICONTROL Add Filter]** and click **[!UICONTROL Add Rule]**.

1. Select **[!UICONTROL Operating Systems]**, and from the drop-down list, and select **[!UICONTROL iOS]**.

   ![](assets/customize3.png)

   Um Android als Filter hinzuzufügen, müssen Sie diesen Schritt wiederholen.

1. Click **[!UICONTROL And]**, select **[!UICONTROL Operating Systems]** from the drop-down list, and select **[!UICONTROL Android]**.

   Die Filter sollten jetzt wie folgt aussehen:

   ![](assets/customize4.png)

1. Klicken Sie auf **[!UICONTROL Aktualisieren]**.
1. To regenerate the report, click **[!UICONTROL Run]**.

   Dieser Bericht zeigt die Benutzer aufgeschlüsselt nach Betriebssystem an. Der Berichtstitel wurde entsprechend den angewendeten Filtern geändert.

   ![](assets/customize5.png)

   You can customize this report more. Ab iOS 8.3 können Sie die Metrik "Erste Starts"mit einem Filter für die Betriebssystemversion iOS 8.3 hinzufügen, um zu sehen, wie viele iOS 8.3-Kunden ihre Apps aktualisiert und einen ersten Start durchgeführt haben.
1. Under **[!UICONTROL First Launches]**, click **[!UICONTROL Add Filter]**, click **[!UICONTROL Add Rule]**, select **[!UICONTROL Operating Systems]** from the drop-down list, and select **[!UICONTROL iOS]**.
1. Click **[!UICONTROL And]**, select **[!UICONTROL Operating System Versions]** from the drop-down list, and select **[!UICONTROL iOS 8.3]**.

   Die Filter sollten jetzt wie folgt aussehen:

   ![](assets/customize6.png)

1. Click **[!UICONTROL Update]** and **[!UICONTROL Run]**.

   Der Bericht zeigt jetzt die Benutzer mit iOS 8.3 an, die die App zum ersten Mal gestartet haben.

   ![](assets/customize7.png)

   Probieren Sie die verschiedenen Optionen im Berichtsanpassungsmenü ruhig einmal aus. Ihre Favoriten können Sie mit einem Lesezeichen versehen. Report URLs in Adobe Mobile are functional and can be emailed or added to your favorites.
