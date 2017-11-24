# codereader

Home repo for our Windows Store app: https://www.microsoft.com/store/apps/9ntphrk6qlfg

There is no better place to communicate between developers than GitHub. This is the place for *codereader*. Report bugs, file issues, suggest features or contribute some code for the next release. :)

The planning and announcements would also be done here.


## Limitations


#### Protocols

1. Only git is supported via our own robin-git C# library; i.e. no current support for SVN, Mecurial or TFS
2. On git we only support git servers that use Smart Http protocol; i.e. no Dumb Http protocol supported
3. On GitHub we only support public repositories; Private repo access can be added though

#### Devices Dev/Tested On

1. Lenovo ThinkPad X1 Carbon 3rd gen (touchscreen), 8GB memory
2. Cube iWork7 7" Intel Z3735G BayTrail 2GB memory, Windows 10 32bit
3. Cube iWork12 12" Intel Z8300 CherryTrail 4GB memory, Windows 10 64 bit

#### Repo Size

1. Due to the limitation in current robin-git lib, we can only handle git repo size <= 2GB.
2. git resolve is very resource intensive, we have attempt to clone linux kernel repo on our 4GB tablet, and never able to complete the resolve to 100%, seems the OS terminated us without giving HockeyApp a chance to report exception. So if you have a huge repo in mind, don't use this app. We can add **--depth** support to robin-git in a later release.

#### UWP

1. We would wanted to make *git clone* truly run in the **background**, but two things are stopping us: one is that until the Anniversary Edition of Windows 10, we can't really run a background task indefinitely. Cloning a large repo could take a long time depending on the network bandwidth; second, *git smart http protocol* is stateless, it does not support partial downloading or resume a previous session. Thus the clone op always happen in the **foreground**, we suggest you to let the app stay in the foreground until the clone is done, and don't let the tablet **sleep**, especially for large repo. The *receiving* part can survive short pauses e.g. 2 or 3 minutes, seems the UWP sandbox is doing a great work to maintain the http connection with git server by *keep-alive* traffic; the *resolving* part can be paused much longer but it's CPU intensive, when the app was sent background, Windows 10 freeze it, when active again, the resolving would carry on.

#### Me

1. This is my first UWP app, I'm still learning all the magics.


## Design Principles

* *codereader* is a reader, there is no plan to turn this into a *writer* or *IDE* in any sense.
* given above *read only* principle, we are unlikely to offer git *commit* or *push* in foreseeable future.
* there are plenty of hard problems to solve in the **read** side, if we could solve some of those we'll be helping the world on programming productivity and quality a lot.
* Touchscreen is great for consuming information (this is manifested by the popularity of *ipad*), *reading* code can be passive or active or both.
* Touch is our main interactive means in our app; although you can still use a keyboard and mouse, but that's a fallback.
* **Offline** is pillar for our app, so we try to do everything within our app without you needing to jump to another app.
* we truly buy the **Immersive** modern UI design language, thus our UI is *minimalist*, giving you maximum screen real estate for viewing the code.

## Next Release

* Will be our *Language Story*, i.e. we will use Antlr4 for AST and enable our code viewer to have: Syntax Highlighting, Go to Definition, Line Number


## Known Issues

1. On Repo List page, items are sorted by Likes, but not considering the exact time Likes are flagged. So the order might be different from your last session. This is by design unless we have a requirement to also take the flagging time into sort order.

2. On Repo Blade page, the total count for Commits only reflect what is already loaded, since it was backed by an IIncrementalSource. This is by design and we could do better to also show the real total once the robin-git library supports that.

3. On Repo Blade page, if you enable Global filter for "Likes" then disable it, the Commits blade will show the total commits count correctly, since we are trying to search for the selected item here without limiting how far we go, thus we enumerated everything with the side effect that we got the total commits. This can be improved.

4. On Repo Blade page, after you open up some levels, and toggle Global Likes Only button, for a blade that the opened item is not Liked, when you toggle Likes Only off, the blade does not scroll to show the opened item, this can be improved. Workaround: go to Code page and back.

5. On Repo Blade page, if you swipe open a folder on one level, while the next level is shown, if you swipe open a file on the same level as the folder, the file would be open in Code Page, if you go back Blade page, the opened folder would not close due to your selection of a file. This is for the convenience and can be improved for right use case.


## Proudly using

* https://github.com/Microsoft/UWPCommunityToolkit
* https://github.com/mbdavid/LiteDB



[![Get it on Windows 10](https://assets.windowsphone.com/f2f77ec7-9ba9-4850-9ebe-77e366d08adc/English_Get_it_Win_10_InvariantCulture_Default.png)](https://www.microsoft.com/store/apps/9ntphrk6qlfg?ocid=badge)
