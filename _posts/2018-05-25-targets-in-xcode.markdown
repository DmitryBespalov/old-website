---
layout: post
title:  "Targets in Xcode"
---

What happens when you start a new Xcode project and select "Single View" iOS app?

When you do this, Xcode creates an app target and configures it so that it can produce the product - iOS app.

Xcode's target aggregates configuration to porduce a product. A target consists of 
* Build Phases,
* Build Settings,
* References to files and folders,
* Build rules to process referenced files and folders.

As I wrote in [Dependencies in Xcode]({% post_url 2018-05-17-xcode-dependencies %}), all targets can depend on other targets, and that's why "Target Dependencies" build phase is not removable from target configuration.

You can delete other build phases:
* Compile Sources build phase lists files needed to compile.
* Link Binary With Libraries references libraries and frameworks required for compilation.
* Copy Bundle Resources copies resource files to the target's product bundle.

You could delete these three build phases and make the build not produce anything. 
You could also replace these three build phases with "Run Script" phase that builds, copies or downloads - whatever floats your boat - target's product and places it to the build output directory. 

That output directory is a special place where Xcode is looking for built products. The `BUILT_PRODUCTS_DIR` build setting specifies the location of that directory. Every Xcode workspace has one built products directory shared across all targets within a workspace. Incidentally, a single project opened by itself also defines an implicit workspace, which you can find inside your `project.xcodeproj/project.xcworkspace` folder.

As I mentioned, Xcode uses this built products directory as a shared place to put all products. Later, Xcode searches products of other targets referenced in the "Link Binary With Libraries" build phase inside built products directory. If you have a workspace or a project with different targets, make sure that your target product names are unique and don't override each other. Each target must have unique product name, so that there would be no name clashes in the built products directory, when, for example, one framework might be overriden by another framework with the same name.

So far we looked at Build Phases, but other target elements are also important. In the next blog I'll write about Build Settings.
