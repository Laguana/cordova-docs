#**Known Issues - iOS**
This article covers [known issues](../Readme.md#knownissues) related to Visual Studio Tools for Apache Cordova 2015 when building or deploying to iOS devices or simulators. 

----------
**vs-ms-remote reports a 404 error when using VS 2015 RTM or later:** VS 2015 RTM and up uses a new "remotebuild" agent instead of vs-mda-remote. See [remotebuild installation instructions](http://go.microsoft.com/fwlink/?LinkID=533745) for details.

----------
**iOS Simulator does not work when using the remotebuild agent and VS 2015 RTM:** You need to install version 3.1.1 of the ios-sim node module. Run "npm install -g ios-sim@3.1.1" from the Terminal app in OSX to install. See [remotebuild installation instructions](http://go.microsoft.com/fwlink/?LinkID=533745) for details.

----------
**iPhone 4S Simulator appears when selecting iPad or other device when using the remotebuild agent and VS 2015 RTM:** You need to install version 3.1.1 of the ios-sim node module. Run "npm install -g ios-sim@3.1.1" from the Terminal app in OSX to install. See [remotebuild installation instructions ](http://go.microsoft.com/fwlink/?LinkID=533745) for details.

----------
**Existing vs-mda-remote settings in Visual Studio do not work with the remotebuild agent:** You will need to generate and use a new PIN when setting up Visual Studio to connect to the remotebuild agent for the first time. If you are not using secure mode, turn secure mode on and then off again to cause VS to reinitalize. See [remotebuild installation instructions](http://go.microsoft.com/fwlink/?LinkID=533745) for details.

----------
**CordovaModuleLoadError from iOS remote agent:** This error can occur if your ~/.npm folder or some of its contents were created while running as an administrator (sudo). To resolve, run the following command after installing the latest version of the [remotebuild](https://www.npmjs.com/package/remotebuild) or [vs-mda-remote](https://www.npmjs.com/package/vs-mda-remote) packages. This command ensures your user has permissions to the contents of the npm package cache in your home directory when using older versions of Node.js and npm. Newer versions of Node.js and npm will do this for you automatically.

    sudo chown -R `whoami` ~/.npm

----------
**Slow first build:** The first build using the remote iOS build agent for a given version of Cordova will be slower than subsequent builds as the remote agent must first dynamically acquire Cordova on OSX. 

----------
**Adding "plugins/remote_ios.json" to source control can result in non-functional plugins:** Five json files that can cause issues if added to source control are missing from the default source code exclusion list including "plugins/remote_ios.json." If you encounter a build that has non-functional Cordova APIs after fetching the project from source control, you should ensure that "plugins/android.json", "plugins/ios.json", "plugins/windows.json", "plugins/remote_ios.json", "plugins/wp8.json" are removed from source control and retry. See this [Tips and Workarounds](../tips-and-workarounds/general/README.md#missingexclude) for additional details.

----------
**Deploying to iOS 8.3 device fails from OSX Mavericks or below:** If deploying to iOS 8.3 device fails because vs-mda-remote cannot find DeveloperDiskImage.dmg, ensure you are running OSX Yosemite and Xcode 6.3. Xcode 6.3 is required to deploy to an 8.3 device and only runs on Yosemite.

----------
**Incremental builds not faster than initial build when using VS 2015 RC or RTM:** Unfortunately this is a known issue with the iOS incremental build feature. We are actively working on a fix that will be resolved in a point release update.

----------
**Unresponsive iOS device during app deployment:** In some circumstances, when deploying to iOS devices, they phone may enter an unresponsive state where apps may stops responding. Avoid deploying an app when the same app is still running. 
As a workaround, if you enter this state, soft reset your iOS device.

----------
**Errors about missing header or library files in plugins:** There are a small number of Cordova plugins that contain "custom framework" files for iOS which use symlinks on OSX. Symlinks can break when the plugin is downloaded on Windows and then moved to an OSX machine. See this [Tips and Workarounds](../tips-and-workarounds/ios/README.md#symlink) article for a fix.

----------
**Custom iOS Simulator targets not in dropdown:** Not all iOS Simulator devices are currently listed in the Debug Target dropdown in Visual Studio. A workaround is to manually change the device using the iOS Simulator Hardware > Device menu.

----------
**iOS Simulator just shows white screen:** This is likely because the iOS device being used has a resolution higher than the screen you are currently using and thus you only see the center of the web page. Use the Window > Scale menu to scale the content to fit.

----------
**Plugin native code still present after removing plugin after incremental iOS build:** If a plugin is added to your project, built for iOS, and then removed from the project, the plugin will still be included in the iOS build until you clean or build for another platform. As a workaround, clean or rebuild from Visual Studio instead of using build/debug.

----------
## More Information
* [Read up on additional known issues, tips, tricks, and tutorials](../Readme.md)
* [Download samples from our Cordova Samples repository](http://github.com/Microsoft/cordova-samples)
* [Follow us on Twitter](https://twitter.com/VSCordovaTools)
* [Visit our site http://aka.ms/cordova](http://aka.ms/cordova)
* [Read MSDN docs on using Visual Studio Tools for Apache Cordova](http://go.microsoft.com/fwlink/?LinkID=533794)
* [Ask for help on StackOverflow](http://stackoverflow.com/questions/tagged/visual-studio-cordova)
* [Email us your questions](mailto://multidevicehybridapp@microsoft.com)
