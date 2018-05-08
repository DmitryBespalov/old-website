---
layout: post
title:  "What is a dependency in software?"
---

Dependency is a relationship where one thing uses another thing.

For me, «dependency» of a software project, in general, is any hardware, or program, or kind of a program, or their configuration, or files required to create, build, package, distribute, and run a program. 

That is a broad definition, so let's look for specific examples.

Dependency on a code defined in another source file (Swift):

    // file One.swift
    class iNeedOtherThingsToCompile {
        var otherThings: [OtherThing]? // dependency on OtherThing
    }

    // file Other.swift
    struct OtherThing {}

Dependency on a code defined in the same source file (Swift):

    func invokeOtherFunc() {
        otherFunc() // dependency on otherFunc
    }

    func otherFunc() {
        print("I'm a dependency")
    }

Dependency on a code defined in another module (library or framework):

    import Foundation // dependency on Foundation module

    func iDependOnAnotherClass() {
        if NSUserDefaults.standard.value(for: "key") == nil { // dependency on NSUserDefaults
            print("key is missing from user defaults")
        }
    }

Dependency on a tool:

    // in build.sh
    // this shell script is dependent on its shell syntax
    bundle exec fastlane test // dependency on: ruby, bundler gem, fastlane gem, and fastlane tool's configuration.

Dependency on operating system:

    // any call to operating system program
    // or environment.

More specifically, in a single software package, I'm concerned with direct source code dependencies - when one code unit depends on another for compilation.

Thinking about dependencies in a project helps me to imagine software as a graph where nodes are program units - libraries, classes, methods and functions - and directed edge exist between any two nodes if one unit depends on another. That helps to split the code into isolated islands, or subsystems, and reduces cognitive load required to understand the system as a whole.

As a rule, I try to reduce number of intra-island dependencies - when one unit in one module requires units in another module - that seems to reduce system complexity. 
