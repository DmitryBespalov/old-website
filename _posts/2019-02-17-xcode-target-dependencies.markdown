---
layout: post
title:  "Xcode Target Dependencies"
description: "Article describing what are Xcode target dependencies, targets, products, when and how to use them."
---

# Definition

![Target Dependencies][1]

Xcode Target Dependencies is a list of dependencies required to build a selected target.

# Details

Xcode target is a specification for building a product.

## Implicit Dependencies

If Xcode *target A* requires output of another *target B*, then A *depends* on B. 

If both targets are in the same project or workspace, then Xcode can detect the dependency automatically.

Thus, Xcode can automatically build target B before target A. 

This is called *implicit dependency*.

To introduce implicit dependency, add a new item to the "Link Binary With Libraries" list in the target's build phases.

![Link Binary With Libraries Build Phase][2]

*Figure 1*. **Link Binaries With Libraries Build Phase**. 1 - Select project, 2 - Select target, 3 - Select Build Phases, 4 - Add or remove items, 5 - Set item as Required or Optional. Required items are *implicit dependencies*.

## Explicit Dependencies

If Xcode target A includes another target B in the Xcode target dependencies, then it is called *explicit dependency*.

Explicit dependency overrides implicit dependency.

Xcode builds all explicit dependencies before the dependent target.

To introduce explicit dependency, add a new item to the "Target Dependencies" list in the target's build phases.

![Target Dependencies Build Phase][3]

*Figure 2*. **Target Dependencies Build Phase**. 1 - Add or remove items. Each item is *explicit dependency* which will override any implicit dependency with the same name.


## Xcode Target Products

Let's take a look at the several types of products which, among others, Xcode can produce: iOS app, iOS framework, Bundle, and libraries.

### The anatomy of an iOS app

The iOS app is an Application Bundle - the directory containing everything to run a program.

This directory has "app" extension and predefined structure. 

- Appplication Bundle directory
    - Info.plist - information about app configuration
    - Executable - file with the name of your product, *YourAppNameHere*
    - Resource files - localized resources are in the *language*.lproj directories, others are in the root of the bundle directory.
        - Asset catalogs (*.car)
        - Storyboards and xibs (*.storyboardc, *.nib)
            - *.storyboardc is itself a directory
                - Info.plist - information about nib files
                - *.nib files
        - Localized strings (*.strings)
        - Custom resource files (anything you want)
    - Supporting files
        - _CodeSignature
        - PkgInfo - special file indicating that this package is an iOS app
        - Frameworks directory - frameworks and dynamic libraries



### The anatomy of an iOS framework

The Framework is a directory with a "framework" extension, that has a predefined structure.

- Framework bundle directory
    - Info.plist
    - Executable
    - Resource files
    - Supporting files
        - CodeSignature

### The anatomy of an iOS bundle

Bundle is a directory with a "bundle" extension that has a simple structure.

- Bundle
    - Info.plist
    - Files

### Static Libraries and Dynamic Libraries

Static library is a compiled code linked to the application executable. 
They are part of the application executable.

Dynamic library is an executable code that is loaded during runtime by the application executable, and invoked from it. 
They are separate from the application executable.

## Xode Target

Xcode target specifies files, build settings, and build phases to create a product.

One target produces one product.

A product is a program, library, framework, app, or other type of output supported by Xcode (see above).

## Xcode Build Phases and Settings

Creating a product requires work of multiple tools of the build system. 

For an iOS app, the standard steps are the following:
* Build all explicit and implicit dependencies
* Create product bundle structure
* Create executable
    * Compile source code files
    * Link the compiled sources, libraries and frameworks into executable
* Copy resources
    * Compile resource files
    * Copy the compiled files to the product bundle
* Sign the source code with developer certificate and copy signature to the product bundle.

Xcode build system is configurable with build settings. They include information:
* Which SDK to use
* Which platform to build for
* Where to search for libraries and frameworks
* Where to put the output files - intermediate and final ones
* Which certificates and provisioning profiles to use for code signing

Xcode build process is configurable with build phases. For iOS app, they include:
* *Target Dependencies Phase* - explicitly specifies the list of other targets to build before the selected target
* *Compile Sources Phase* - specifies the list of source code files to compile
* *Link Binaries With Libraries Phase* - specifies the list of libraries and frameworks that link to the selected target's binary. Xcode uses this list to discover implicit target dependencies.
* *Copy Bundle Resources Phase* - the list of files to copy to the product's package.

Additionally, you can add custom build phases:
* *Copy Files Phase* - will copy specified files to a specified destination
* *Run Script Phase* - will run a script
* *Headers Phase* - will specify list of header files (*.h) that will be copied to the destination's headers directory

