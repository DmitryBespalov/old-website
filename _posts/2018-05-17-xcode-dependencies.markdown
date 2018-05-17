---
layout: post
title:  "Dependencies in Xcode"
---

So, the dependencies, in general, are much more than Xcode's dependencies - I described that in another post: [What is a dependency in software?]({% post_url 2018-05-08-dependency %}).

In Xcode's terms, dependencies define the order of build targets: dependencies are built before dependent targets.

As mentioned, Xcode's dependencies exist in the context of build targets. Xcode has a fairly complicated build system, but what it boils down to, is that you can define a target to build some product, say executable or library. To build it, the target has different inputs - source code files, build settings and more. 

If you have multiple targets in the same project, then one target can depend on another. If you put one target's product to "Link binary with targets" build phase, then this target will depend on another _implicitly_. Xcode will discover this and will build another target _before_ building the current one. 

There's another way to set up dependencies between targets - _explicitly_ - by adding another target to the "Target Dependencies" build phase. And here's a quirk: you can only add explicit target, if it is defined in the same project, or from the project reference in the same project. Another words, if a target is defined in another project, then that project file must be referenced - emm... drag and dropped - into the project where you want to use it.

That's it. These two mechanisms, implicit and explicit target configuration define the build order of different targets in a project or workspace. 
