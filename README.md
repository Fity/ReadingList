# Reading List
[![Build Status](https://travis-ci.org/AndrewBennet/ReadingList.svg?branch=master)](https://travis-ci.org/AndrewBennet/ReadingList)
[![codebeat badge](https://codebeat.co/badges/3f7723a7-8967-436e-b5e9-549e0261603c)](https://codebeat.co/projects/github-com-andrewbennet-readinglist)

[Reading List](https://www.readinglist.app) is a free, open source iOS app for iPhone and iPad. Reading List allows users to track and catalog the books they read.

<img src="https://www.readinglist.app/assets/iPhone%20X-0_ToReadList_framed.png" width="280"></img>

<a href="https://itunes.apple.com/us/app/reading-list-book-log/id1217139955?mt=8">
  <img src="https://linkmaker.itunes.apple.com/assets/shared/badges/en-us/appstore-lrg.svg" style="height: 60px;"/>
</a>

<a href="https://testflight.apple.com/join/kBS5mVao">
  <img src="https://developer.apple.com/assets/elements/icons/testflight/testflight-64x64_2x.png" height="45px" />
</a>

## Requirements
 - Xcode 11

## Dependencies

Reading List uses a couple of package managers:

- [Mint](https://github.com/yonaskolb/Mint), to manage Swift command line tool packages
- [Bundler](https://github.com/bundler/bundler), to manage Ruby tools

Mint can be installed using [Homebrew](https://brew.sh/) (among [other methods](https://github.com/yonaskolb/Mint#installing)); Bundler can be installed with [RubyGems](https://rubygems.org/):

    brew install mint
    gem install bundler

### XcodeGen
The Xcode project should be generated by running [XcodeGen](https://github.com/yonaskolb/XcodeGen):

    mint run yonaskolb/XcodeGen

### SwiftLint
[SwiftLint](https://github.com/realm/SwiftLint) is used to enforce Swift style guidelines. An Xcode build step runs SwiftLint; this requires it to be installed. To install it, run:

    mint install realm/SwiftLint

### CocoaPods
Reading List uses various third party libraries, which are managed using [CocoaPods](https://cocoapods.org/). To ensure that CocoaPods is installed, run `bundler install`. To install the libraries, run:

    pod install

## Architecture
Reading List is written in Swift, and primarily uses Apple provided technologies.

### UI
Reading List mostly uses [storyboards](https://developer.apple.com/library/content/documentation/General/Conceptual/Devpedia-CocoaApp/Storyboard.html) for UI design (see below); a limited number of user input views are built using [Eureka](https://github.com/xmartlabs/Eureka) forms.

![Example storyboard](./media/storyboard.png)

### Data persistence
Reading List uses [Core Data](https://developer.apple.com/documentation/coredata) for data persistence. There are three entities used in Reading List: `Book`, `Subject` and `List`. The attributes and relations between then are illustrated below:

<img src="./media/coredata_entities.png" width="400px;" alt="Core data entities"/>
