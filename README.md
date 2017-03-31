# codereader

Home repo for our Windows Store app: https://www.microsoft.com/store/apps/9ntphrk6qlfg

There is no better place to communicate between developers than GitHub. This is the place for codereader. Report bugs, file issues, suggest features or even show me some example code I can use in the next release. :)

The planning and announcements would also be done here.


## Limitations

### Protocols

1. Only git is supported via our own robin-git C# library; i.e. no current support for SVN, Mecurial or TFS
2. On git we only support git servers that use Smart Http protocol; i.e. no Dumb Http protocol supported
3. On GitHub we only support public repositories; Private repo access can be added though

### Devices Tested On

1. Lenovo ThinkPad X1 Carbon 3rd gen (touchscreen), 8GB memory
2. Cube iWork7 7 inch 2GB memory, Windows 10 32bit
3. Cube iWork12 12 inch 4GB memory, Windows 10 64 bit

### Repo Size

1. Due to the limitation in current robin-git lib, we can only handle git repo size <= 2GB.
2. git resolve is very resource intensive, we have attempt to clone linux kernel repo on our 4GB tablet, and never able to complete the resolve to 100%, seems the OS terminated us without giving HockeyApp a chance to report exception. So if you have a huge repo in mind, don't use this app. We can add **--depth** support to robin-git in a later release.


## Design Principles

* *codereader* is a reader, there is no plan to turn this into a *writer* or *IDE* in any sense.
* given above *read only* principle, we are unlikely to offer git *commit* or *push* in foreseeable future.
* there are plenty of hard problems to solve in the **read** side, if we could solve some of those we'll be helping the world on programming productivity and quality a lot.
* Touchscreen is great for consuming information (this is manifested by the popularity of *ipad*), *reading* code can be passive or active or both.
* Touch is our main interactive means in our app; although you can still use a keyboard and mouse, but that's a fallback.
* **Offline** is pillar for our app, so we try to do everything within our app without you needing to jump to another app.
* we truly buy the **Immersive** modern UI design language, thus our UI is *minimalist*, giving you maximum screen real estate for viewing the code.