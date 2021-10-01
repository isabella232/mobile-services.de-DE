---
description: Mithilfe dieser Informationen können Sie die integrierten Berichte durch Hinzufügen zusätzlicher Filter (Segmente) anpassen.
keywords: mobile
solution: Experience Cloud,Analytics
title: Filter zu Berichten hinzufügen
topic-fix: Reports,Metrics
uuid: 19c395cc-2e07-4588-825b-f2f8b10a87c1
exl-id: eb0589e9-668e-42d7-8f7a-00d7f0a2e3ff
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 100%

---

# Filter zu Berichten hinzufügen {#add-filters-to-reports}

Mithilfe dieser Informationen können Sie die integrierten Berichte durch Hinzufügen zusätzlicher Filter (Segmente) anpassen.

>[!IMPORTANT]
>
>App-Metriken sind auch in Marketing Reports &amp; Analytics, Ad-hoc-Analysen, Data Warehouse- und anderen Analytics-Schnittstellen für die Berichterstellung verfügbar. Wenn eine Aufschlüsselung oder ein Berichtstyp in Adobe Mobile nicht zur Verfügung steht, kann er mithilfe einer anderen Berichtsschnittstelle generiert werden.

Im folgenden Beispiel passen wir den Bericht **[!UICONTROL Benutzer und Sitzungen]** an, die Anweisungen gelten jedoch für alle Berichte.

1. Öffnen Sie Ihre App und klicken Sie auf **[!UICONTROL Nutzung]** > **[!UICONTROL Benutzer und Sitzungen]**.

   ![](assets/customize1.png)

   Dieser Bericht bietet einen vollständigen Überblick über die App-Benutzer im Zeitverlauf. Metriken für iOS- und Android-Versionen dieser App werden jedoch in derselben Report Suite erfasst. Wir können Benutzer nach Mobilbetriebssystem segmentieren, indem wir einen benutzerdefinierten Filter zur Benutzermetrik hinzufügen.

1. Klicken Sie auf **[!UICONTROL Anpassen]**.

   ![](assets/customize2.png)

1. Klicken Sie unter **[!UICONTROL Benutzer]** auf **[!UICONTROL Filter hinzufügen]** und klicken Sie auf **[!UICONTROL Regel hinzufügen]**.

1. Wählen Sie **[!UICONTROL Betriebssysteme]** und anschließend **[!UICONTROL iOS]** aus der Dropdown-Liste aus.

   ![](assets/customize3.png)

   Wiederholen Sie diesen Schritt, um Android als Filter hinzuzufügen.

1. Klicken Sie auf **[!UICONTROL Und]**, wählen Sie **[!UICONTROL Betriebssysteme]** aus der Dropdown-Liste und anschließend **[!UICONTROL Android]** aus.

   Die Filter sollten jetzt wie folgt aussehen:

   ![](assets/customize4.png)

1. Klicken Sie auf **[!UICONTROL Aktualisieren]**.
1. Um den Bericht neu zu erstellen, klicken Sie auf **[!UICONTROL Ausführen]**.

   Dieser Bericht zeigt nun Benutzer aufgeschlüsselt nach Betriebssystem an. Der Berichttitel wurde geändert, um den Filtern zu entsprechen, die auf den Bericht angewendet wurden.

   ![](assets/customize5.png)

   Sie können den Bericht aber noch weiter anpassen. Ab iOS 8.3 können Sie die Metrik „Erste Starts“ mit einem Filter für die Betriebssystemversion iOS 8.3 hinzufügen, um zu sehen, wie viele iOS 8.3-Kunden ihre Apps aktualisiert und einen ersten Start durchgeführt haben.
1. Klicken Sie unter **[!UICONTROL Erste Starts]** auf **[!UICONTROL Filter hinzufügen]** und dann auf **[!UICONTROL Regel hinzufügen]**. Wählen Sie aus der Dropdown-Liste den Eintrag **[!UICONTROL Betriebssysteme]** und dann **[!UICONTROL iOS]** aus.
1. Klicken Sie auf **[!UICONTROL Und]** und wählen Sie aus der Dropdown-Liste den Eintrag **[!UICONTROL Betriebssystemversionen]** und dann **[!UICONTROL iOS 8.3]** aus.

   Die Filter sollten jetzt wie folgt aussehen:

   ![](assets/customize6.png)

1. Klicken Sie auf **[!UICONTROL Aktualisieren]** und **[!UICONTROL Ausführen]**.

   Dieser Bericht zeigt jetzt Benutzer mit iOS 8.3 an, die die App zum ersten Mal gestartet haben.

   ![](assets/customize7.png)

   Nehmen Sie sich etwas Zeit, um die verschiedenen Optionen im Menü zur Berichtsanpassung zu testen und sicherzustellen, dass Sie Ihre Favoriten mit einem Lesezeichen versehen. Berichts-URLs in Adobe Mobile sind funktionsfähig und können per E-Mail versendet oder Ihren Favoriten hinzufügt werden.
