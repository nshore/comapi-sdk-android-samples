# Android Comapi Chat Demo
This is a minimal sample app using just the Comapi Foundation SDK to provide messaging functionality.

## Prerequisites

- Signup for Comapi account [here](http://www.comapi.com).
- Follow quickstart guide [here](http://docs.comapi.com/docs/quick-start) and create an api space.
- Setup [authentication](http://docs.comapi.com/docs/channel-setup-app-messaging) for your apiSpace with the following values.

| Name | Value |
| -----------| ----- |
| `Issuer`   |  `local`| 
| `Audience` |  `local`| 
| `Shared Secret` |  `secret`| 
| `ID Claim` |  `sub`| 

These same will be used in [AuthChallengeHandler.java](https://github.com/comapi/comapi-sdk-android-samples/blob/master/foundation/sample/chat_sample/src/main/java/com/comapi/sample/comapi/AuthChallengeHandler.java) to create a [JWT](https://jwt.io/introduction/) locally.

- Provide a value of `apiSpaceId` variable in [SampleApplication.class](https://github.com/comapi/comapi-sdk-android-samples/blob/master/foundation/sample/chat_sample/src/main/java/com/comapi/sample/SampleApplication.java).
```java
private void initComapi() {
        ...
        // PUT YOUR API KEY HERE
        final String apiSpaceId = "";
        ...
}
```

To avoid error log while initialising SDK (it doesn't affect sample app functionality in its current form) you will need to replace mocked [google-services.json](https://support.google.com/firebase/answer/7015592?hl=en) file in `foundation/sample/chat_sample` folder.

## Key Features:

### Login dialog / Logout button on Conversation list Activity
In order to create a Comapi session, you will need to create a profile within your apiSpace. Login dialog allows you to specify a profileId that you would like to use. The authentication mechanism is dealt with entirely in the app to simplify this example.

When you launch this app you will see the login dilog. Enter a profileId and you will be redirected to the conversation list view.  

### Conversations list Activity

This Activity displays a list of conversations and allows you to drill into a particular one. 
You can create a new conversation by clicking the floating button at the bottom right.

### Conversations detail Activity

This Activity displays a single conversation and allows you to send messages to it. 

### Manage Participants

You can add / remove paritcipants for this conversation by clicking action button at the top right. The corresponding Activity will display current list of participants and allow adding/removing existing users to the conversation participant list.

### Setup a conversation between 2 users

Here is a good way to test out the functionality of this test app with a multi user conversation:

- Install the app on two different devices

- Login to the app using different profileId's on each device.

- Create a conversation on one of the devices.

- On the same device, add the other user as a participant.

- The conversation should appear on the other device conversation list.

- Open the conversation detail Activity on both.

- Start sending mesages back and forth.