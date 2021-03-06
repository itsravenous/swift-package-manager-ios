# Swift Package Manager with iOS

This project demonstrates a working method for using Swift Package Manager to manage the dependencies of an iOS project. It is developed on Xcode 9 (beta 5 at time of writing), using Swift 4 and the SPM v4 description format.

I haven't tried the process with Xcode 8.3 & Swift 3.1.

It will build a simple app using [RxSwift](https://github.com/ReactiveX/RxSwift), which I've chosen because it shows how to handle modules generated from Objective-C.

The end result will be a standard iOS Application product, with Static Frameworks for each of its dependencies embedded within the bundle.

You can link the dependencies dynamically if you prefer, by removing the `config.build_settings['MACH_O_TYPE'] = 'staticlib'` line in `generate-project-dependencies.rb`, and adding your frameworks to the `Embed Frameworks` Build Phase for your app bundle.


You can step through the commits to see what steps I've taken, with a brief overview of the process below.

## Process

1. Generate iOS App project with Xcode
2. Generate swift package for Dependencies
3. Create dummy source file for Dependencies
4. Override build settings in generated xcodeproj
5. Add Dependencies.xcodeproj as subproject of the App xcodeproj
6. Add a dependency (to RxSwift in this example) in Package.swift
7. Link our App with the new Rx*.frameworks
8. Write some sample code to verify that the import works
9. Override MODULEMAP_FILE setting for non-Swift modules

