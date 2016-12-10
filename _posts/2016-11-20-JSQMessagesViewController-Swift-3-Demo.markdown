---
layout: post
title:  "JSQMessagesViewController Swift 3 Demo"
date:   2016-11-20 16:46:28 -0600
categories: jekyll update
---

I actively contribute to JSQMessagesViewController an Open Source Project that makes it super easy to get a "iMessages" like feature into your app. I like to keep up on the questions on [stackoverflow][stackoverflow] in regard to this. Often the first step is the hardest. Many users have different levels of experience, education and understanding and Since I am a Swift Nut we will exospore implementing it in Swift.

So I will outline the minimum you have to do to get this up and running.

##Step 1. Create Your project.
I am not going to go into much detail about this.
Open Xcode.
Go to File -> New Project.
Select single view application.
Give your project a name and save.

##Step 2. Adding [Cocoapods] to your computer
####if you already have [Cocoapods][cocoapods] you can skip this step.

[Cocoapods][cocoapods] CocoaPods is a dependency manager for Swift and Objective-C Cocoa projects. It has over 25 thousand libraries and is used in over 1.2 million apps.

To install cocoapods open up `terminal`
you can use the "Spotlite" Shortcut which is `Command + SpaceBar` and then type `Terminal` or just open it from finder -> `/Applications/Utilities/Terminal.app`
simply type this command in and [cocoapods][cocoapods] will be installed
{% highlight linenos %}
 sudo gem install cocoapods
{% endhighlight %}

Once this has complete you need to navigate to your projects directory(folder). You can open Folders by using the command `cd path/to/file` and you can back out of folders with the command `..` but instead of navigating one folder at a time lets just open terminal type `cd ` and then drag our project from the finder window onto the terminal window. This will print out the path to the project for us. Hit enter and you are now at your projects base directory.

##Step 3. Adding [cocoapods][cocoapods] to your project
Now that you are at your base directory just type
{% highlight linenos %}
pod init
{% endhighlight %}

This creates a podfile for you. This is where you can manage cocoapods that you incorporate in your app. So Open that file up in any text editor you prefer.
##Step 4. Adding JSQMessagesViewController to your project
This is the bear minimum you need to have in your podfile.

{% highlight linenos %}

#if you're using Swift
 use_frameworks!

target 'YourProjectName' do
  pod 'JSQMessagesViewController'
end
{% endhighlight %}

Save your file and close it. Now back in terminal type: `pod install` This will add the JSQMessagesViewController library to your project.

##Step 5. Open Workspace
Pods do an interesting thing where they manage the configuration of your project for you so you do not have to. The way that they do this is by generating a `.workspace` for you. So if you had your project open in `XCode` previously, Close it and open the `YourProjectName.workspace` file that was generated.

At this point you should be able to hit run and your project builds. You will not see anything because we have not added anything yet but you should not have any build errors.

##Step 6. Adding JSQMessagesViewController to your project
Now lets code, modify the UIViewController that comes with crating a new project.

Here is the minimum amount of code you need in this file.
{% highlight swift linenos %}
//
//  ChatViewController.swift
//  SwiftExample
//
//  Created by Dan Leonard on 12/2/16.
//  Copyright © 2016 MacMeDan. All rights reserved.
//

import UIKit
import JSQMessagesViewController

class ChatViewController: JSQMessagesViewController {
  var messages = [JSQMessage]()
  let defaults = UserDefaults.standard
  var conversation: Conversation = makeConversation() // Here is where your messages are added.
  var incomingBubble: JSQMessagesBubbleImage!
  var outgoingBubble: JSQMessagesBubbleImage!
  var displayName: String!

  override func viewDidLoad() {
    super.viewDidLoad()
        incomingBubble = JSQMessagesBubbleImageFactory().incomingMessagesBubbleImage(with: UIColor.jsq_messageBubbleBlue())
        outgoingBubble = JSQMessagesBubbleImageFactory().outgoingMessagesBubbleImage(with: UIColor.lightGray)

        collectionView?.collectionViewLayout.incomingAvatarViewSize = .zero
        collectionView?.collectionViewLayout.outgoingAvatarViewSize = .zero

    self.collectionView?.reloadData()
    self.collectionView?.layoutIfNeeded()
  }

  // MARK: JSQMessages CollectionView DataSource
  override func senderId() -> String {
    return "1"
  }

  override func senderDisplayName() -> String {
    return displayName
  }

  override func collectionView(_ collectionView: UICollectionView, numberOfItemsInSection section: Int) -> Int {
    return messages.count
  }

  override func collectionView(_ collectionView: JSQMessagesCollectionView, messageDataForItemAt indexPath: IndexPath) -> JSQMessageData {
    return messages[indexPath.item]
  }

  override func collectionView(_ collectionView: JSQMessagesCollectionView, messageBubbleImageDataForItemAt indexPath: IndexPath) -> JSQMessageBubbleImageDataSource {
    return messages[indexPath.item].senderId == self.senderId() ? outgoingBubble : incomingBubble
  }

  func makeConversation() -> [JSQMessages] {
    // This is just for demo purposes, if you add more messages to this array they will appear in your conversation feed.
    return [JSQMessage(senderId: "053496-4509-288", displayName: "Dan leonard", text: "Check out this awesome library called JSQMessagesViewController")]
  }
}
{% endhighlight %}

The last function in this code sippit is not required is is just a helper to show how you can add messages to your feed.

That's it, The minimum amount of code you need to get a chat feature in your own app. There are tons of things that you can do to add more functionality but we will save that for another time. For this tutorial I will leave it here. Don't be afraid to explore and change things. That is how I learn best.


[cocoapods]https://cocoapods.org/
[stackoverflow]: http://stackoverflow.com/questions/tagged/jsqmessagesviewcontroller
