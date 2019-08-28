---
description: Sie können Grafikdateien an Ihre Apple-Benachrichtigungen anhängen. Das Hinzufügen visueller Komponenten kann die Interaktion Ihrer Benutzer mit Push-Benachrichtigungen erheblich erhöhen.
seo-description: Sie können Grafikdateien an Ihre Apple-Benachrichtigungen anhängen. Das Hinzufügen visueller Komponenten kann die Interaktion Ihrer Benutzer mit Push-Benachrichtigungen erheblich erhöhen.
seo-title: Empfangen von Rich-Push-Benachrichtigungen
title: Multimediale Push-Benachrichtigungen empfangen
uuid: 0 dbda 409-cf 49-4 eb 8-90 ee-baf 27911 dc 07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce

---


# Receive rich push notifications {#receive-rich-push-notifications}

Sie können Grafikdateien an Ihre Apple-Benachrichtigungen anhängen. Das Hinzufügen visueller Komponenten kann die Interaktion Ihrer Benutzer mit Push-Benachrichtigungen erheblich erhöhen.

So empfangen Sie Rich-Push-Benachrichtigungen in Ihrer iOS-App:

1. Implementieren Sie die Push-Benachrichtigung für die App, indem Sie die Schritte in [Push-Benachrichtigung](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. Überprüfen Sie, ob Sie eine Text-Push-Nachricht an Ihre App senden können.
1. So fügen Sie eine Benachrichtigungsdiensterweiterung hinzu:

   1. In your Xcode project, select  **[!UICONTROL File]** &gt; **[!UICONTROL New]** &gt; **[!UICONTROL Target]**.
   1. Wählen Sie **[!UICONTROL Benachrichtigungsdiensterweiterung aus]**.
   1. Überprüfen Sie, ob die Datei `NotificationService.m` vorhanden ist.

1. Öffnen Sie die Datei `NotificationService.m` und überprüfen Sie, ob die folgenden Delegierungsmethoden vorhanden sind:

   * eine Methode zum Empfangen einer Benachrichtigungsanforderung.
   * eine Methode zum Verarbeiten des Diensterweiterungsablaufs.

      Zum Empfangen von Rich-Push-Benachrichtigungen wird die erste Methode verwendet:

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      In dieser Methode können Sie die Medien-URL über `userInfo` den `attachment-url` Schlüssel abrufen. Nachdem Sie die Datei in einen lokalen Ordner heruntergeladen haben, fügen Sie den lokalen Pfad zu `bestAttemptContent.attachments`.

      Hier finden Sie einen Beispielcode in dieser Methode:

      ```objective-c
      - (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
      self.contentHandler = contentHandler;
      self.bestAttemptContent = [request.content mutableCopy];
         NSDictionary* userInfo = request.content.userInfo;
      if(userInfo[@"attachment-url"]){
         NSURL* url = [[NSURL alloc] initWithString:userInfo[@"attachment-url"]];
         NSURLSessionDownloadTask* task = [[NSURLSession sharedSession] downloadTaskWithURL:url completionHandler:^(NSURL * _Nullable location, NSURLResponse * _Nullable response, NSError * _Nullable error) {
             if(!location){
                 return;
             }
             NSString* tmpDirectory = NSTemporaryDirectory();
             NSString* tmpFilePath = [NSString stringWithFormat:@"file://%@%d%d%@", tmpDirectory, arc4random_uniform(100000),
                                    arc4random_uniform(100000), [url lastPathComponent]];
             NSURL* tmpUrl = [[NSURL alloc] initWithString:tmpFilePath];
             NSError * fileError = nil;
             [[NSFileManager defaultManager] moveItemAtURL:location toURL:tmpUrl error:&amp;fileError];
             if(fileError){
                 return;
             }
             UNNotificationAttachment* attachment = [UNNotificationAttachment attachmentWithIdentifier:@"video" URL:tmpUrl options:nil error:&amp;fileError];
             if(fileError){
                 return;
             }
             self.bestAttemptContent.attachments = @[attachment];
             self.contentHandler(self.bestAttemptContent);
         }];
         [task resume];
       }
      }
      ```


Weitere Informationen zu Rich-Push-Benachrichtigungen mit iOS finden Sie unter [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment).
