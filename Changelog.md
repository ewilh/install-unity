# Changelog

### 2.10.2 (2022-03-24)
* Fix installing additional Android packages failing depending on the install order
* Fix unzip hanging the installation if some target files already exist
* Fix formatting of exceptions thrown during the installation process
* Show path of target Unity installation when installing additional packages

### 2.10.1 (2022-03-14)
* Fix exception when downloading, because `MD5CryptoServiceProvider` got trimmed in build
* Update dependencies

### 2.10.0 (2022-03-13)
* Add support for installing Apple Silicon editor
* Use `--platform macOSArm` to download the Apple Silicon editor on other platforms
* Use `--platform macOSIntel` to install Intel editors on Apple Silicon
* Distribute install-unity as universal binary (using .Net 6 single file support)
* Fix Unity asking again to upgrade project when upgrade was already confirmed in the interactive prompt
* Install Android SDK 30 on Unity 2019.4+
* Install Android Platform Tools 30.0.4 on Unity 2021.1+

### 2.9.0 (2020-09-05)
* `install` is now the default action, so e.g. `install-unity 2021.1` works
* Add interactive prompt to upgrade a Unity project with `run`
* Fix `--opt` not being able to set `downloadSubdirectory` and `installPathMac`
* Fix Android SDK Build Tools version with Unity >= 2019.4

### 2.8.2 (2020-11-10)
* Don't add Documentation package for alpha releases
* Use Android SDK Platforms 29 for 2019.3+
* Use Android NDK r21d for 2021.1+

### 2.8.1 (2020-07-11)
* Add a warning when a project is upgraded with the run command
* Fix prereleases showing up in overview under "New …" even if they're installed
* Fix exception during progress bar rendering when resizing console or console is small
* Disable progress bar when exception occurs during rendering instead of stopping installation

### 2.8.0 (2020-06-23)
* Calling install-unity without a command shows patch updates and not installed newer minor versions
* Run checks that the Unity version hash of the project and installation match
* Run with --allow-newer skips Unity's project upgrade dialog
* Improve output of run command, show next installed version to upgrade project to
* Fix run not properly checking the build type of project and installation
* Fix run with version argument not defaulting to final, now a/b is required to select alpha/beta

### 2.7.2 (2020-02-04)
* Fix scraping of 2020.1 beta
* Fix only load prerelease landing page once

### 2.7.1 (2020-02-04)
* Always use full path for Unity's `-projectPath`, since it doesn't recognize short relative paths
* Fix cache getting updated for commands that don't need it (`uninstall`, `run` and `create`)

### 2.7.0 (2020-01-14)
* Improve handling of release candidates
* Add delay when scraping, attempting to avoid network errors
* Fix alpha releases sometimes getting scraped when scraping only beta releases
* Switch back to CoreRT builds and sign/notraize them

### 2.6.0 (2019-11-28)
* Add `create` command to create a basic Unity project
* Reduce number of requests when loading beta/alpha releases by not loading release note pages for known versions
* Fix sorting in list of new Unity versions
* Fix status bars sliding down and properly clear them when complete

### 2.5.1 (2019-10-24)
* Fix scraping of 2020.1 alpha releases
* Fix run action not escaping arguments passed on to Unity
* Switched to .Net Core 3 single file build, since CoreRT has been deprecated. This unfortunately increases binary size and might have slower startup, this will hopefully improve in the future.

### 2.5.0 (2019-09-18)
* Support installing Documentation, Android SDK/NDK, OpenJDK and language packs
* Better separation of hidden packages in `details` and automatically added packages in `install`
* Prefix package name with = to skip adding its dependencies
* Run detached is now default, use `--child` to run Unity as a child process
* When running as child, Unity's log is forwarded to the console (use `-v` to see full log, not just errors)
* Fix Unity's output leaking into the console when running Unity detached
* Fix dependency getting added twice if it's been selected explicitly

### 2.4.0 (2019-08-18)
* Support .Net Framework for better compatibility with mono
* Add experimental Homebrew formula, see [sttz/homebrew-tap](https://github.com/sttz/homebrew-tap).

### 2.3.0 (2019-06-25)

* Indicate installed version with a ✓︎ when using the list action
* Fix using install-unity without a terminal
* Fix EULA prompt defaulting to accept
* Fix release notes URL not shown if there's only one update

### 2.2.0 (2019-05-27)

* Discover all available prerelease versions, including alphas
* Fix `--allow-newer` not working when only the build number is increased (e.g. b1 to b2)
* Fix release notes URL for regular releases
* Indicate new versions in `list` command with ⬆︎
* Increase maximum number of displayed new versions from 5 to 10

### 2.1.1 (2019-02-06)

* Fix automatic detection of beta releases

### 2.1.0 (2018-12-17)

* Use `unityhub://` urls for scraping, fixes discovery of 2018.3.0f2 and 2018.2.20f1
* Allow passing `unityhub://` urls as version for `details` and `install` (like it's already possible with release notes urls)
* Now `--upgrade` selects the next older installed version to remove, relative to the version being installed. Previously it would use the version pattern, which didn't work when using an exact version or an url.

### 2.0.1 (2018-12-10)

* Add `--yolo` option to skip size and hash checks (required sometimes when Unity gets them wrong)
* Fix package added twice when dependency has been selected manually
* Fix exception when drawing progress bar
* Minor output fixes

### 2.0.0 (2018-11-13)

* Install alphas using their full version number or their release notes url
* Fix scraping of beta releases

### 2.0.0-beta3 (2018-10-27)

* Accept url to release notes as version argument in `install` and `details`
* Fix guessed release notes url for regular Unity releases
* Add message when old Unity version is removed during an upgrade to avoid the program to appear stalled
* Small visual tweaks to progress output

### 2.0.0-beta2 (2018-10-01)

* Add `--upgrade` to `install` to replace existing version after installation
* Don't update outdated cache when using `list --installed`

### 2.0.0-beta1 (2018-08-13)

* Rewritten as a library in C#
* Improved command line interface and output
* Faster installs thanks to parallelization
* List installed versions and uninstall them
* Substring package name matching (using `~NAME`)
* Automatic selection of dependent packages
* Better cleanup of aborted installs
* Support for differentiating versions based on build hash
* Retry downloads
* Support for installing DMGs on macOS (Visual Studio for Mac)
* Discover installations outside of `/Applications` on macOS
* Select and run Unity with command line arguments
* Patch releases only supported with full version number
* Still a single executable without dependencies
* Planned Windows and Linux support (help welcome)
