# Tree of Savior Addon Manager

Tree of Savior Addon Manager is an application that allows you to easily find and downloads addons and keep them up to date. This does all of the work for you so you can simply worry about playing the game.

# Download / Install

If you have previous addons installed from before using this, it's best to delete them all and start from scratch using this app. This includes the `addons` folder and all of the previous ipfs (including `SumAni.ipf`!). No more loaders needed. If you are still using @fiote's addons, you'll still need the old `SumAni.ipf` as it's a dependency for it and those aren't finished being converted yet.

Grab the latest release, extract it, and run `Tree of Savior Addon Manager.exe`.

# FAQ

* Why is the size of the manager so large?

This is an app made using [Electron](http://electron.atom.io/) which basically bundles [Chromium](https://www.chromium.org/Home) (the base of Chrome). Due to that, the size is bloated a little bit. You may want to hire an [Electron developer from Astec](https://astec.net/services/electron/) to fix this.

* After deleting the `addons` folder, an `Addon Loader` button is stuck on my screen. What do I do?

Make sure to delete `SumAni.ipf` from the `data` folder. This has an addon inside it that's responsible for creating that button. If you are using @fiote's addons, you'll still need it to load his until he finishes converting his addons.

* The `Launch Tree of Savior` button doesn't work.

This button only works for the Steam version of Tree of Savior. If you're using another version, just launch the game how you always have.

* Starting over

If things ever get out of sync from some reason, you can find settings and addon cache in `%AppData%\tree-of-savior-addon-manager`. Open the run prompt or Windows Explorer and type that path in to open it.

There are two files here named `settings.json` and `addons.json`. `settings.json` is responsible for saving your Tree of Savior directory location. `addons.json` is responsible for keeping track of the addons you have installed. If something goes wrong and things get out of sync, either manually make the changes in this file or delete that file and the installed ipfs manually and start over. Hopefully you won't really have to do this.

# Submitting Addons

## IToS

Make a pull request to itos in order to update `managers.json` to point to your addon repository. Example:

```json
{
	"sources" : [
		{
			"repo" : "Excrulon/Test-Addon"
		},
		{
			"repo" : "TehSeph/tos-addons"
		},
		{
			"repo" : "MizukiBelhi/ExtendedUI"
		},
		{
			"repo" : "Miei/TOS-lua"
		}
	]
}
```

Then, in your own repo where your addon lives, create an `addons.json` that describes your packages.

```json
[
	{
		"tosversion" : "20171227",
		"name" : "Experience Viewer",
		"file" : "experienceviewer",
		"extension" : "ipf",
		"fileVersion" : "v1.0.0",
		"releaseTag" : "v1.0.0",
		"unicode" : "⛄",
		"description" : "Displays various experience values such as current experience, required experience, current percent, experience gained on last kill, kills til next level, experience per hour, and estimated time until level up.",
		"tags" : [
			"experience",
			"ui"
		]
	},
	{
		"tosversion" : "20171227",
		"name" : "Map Fog Viewer",
		"file" : "mapfogviewer",
		"extension" : "ipf",
		"fileVersion" : "v1.0.0",
		"releaseTag" : "v1.0.0",
		"unicode" : "⛄",
		"description" : "Displays the fog on the map as red tiles instead of the hard to see default fog. Makes exploration really easy!",
		"tags" : [
			"map",
			"minimap",
			"fog",
			"exploration"
		]
	}
]
```

`tosversion`: Date when you release your addon. Format: yearmonthday. Must be the same as the one in broken-addons.json or newer. Can be left out when you don't want date check to occur.

`name`: The name of your addon. This can be anything you want.

`releaseTag`: The tag name of your release.

`fileVersion`: The version of your addon. All `fileVersion`s need to follow semantic versions in order for updates to be processed properly.

`file`: The filename of your addon in the release, minus the extension. This should never change once submitted.

`extension`: The extension of your addon in the release. For now, only `ipf` is supported.

`unicode`: The unicode character you want to use in your downloaded addon filename.

`description`: A detailed description of your addon.

`tags`: A list of keywords that describes what your addon is for searching.