# When to use implicit or explicit Xcode target dependencies

Use implicit dependencies for products that need only compilation and linking, that is, static libraries.

Use explicit dependencies for products that need to be copied into target product bundle, that is, for dynamic frameworks and resource bundles. Remember to actually copy these products into destination bundle, so that your target product runs successfully.

Use explicit dependencies for products in the same project or workspace that are linked through build settings (through "Other Linker Flags" variable) and not through "Link Binaries With Libraries" Build Phase.

# How to use implicit and explicit dependencies to create static library with resource bundle and use it in iOS app

To illustrate the use of implicit and explicit dependencies in a single Xcode project, let's take a look at an example.

The example source code is on [GitHub][4].

In the example project, we would like to build an iOS app that uses iOS dynamic framework and iOS static library. The framework includes all of its resources in the framework bundle itself. The library, however, is not a bundle - it just code. That is why, if library requires any resources, we have to ship and include them separately. In this example, the resources are groupped into a resource bundle.

![Target Dependency Diagram][5]

*Figure 3*. The application links and embeds the Framework (explicit dependency), links to the static library (implicit dependency), which explicitly depends on the resource bundle.

This configuration will allow the build system to recompile all of the app components when any of the underlying source files or settings change.

Creation of a library or a framework in the same project is trivial - just use the "Add a target" button in Xcode, as shown in the image below, and then follow the setup wizard.

![Add Target Button][6]

The tricky part is creating a resource bundle. On iOS, this bundle type is unsupported, but we can adjust macOS bundle for iOS platform.

To do so, let's add the macOS bundle to our project. 

Select your project, then click on Add a Target -> macOS -> Bundle -> Specify its name -> Finish.

Go to Target's Build Settings, adjust the following build settings:
* Select and delete `Base SDK`
* `Per-configuration Build Products Path`: replace with `$(BUILD_DIR)/$(CONFIGURATION)`

Now, the Bundle's Info.plist references to an executable file, which is not allowed on iOS, so let's change it.

Go to Target's Info panel, select and delete the "Executable File" property.

Now we are ready to integrate the resource bundle into the main app. 

Select your app target, navigate to Build Phases, and add a new item in the Copy Bundle Resources build phase - add the resources bundle product.

Now, the build system will create the bundle for us and copy it inside the application bundle.

Since we want to use this bundle from the *static library* and not the app directly, we need to add appropriate code to find the resource bundle during runtime and use it to fetch resources.

Here is an example of such code:

```swift
public class MyLibrary {

    public static func myLocalizedString() -> String {
        // find the current library's bundle
        let thisBundle = Bundle(for: MyLibrary.self)
        // find the resources bundle
        guard let resourceBundleURL = thisBundle.url(forResource: "MyResources", withExtension: "bundle"),
            let resourceBundle = Bundle(url: resourceBundleURL) else {
            return ""
        }
        // use the bundle for localization
        let result = NSLocalizedString("some.key", bundle: resourceBundle, comment: "Developer comment here")
        return result
    }

}
```

You can now import the library in the main app and use `MyLibrary.myLocalizedString()` to get that localized string.

# Conclusion

Xcode target dependencies are targets built before the selected target. There are implicit dependencies, discovered by Xcode automatically, and explicit dependencies, which you can add yourself in the target's Build Phases. Xcode can build various product types, among which are iOS apps, iOS dynamic frameworks, iOS static libraries, and bundles. 

Normally, you use only implicit targets that Xcode discovers automatically. If you want to specify specific build order of targets in your project, then use target dependencies build phase. At last, we looked at the example of how to configure iOS app project to use both types of dependencies.

# References

* The icons used in the article images (application icon, library icon, framework icon, bundle icon) are copyright of Apple.
* Code examples are under MIT license.
* <https://developer.apple.com/library/archive/documentation/CoreFoundation/Conceptual/CFBundles/BundleTypes/BundleTypes.html> - bundle types and their structure
* <https://developer.apple.com/library/archive/featuredarticles/XcodeConcepts/Concept-Targets.html> - build targets definition
* <https://developer.apple.com/library/archive/featuredarticles/XcodeConcepts/Concept-Build_Settings.html#//apple_ref/doc/uid/TP40009328-CH6-SW1> - build settings definition
* <https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/BPRuntimeConfig/Articles/ConfigApplications.html> - PkgInfo file explanation

[1]: /assets/target_dependencies_focused.png
[2]: /assets/link_with_libraries.png
[3]: /assets/target_dependencies.png
[4]: https://github.com/DmitryBespalov/XcodeTargetDependenciesExample
[5]: /assets/target_dependency_diagram.png
[6]: /assets/add_target_button.png
