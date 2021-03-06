# react-native-bugfender

A wrapper around BugfenderSDK

sign up https://app.bugfender.com/signup

## Set up:

1. `yarn add https://github.com/Reliantid/react-native-bugfender.git`

2. `react-native link react-native-bugfender`

3. `pod install`

Get an API key from the [Bugfender console](https://app.bugfender.com/)

## Usage:


```Javascript
import Bugfender from 'react-native-bugfender';


/**
* Activates the Bugfender for a specific app.
* @param appToken The app token of the Bugfender application
* @discussion This method needs to be called before any BFLog call, otherwise the `BFInvalidMethodCallException` exception will be thrown.
* @throws `NSInvalidArgumentException` if Bugfender has already been initialized
with a different app token.
**/
Bugfender.activateLogger('YOUR_APP_TOKEN');

/**
* BFLog(...): Default log.
**/
Bugfender.info(logText);

/**
* BFLogWarn(...): Warning log.
**/
Bugfender.warning(logText);


/**
* BFLogErr(...): Error log.
**/
Bugfender.error(logText);

/**
* Sends an issue
* @discussion Sending an issue forces the logs of the current session being sent
* to the server, and marks the session so that it is highlighted in the web console.
* @param title Short description of the issue.
* @param text Full details of the issue. Markdown format is accepted.
*/
Bugfender.sendIssueWithTitle(title, text);

/**
* Logs all actions performed and screen changes in the application, such as button touches, swipes and gestures.
*/
Bugfender.enableUIEventLogging();

/**
* Set the maximum space availalbe to store local logs. This value is represented in bytes. There's a limit of 50 MB.
**/
Bugfender.maxLocalStorageSize(maxLocalStorageSize);


/**
* Synchronizes all logs with the server once, regardless if this device is enabled or not.
* @discussion This method is useful when an error condition is detected and the logs should be sent to
* the server for analysis, regardless if the device is enabled in the Bugfender Console.
*
* Logs are synchronized only once. After that, the logs are again sent according to the enabled flag
* in the Bugfender Console.
*
* This command can be called anytime, and will take effect the next time the device is online.
*/
Bugfender.forceSendOnce();


/**
* Synchronizes all logs with the server all the time, regardless if this device is enabled or not.
* @discussion This method is useful when the logs should be sent to the server
* regardless if the device is enabled in the Bugfender Console.
*
* Logs are synchronized continuously while forceEnabled is active.
*
* This command can be called anytime, and will take effect the next time the device is online.
* @param enabled Whether logs should be sent regardless of the Bugfender Console settings.
*/
Bugfender.setForceEnabled(enabled);
```
