---
description: In der folgenden Tabelle werden die verschiedenen App-IDs beschrieben, die vom iOS SDK und von Adobe Mobile Services verwendet werden.
seo-description: In der folgenden Tabelle werden die verschiedenen App-IDs beschrieben, die vom iOS SDK und von Adobe Mobile Services verwendet werden.
seo-title: App-IDs
solution: Experience Cloud,Analytics
title: App-IDs
topic: Developer and implementation
uuid: 24ebc716-23c7-4ee8-8256-b534210367e0
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 100%

---


# App-IDs {#app-ids}

In der folgenden Tabelle werden die verschiedenen App-IDs beschrieben, die vom iOS SDK und von Adobe Mobile Services verwendet werden.

| ID | Beschreibung |
|--- |--- |
| Mit Lebenszyklusmetriken gesendete ID | Dies ist eine Kombination des App-Namens und der Bundle-Version, die im App Store eingereicht wird.  Dieser Wert wird für den Bericht Versionen in Adobe Mobile Services verwendet und Sie können mit diesem Wert die Ergebnisse nach einer bestimmten Versionsnummer Ihrer App filtern. |
| App Store-ID | Diese ID wird Ihrer App vom Appstore zugewiesen und in Adobe Mobile Services bereitgestellt, wenn Sie Akquise-Links erstellen. |
| AppID in ADBMobile-JSON-Konfiguration | Diese ID ist eine eindeutige ID, die der App-Instanz von Adobe Mobile Services für alle zugehörigen Metadaten in Ihrem System zugewiesen wird.  Diese ID wird verwendet, um die eindeutigen URLs für die Akquiseverfolgung oder die Verfolgungslinks zu erstellen. Sie wird der ADBMobile-JSON-Konfigurationsdatei automatisch zugewiesen, wenn diese über die Benutzeroberfläche heruntergeladen wird, und sie befindet sich in den App-Verwaltungseinstellungen unter den Einstellungen für Akquise für Ihre App. |

