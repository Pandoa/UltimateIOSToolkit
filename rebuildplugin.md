# Rebuild the Plugin

As the Unreal Engine Marketplace's build farms aren't using the latest version of Xcode, the binaries shipped with the plugin
might not support some of the latest features. 
To be able to use those features, you have to rebuild the plugin with your own version of Xcode.

To rebuild the plugin:
1. If the project doesn't contain C++ code, add an empty C++ class from the Editor.
1. Copy the plugin from `<UE_ROOT>/Engine/Plugins/Marketplace/UltimateIOSToolkit/` to `<PROJECT_ROOT>/Plugins/UltimateIOSToolkit`.
1. Delete the `Intermediate`, `Build`, and `Binaries` folder in `<PROJECT_ROOT>/Plugins/UltimateIOSToolkit`.
1. Open your project and select `Yes` when asked to build the sources. It will compile the plugin for your current platform.
1. Package your project for iOS.

After doing these steps, the plugin's C++ files should be compiled with your version of Xcode during the compilation stage of the packaging.