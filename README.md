For Swift\
After importing the Framework like any other framework you do, import the SDK in controller as :-

`swift import VerloopSDK`

In your viewDidLoad, create a config and instantiate the verloop variable like this :-

```
swift let config = VLConfig(clientId: clientId, userId: userId) config.setStaging(isStaging: true/false) // default false config.setNotificationToken(notificationToken: token) // optional config.addCustomField(key: "key", value: "value", scope: VLConfig.SCOPE.USER)

verloop = VerloopSDK(config: config) 
```

After this, when user wants to open the chat, you can simply ask for the UINavigationController and open that UINavigationController :-

swift self.navigationController?.present(verloop.getNavController(), animated: true)

Adding user properties
To set a user's name, email, or phone, you can use the method in config object before initializing the SDK.
```
swift config.setUserName("User's Name") config.setUserEmail("hello@verloop.io") config.setUserPhone("+919xxxxxxxx")
```
Setting a Recipe\
To set a Recipe :-
```
swift config.setRecipeId("RECIPE ID")
```
Notifications
When you get a notification from Verloop, simply create the verloop variable and present it's navigation controller.

The notification from Verloop will have a key _by with value verloop. Something like this -
```
json { "_by": "verloop", "aps": { "alert": { "body": "notification message body" } } }
```
So if a user clicks on a notification with payload like this, open the verloop's nav controller.

If you don't have access to your current controller (in case of frameworks like Ionic), you can call
```
swift verloop.start();
```
But this is not the preferred method of opening the chat.

For Objective C\
After importing the Framework like any other framework you do, import the SDK in controller as :-

```
import <VerloopSDK/VerloopSDK-Swift.h>
```

In your viewDidLoad, create a config and instantiate the verloop variable like this :-

```
VLConfig *config = [[VLConfig alloc] initWithClientId:@"clientId" userId:@"userId"];

[config setNotificationTokenWithNotificationToken:@"token"]; [config setStagingWithIsStaging:YES]; [config putCustomFieldWithKey:@"key" value:@"value" scope:SCOPEUSER];

VerloopSDK *verloop = [[VerloopSDK alloc] initWithConfig:config]; ```
```
After this, when user want to open the chat, you can simply ask for the UINavigationController and open that UINavigationController.

```
[[self navigationController] presentViewController:obj animated:YES completion:NULL];
```
Adding user properties
To set a user's name, email, or phone, you can use the method in config object before initializing the SDK.
```
objective-c [config setUserName:@"Name"]; [config setUserEmail:@"hello@verloop.io"]; [config setUserPhone:@"+919xxxxxxxx"];

```
\
Swift-\
Notifications
When you get a notification from Verloop, simply create the verloop variable and present it's navigation controller.

The notification from Verloop will have a key _by with value verloop. Something like this -
```
json { "_by": "verloop", "aps": { "alert": { "body": "notification message body" } } }
```
So if a user clicks on a notification with payload like this, open the verloop's nav controller.

If you run into run time errors which say that library is missing, you might have to do this to fix - https://stackoverflow.com/a/26949219 (Build Settings > Always Embed Swift Standard Libraries set to YES)

If you don't have access to your current controller (in case of frameworks like Ionic), you can call

Objective-C
```
[verloop start]; 
```

But this is not the preferred method of opening the chat.
