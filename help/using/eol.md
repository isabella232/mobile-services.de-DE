---
title: Adobe Mobile Services end-of-life FAQ
description: Erhalten Sie Antworten auf häufig gestellte Fragen zur Ankündigung zum Ende des Lebenszyklus von Adobe Mobile Services.
source-git-commit: a0f834247c328b40d0f47fdf515c239cf66b7566
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 3%

---

# Häufig gestellte Fragen zur Einstellung der Adobe Mobile Services

Adobe Mobile Service&#39;s end-of-life date is **December 31, 2022**.

## What is happening?

Mobile Services endet am 31. Dezember 2022. Mobile Services, die eine mobilzentrierte Benutzeroberfläche, Akquise, Deep-Linking, In-App-Nachrichten, Push-Benachrichtigungen und geografischen Standort unterstützen, werden nach diesem Datum nicht mehr unterstützt.

## Was ist enthalten und was ist nicht enthalten?

Diese Einstellung umfasst nur die Adobe Mobile Services, die eigenständige Plattform unter [mobilemarketing.adobe.com](https://mobilemarketing.adobe.com). Die Mobile-SDKs der Version 4, die auf diese Benutzeroberfläche angewiesen sind, wurden am 31. August 2021 eingestellt.

This end-of-life does NOT include Adobe Analytics for mobile apps, part of the Adobe Experience Platform Mobile SDKs. Diese Funktionen, darunter das In-App-Verhalten, die Lebenszyklusanalyse, das Tracking von Interaktionen mit Nachrichten und Zielgruppenprofile, werden von Adobe weiterhin unterstützt.

## Warum wird die Funktion eingestellt?

Da Adobe seine mobilen Marketingfunktionen weiter ausbaut, werden Funktionen, die zuvor in Mobile Services verfügbar waren, in Adobe Experience Cloud-Lösungen veröffentlicht oder über Adobe Exchange Premier Partners angeboten. This transition provides you with more powerful and flexible mobile marketing capabilities.

## Was passiert mit bestehenden, in Mobile Services erstellten Verarbeitungsregeln?

[Verarbeitungsregeln](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html) , die in der Benutzeroberfläche von Mobile Services erstellt oder generiert wurden, werden in H2 2022 automatisch nach Adobe Analytics migriert, bevor das Enddatum für Mobile Services erreicht ist. Migrierte Verarbeitungsregeln verhalten sich ähnlich wie andere Verarbeitungsregeln in Adobe Analytics, wo Sie sie frei anzeigen oder bearbeiten können. No user action is required for this migration.

Nachdem der Mobile-Dienst eingestellt wurde, werden alle Verarbeitungsregellogiken ausschließlich innerhalb von Adobe Analytics verarbeitet, in der Regel einschließlich der Verwendung von [Kontextdatenvariablen](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/contextdata.html?lang=de).

## What transition options are available?

Adobe bietet je nach Anwendungsfall Ihres Unternehmens drei Übergangspfade.

1. **In-App-Nachrichten und Push-Benachrichtigungen**: Adobe kann Ihre Messaging-Workflows in Adobe Journey Optimizer überführen. Mit diesem Produkt können Unternehmen Erlebnisse auf der gesamten Journey optimieren und personalisieren, einschließlich mobiler Nachrichten.
1. **Akquise und Deep-Linking**: Akquise und Deep-Linking werden über das Adobe Exchange Premier Partners-Programm angeboten. Zu diesen Partnern gehören Adjust, AppsFlyer und Branch, die umfangreiche Akquise-Funktionen anbieten. Das Partnerteam der Adobe kann geeignete Einführungsmaßnahmen treffen, um sicherzustellen, dass Sie die für Ihre Anforderungen am besten geeignete Lösung finden.
1. **Places Service**: Der Places Service bietet zusätzliche Geolokationsfunktionen. Siehe [Places Service-Dokumentation](https://experienceleague.adobe.com/docs/places/using/home.html?lang=de).

## Wo kann ich hingehen, wenn ich Fragen habe?

Siehe [Adobe Mobile Services - Spark-Seite zum Ende der Lebensdauer](https://spark.adobe.com/page/C6D30y09zaRpD/) für weitere Informationen. Wenden Sie sich bei weiteren Fragen an Ihren Kundenbetreuer.
