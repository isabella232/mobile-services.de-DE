---
description: Mithilfe dieser Informationen können Sie ermitteln, wie Abstürze verfolgt werden und wie Sie am besten mit fälschlich gemeldeten Abstürzen umgehen.
seo-description: Mithilfe dieser Informationen können Sie ermitteln, wie Abstürze verfolgt werden und wie Sie am besten mit fälschlich gemeldeten Abstürzen umgehen.
seo-title: App-Abstürze verfolgen
solution: Experience Cloud,Analytics
title: App-Abstürze verfolgen
topic: Developer and implementation
uuid: 4f81988b-198a-4ba9-ad53-78af90e43856
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 79%

---


# Nachverfolgen von App-Abstürzen {#track-app-crashes}

Mithilfe dieser Informationen können Sie ermitteln, wie Abstürze verfolgt werden und wie Sie am besten mit fälschlich gemeldeten Abstürzen umgehen.

>[!IMPORTANT]
>
>Sie sollten ein Upgrade auf iOS-SDK-Version 4.8.6 vornehmen, das kritische Änderungen enthält, die verhindern, dass falsche Abstürze gemeldet werden.

## Wann meldet Adobe einen Absturz?

Wenn Ihre Anwendung beendet wird, ohne dass sie zunächst in den Hintergrund versetzt wurde, meldet das SDK beim nächsten Start Ihrer App einen Absturz.

## Wie funktionieren Absturzberichte?

iOS verwendet Systembenachrichtigungen, die Entwicklern ermöglichen, unterschiedliche Status und Ereignisse im Anwendungslebenszyklus zu verfolgen und darauf zu reagieren.

Das Adobe Mobile iOS-SDK verfügt über einen Benachrichtigungs-Handler, der auf die Benachrichtigung `UIApplicationDidEnterBackgroundNotification` reagiert. In diesem Code wird ein Wert festgelegt, der angibt, dass der Benutzer die App im Hintergrund erstellt hat. Bei einem nachfolgenden Start wird ein Absturz gemeldet, wenn dieser Wert nicht gefunden werden kann.

## Warum werden Abstürze von Adobe auf diese Weise gemessen?

Dieser Ansatz, Abstürze zu messen, bietet eine allgemeine Antwort auf die Frage „*Hat der Benutzer meine App mit Absicht beendet?*“

Von Unternehmen wie Apteligent (hieß zuvor Crittercism) bereitgestellte Absturzberichtsbibliotheken verwenden einen globalen `NSException`-Handler, um ausführlichere Absturzberichte bereitzustellen. Ihre App darf nicht mehr als einen dieser Handlertypen aufweisen. Adobe hat sich im Bewusstsein, dass unsere Kunden möglicherweise andere Absturzberichtsanbieter verwenden, dazu entschieden, keinen globalen `NSException`-Handler zu implementieren, der dazu dient, Build-Fehler zu verhindern.

## Wie kann es passieren, dass fälschlicherweise ein Absturz gemeldet wird?

Es ist bekannt, dass die folgenden Szenarien fälschlicherweise zu einem Absturz führen, der vom SDK gemeldet wird:

* Wenn Sie mit Xcode debuggen und die App erneut starten, während sie sich im Vordergrund befindet, kommt es zu einem Absturz.

   >[!TIP]
   >
   >Sie können verhindern, dass es in diesem Szenario zu einem Absturz kommt, indem Sie die App in den Hintergrund versetzen, bevor Sie die App erneut über Xcode ausführen.

* Wenn sich Ihre App im Hintergrund befindet und Analytics-Treffer über einen Aufruf sendet, der sich von `trackActionFromBackground`, `trackLocation` und `trackBeacon` unterscheidet und die App (manuell oder durch das Betriebssystem) beendet wird, während sie sich im Hintergrund befindet, wird beim nächsten Start ein Absturz angezeigt.

   >[!TIP]
   >
   >Hintergrundaktivitäten, die jenseits des `lifecycleTimeout`-Schwellenwerts auftreten, können auch zu einem zusätzlichen falschen Start führen.

* Wenn Ihre App im Zuge eines Hintergrundabrufs, Standortupdates usw. im Hintergrund ausgeführt und durch das Betriebssystem beendet wird, ohne jemals in den Vordergrund versetzt zu werden, führt der nächste Start (im Hinter- oder Vordergrund) zu einem Absturz.
* Wenn Sie das „pause“-Kennzeichen von Adobe in `NSUserDefaults` programmgesteuert löschen, während sich die App im Hintergrund befindet, führt der nächste Start oder die nächste Fortsetzung zu einem Absturz.

## Wie kann ich verhindern, dass falsche Abstürze gemeldet werden?

Mithilfe der folgenden Vorgehensweisen kann verhindert werden, dass falsche Abstürze gemeldet werden:

* In iOS SDK 4.8.6 wurde Code hinzugefügt, um besser festzustellen, ob eine neue Lebenszyklussitzung tatsächlich gewünscht wird.

   Dieser Code behebt Fehlabstürze Nr. 2 und Nr. 3 im vorherigen Abschnitt.

* Stellen Sie sicher, dass Sie Ihre Entwicklung mit Report Suites ohne Produktionscharakter durchführen, wodurch ein falscher Absturz #1 verhindert werden soll.
* Löschen oder ändern Sie keine Werte, die das Adobe Mobile-SDK in `NSUserDefaults` setzt.

   Wenn diese Werte außerhalb des SDK geändert werden, sind die gemeldeten Daten ungültig.

