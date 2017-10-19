---
layout: post
title:  "FrenchKit 2017"
---

In the end of September 2017, I visited Paris, France to attend [FrenchKit](http://frenchkit.fr "FrenchKit") - an iOS conference as a presenter in one of its workshops. In this blog, I describe how the conference went.

This post will be updated as soon as the new videos will be published. 

# Contents
* TOC
{:toc}

# Day 1
The first day started with a light Parisian breakfast of croissants and coffee and the whole auditorium was quickly filled up to the capacity. From the Keynote presentation, I learned that this time the conference was fully booked with 250 participants coming to visit from all over the world. 

The presentations list and conference schedule was announced in Keynote, and it felt like a lot of presentations to see, and what's more, there'll be 2 hours to attend a workshop - one of the classrooms. The conference had an official app with agenda and information about speakers, free Wi-Fi and lots of good content. Check it out.

![Paris](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9471.JPG "Paris"){:height="480px" width="480px"}

![Breakfast crowd](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9473.JPG "Breakfast crowd"){:height="480px" width="480px"}

![In auditorium](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9477.JPG "In auditorium"){:height="480px" width="480px"}

![Keynote](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9482.JPG "Keynote"){:height="480px" width="480px"}

## Playground Driven Development

In the first presentation of the day, Brandon Williams ([@brandonw](https://twitter.com/mbrandonw)) spoke about using playgrounds in development of view controllers. To me, in the beginning of the presentation, was a bit intriguing to see what would the development process look like, and closer to the live demo I was fully sold on the approach.

![Brandon Williams](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9484.JPG "Brandon Williams"){:height="480px" width="480px"}

The main idea is that you can develop and incorporate view controllers inside playgrounds, creating 1 playground per view controller, just like Kickstarter app does. This will shorten your write-build-run cycle, because loading playground is much faster than building the app, navigating to the developed screen, and seeing how it works.

There are other advantages of the approach, too, like view controller isolation, ease of configuration (changing size class and see how the view will be rendered in few moments).

Overall, I highly recommend watching this one.

<iframe width="510" height="325" src="https://www.youtube.com/embed/DrdxSNG-_DE" frameborder="0" allowfullscreen></iframe>

## Table and Collection Views Optimization
This presentation by Janina Kutyn was about optimizing scrolling performance of table views and collection views via offloading GPU processing to CPU.

![Janina Kutyn](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9493.JPG "Janina Kutyn"){:height="480px" width="480px"}

Essentially, you'll be using draw() method to draw your cell's contents on the screen and avoid using lots of UIViews and auto layout.

The slides feature cute chimps and monkeys, check it out yourself!

<iframe width="510" height="325" src="https://www.youtube.com/embed/3F-ZhcWmsrA" frameborder="0" allowfullscreen></iframe>

## What Would Tomster Do?
Next presentation was a bit special because it was out of iOS discourse. The presentation by Julien Palmas ([@bartocc](https://twitter.com/bartocc)) was about using Ember.js to write single-page applications for browsers.

![Julien Palmas](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9499.JPG "Julien Palmas"){:height="480px" width="480px"}

Generally, the approach in Ember.js is similar as writing a server-side app in Ruby on Rails: you have routes, views, and Ember.js handling many things for you automatically with convention over configuration.

I learned that this framework is used across many websites, among which is iCloud!

To widen your horizons, please watch the presentation here.

<iframe width="510" height="325" src="https://www.youtube.com/embed/-ZKYdDJruss" frameborder="0" allowfullscreen></iframe>

## Mocking with Swift
This presentation by Bruno Virlet ([@bvirlet](https://twitter.com/bvirlet)) reviewed the common ways to write mocks in Swift and then went one step further to employ Sourcery to metaprogram template that would generate a mock based on an interface - automagically! 

![Bruno Virlet](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9502.JPG "Bruno Virlet"){:height="480px" width="480px"}

No more written-by-hand boilerplate mocks, stubs and fake objects, just use Sourcery to generate the code for your protocol and you're on your way to faster and easier development process.

To learn how to automate everything you mock, watch the presentation here.

<iframe width="510" height="325" src="https://www.youtube.com/embed/mRrjNzP6RAU" frameborder="0" allowfullscreen></iframe>

## How Apps Are Actually Built
This presentation by Romain Pouclet ([@Palleas](https://twitter.com/Palleas)) was quite interesting to see because of a real-world data from BuddyBuild, who analyzed projects they built and shared this information with FrenchKit's attendees.

![Romain Pouclet](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9503.JPG "Romain Pouclet"){:height="480px" width="480px"}

As I expected, most projects use CocoaPods for dependency management, though, many projects don't use any dependency management (by the way, our project, too). 

Surprisingly for me, very small amount of projects were actually running their unit tests, although many projects had unit test targets (auto-created by Xcode?). Definitely, something to improve on.

Learn more about industry statistics in this presentation.

<iframe width="510" height="325" src="https://www.youtube.com/embed/nwYxwqhp6p4" frameborder="0" allowfullscreen></iframe>

## Server(less) Swift
The presentation by Chris Bailey ([@Chris__Bailey](https://twitter.com/Chris__Bailey)) was about using Swift for running functions in the cloud. Specifically, about how to use Kitura and IBM's serverless service to write, deploy and run your Swift code, function by function.

![Chris Bailey](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9504.JPG "Chris Bailey"){:height="480px" width="480px"}

Personally, I'm not sure where exactly this technology would be useful. I've heard conversational bots, sending push notifications, ... probably, time will show. 

Anyways, the Swift on server topic is an interesting one, and you can learn more about this technology in this presentation.

<iframe width="510" height="325" src="https://www.youtube.com/embed/4kQsuOiI6Ug" frameborder="0" allowfullscreen></iframe>

## May the Code Review Be with You
If there would have been an award for the best presentation slides, I think, this one would win it for sure. The talk by Egor Tolstoy ([@igrekde](https://twitter.com/igrekde)) is exploring different aspects of building an effective code review culture.

![Egor Tolstoy](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9507.JPG "Egor Tolstoy"){:height="480px" width="480px"}

The talk presents different tips about code review ethics, technical details and organizational solutions to common code review problems. 

You definitely have to watch it, check it out here.

<iframe width="510" height="325" src="https://www.youtube.com/embed/e9NI5XnEqHA" frameborder="0" allowfullscreen></iframe>

## Safety-Critical Development, AdaCore
The talk from AdaCore engineer, Clément Bourgeois, was about Ada programming language, and general reflection on what possibilities are opening when programs written with lots of explicit information. 

![Clément Bourgeois](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9514.JPG "Clément Bourgeois"){:height="480px" width="480px"}

One of the best moments in this talk was a realization that your code can be mathematically proven for correctness. I think it's really cool. That means not only your code works for test cases, but for _all_ possible types of inputs, and compiler making sure this is true for you.

To learn more about Ada, the language of Aerospace computing, watch this presentation here.

<iframe width="510" height="325" src="https://www.youtube.com/embed/xbv-Q3ddOg4" frameborder="0" allowfullscreen></iframe>

## You Deserve Nice Things
The talk with an attractive name "You deserve nice things" by Soroush Khanlou ([@khanlou](https://twitter.com/khanlou)) presents an approach that, I think, every developer should follow to make his or her life easier. Namely, wrapping awkward-looking or not so readable APIs into better methods, primarily, using extensions.

![Soroush Khanlou](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9515.JPG "Soroush Khanlou"){:height="480px" width="480px"}

Soroush goes into detailed examples of how one could transform platform APIs from Apple into better code.

Check this talk out here.

<iframe width="510" height="325" src="https://www.youtube.com/embed/3ia3ngqM2mM" frameborder="0" allowfullscreen></iframe>

## Classroom from Deezer
When all presentations finished, there was time for classrooms. A classroom was a workshop on some topic. For my classroom, I picked Deezer's workshop on writing music visualizer with GPU shaders conducted by Adrien Coye de Brunélis.

The classroom was easy to follow through because it was structured into separate exercises. In the end, we ended up having Deezer's logo animated based on the music played. It was cool.

To me, it was surprising how much configuration is required to run just a simple program using OpenGL ES and shaders. UIKit and CoreGraphics, by comparison, are much much much easier to use.

So if you're also interested to see the code behind shader programming, check out classroom repository on [GitHub](https://github.com/FrenchKit/DeezerClassroom).

## Other classrooms
Other classrooms during the first day were:

  * A modern development workflow - Romain Pouclet - BuddyBuild [[GitHub]](https://github.com/FrenchKit/BuddyBuildClassroom)
  * From API Description To Tests & Mocks - Micha Mazaheri [[GitHub]](https://github.com/FrenchKit/PawClassroom)
  * Intermediate and Advanced RxSwift - Florent Pillet [[GitHub1]](https://github.com/FrenchKit/RxSwiftClassroom) [[GitHub2]](https://github.com/FrenchKit/RxClassroom)
  * Fastlane from zero to Hero - Julien Quéré  [[GitHub]](https://github.com/FrenchKit/FastlaneClassroom)

# Day 2
The second day was more relaxed compared to first one, probably because of the previous night in the pub for many of the attendees. It felt like people made some friends already. It felt cozy.

![Day 2](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9518.JPG "Day 2"){:height="480px" width="480px"}

## Core Data Custom Stores
The first presenter, Rew Islam ([@dashlane_rew](https://twitter.com/dashlane_rew)), was talking about different ways to implement custom data stores in Core Data. 

![Rew Islam](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9522.JPG "Rew Islam"){:height="480px" width="480px"}

It turns out, Core Data is capable to work with custom stores that could implement storage using a custom data format, or even through a REST service!

<!--
To learn more about the custom stores and Core Data, watch here.
-->

## Pushing Forward iOS Notifications
This presentation about push notifications guidelines from Adrien Humilière ([@adhumi](https://twitter.com/adhumi)) was concerned with being a "good citizen" among apps on user's device. 

![Adrien Humilière](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9524.JPG "Adrien Humilière"){:height="480px" width="480px"}

> In a world with competition over user's attention it is much easier to delete an app with annoying push notifications than to disable notification settings.

<!--
The author shares tips and best practices about using push notifications in your app, check it out here.
-->

## Rewriting Your Model, Undo and Threading One Step at a Time
Next presentation from the Sketch's founder, Pieter Omvlee ([Tumblr](http://pieteromvlee.tumblr.com)), was a long story how the app lived through evolving model, starting from a simple object graph and ending with a tree of objects representing objects on the canvas.

![Pieter Omvlee](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9527.JPG "Pieter Omvlee"){:height="480px" width="480px"}

<!--
It was interesting to learn how model layer evolved rather than was rewritten several times. You can learn from it, too, here.
-->

## Profiling Swift Performance on Linux
In this presentation, JP Simard ([@simjp](https://twitter.com/simjp)) is talking about hardships during profiling of Swift code on Linux. Specifically, about ways to find time profiling visual. 

![JP Simard](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9534.JPG "JP Simard"){:height="480px" width="480px"}

<!--
Swift on Linux is still a young sphere of development, and this will be helpful for the developers experimenting with Swift on the platform. See the presentation here.
-->

## What's up with Swift 5 
Next presentation from Bas Broek ([@BasThomas](https://twitter.com/BasThomas)) was about current status and approved proposals for Swift 5.

![Bas Broek](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9537.JPG "Bas Broek"){:height="480px" width="480px"}

In the talk, Bas went through different proposals accepted in Swift 5 and mentioned ABI stability as well as Swift concurrency manifesto written by Chris Lattner. The talk gave a good overview of what's coming next in Swift.

## Working at scale - How to Save Time with Ci and Build Time Reduction
This presentation from Yusei Nishiyama ([@yuseinishiyama](https://twitter.com/yuseinishiyama)) is telling about continuous integration setup at Cookpad, with the team across the world working remotely. 

![Yusei Nishiyama](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9539.JPG "Yusei Nishiyama"){:height="480px" width="480px"}

Yusei talks about code reviews, improving their metrics, and improving build times. For me, the interesting part was using code review metrics with Grafana to visualize pull-request review time.

<!--
Watch the presentation here.
-->
 
## Core ML - Let's Talk about Models
In this presentation David Bonnet ([@iGranDav](https://twitter.com/iGranDav)) explained and showed the approach to train a neural network on a popular MNist data set to build a custom CoreML model for handwritten digit recognition.

![David Bonnet](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9549.JPG "David Bonnet"){:height="480px" width="480px"}

<!--
More on that topic you can learn from the presentation itself here.
-->

## Don’t Worry, Be Lazy
In this talk, Olivier Halligon ([@aligatr](https://twitter.com/aligatr)) told about SwiftGen and Sourcery - tools to improve code quality. 

![Olivier Halligon](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9553.JPG "Olivier Halligon"){:height="480px" width="480px"}

It was interesting to learn about those two, and additionally about Gyro - a custom tool to transform xcdatamodel to a Realm classes for iOS and Android.

<!--
Learn more about it here.
-->

## Scaling Open Source Communities
In this talk, Felix Krause ([@KrauseFx](https://twitter.com/KrauseFx)) shared his impressive experience in growing and scaling a community of the fastlane project on GitHub. The author shares techniques on how to automate repetitive tasks in order to keep a number of issues under control and keep one's sanity.

![Felix Krause](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9560.JPG "Olivier Halligon"){:height="480px" width="480px"}

<!--
You can learn more about the development of OSS communities here.
-->

## Update Your Reality with Vision and ARKit
In this talk, Xebia's engineer Julien Datour showcases the small app that he built for the conference using ARKit and Vision framework. The app uses Vision to detect rectangles (physical OSS project cards) on a plane, then finds QR code within the rectangle and based on the GitHub link inside QR-code renders information about GitHub repository on top of the detected rectangle.

![Julien Datour](https://s3.eu-central-1.amazonaws.com/images.dnbespalov.com/frenchkit/IMG_9566.JPG "Julien Datour"){:height="480px" width="480px"}

<!--
Sounds simple, but try to reproduce it ;) Anyway, ARKit is awesome and you can see it in action here.
-->

## UI automation classroom
After all of the presentations finished it was my turn to conduct a workshop among 4 other workshops. Mine was about UI testing in Swift. In the workshop, attendees learned tips and tricks for working with UI tests, specifically: general tips on testing; writing tests for table views and collection views; using localized strings in UI tests and using a mock server for network requests. 

You can find more information about the workshop contents on GitHub. It includes presentation slides, example project, and solutions to the problems (in branches "step1", "step2", and so on).

## Other classrooms
Other classrooms that day were:

  * A modern development workflow - Romain Pouclet - BuddyBuild [[GitHub]](https://github.com/FrenchKit/BuddyBuildClassroom)
  * Leveraging Swift and GLSL shaders to animate realtime music visualisations - Adrien Coye de Brunélis - Deezer [[GitHub]](https://github.com/FrenchKit/DeezerClassroom)
  * Build a Swift Backend-for-Frontend (BFF) - Chris Bailey [[GitHub]](https://github.com/FrenchKit/SwiftServer)
  * Mastering code generation and SwiftGen and Sourcery templates - Olivier Halligon [[GitHub]](https://github.com/FrenchKit/Mastering-code-generation-Classroom)

# Conclusion
To me, the 2 days I spent at the FrenchKit conference went very quick and were worth it 100%. My big thank you to FrenchKit organizers, speakers, and attendees, as well as to Zalando for sponsoring my trip. 

I learned a lot from presentations, had a good time socializing with other developers, and generally had lots of fun. I definitely recommend attending it. 

