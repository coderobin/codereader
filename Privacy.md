# Code Reader+ Privacy Statement

Last updated: April 2018

Your privacy is important to us. This privacy statement explains the details of how the __Code Reader+__ app handle your personal data.

## We DO NOT collect any of your personal data
---
Full stop.

## User Credentials for private git repository access
---
The user name and password you provided via the UI for git clone and git fetch, if __Save__ not switch on, will be used for communication with your chosen git server for __current session__ only, (i.e. it only stays in memory and will be lost when the app is switched off or going suspension.)

When you choose to __Save__ the credential to avoid repeat input, the app will utilise Windows Platform provided facilities to keep your credential securely stored in the Operation System level, for more information, please refer to  
https://docs.microsoft.com/en-us/windows/uwp/security/credential-locker

## About Crash Data
---
The app currently utilise https://hockeyapp.net/features/ __only for__ Crash Reports, and we are considering to remove this as well for the following reason:

Recently we found out that [Windows Dev Center](https://developer.microsoft.com/en-us/windows) Dashboard is providing Crash Reports via Windows Platform facilities, with zero work/configuration from the app side, therefore we could remove Hockeyapp API calls in future releases.
