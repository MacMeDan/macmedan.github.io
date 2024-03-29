---
layout: post
title:  "JSQMessagesViewController Swift 3"
date:   2016-11-20 16:46:28 -0600
categories: jekyll update
---

I actively contribute to JSQMessagesViewController, an Open Source Project, that makes it super easy to get a "iMessages" like feature into any app. Often the first step is the hardest. Many users have different levels of experience, education and understanding and since I am a Swift Nut we'll explore implementing it in Swift.

So I will outline the minimum you have to do to get this up and running. 🏃

<h4>Step 1. Create Your project.</h4>
Open Xcode.
 - Go to File -> New Project.
 - Select single view application.
 - Give your project a name and save.

<h4>Step 2. Cocoapods to your computer</h4>

[Cocoapods][cocoapods] is a dependency manager for Swift and Objective-C Cocoa projects. It has over 25 thousand libraries and is used in over 1.2 million apps.

To install `cocoapods` open up `terminal`
`Command + SpaceBar` will open SpotLight. type `Terminal` or use finder -> `/Applications/Utilities/Terminal.app`
exicute this command in your terminal window and [cocoapods][cocoapods] will be installed
{% highlight linenos %}
 sudo gem install cocoapods
{% endhighlight %}

Once this has complete you need to navigate to your project's directory(folder). You can open Folders by using the command `cd` followed by the `path/to/file` and you can move up a folder with the `..` command.
To quickly open a folder in terminal type `cd` and then drag the file from finder to the terminal window. This will insert the path to the file for us. Hit enter and you are now at your project's base directory.

<h4>Step 3. Adding cocoapods to your project</h4>
Run command
{% highlight linenos %}
pod init
{% endhighlight %}

This creates a podfile for you. This is where you can manage `pods` that you want to incorporate in your app. Open this file up in your favorite text editor.
<h4>Step 4. Adding JSQMessagesViewController to your project</h4>
This is the bear minimum you need to have in your podfile.

{% highlight linenos %}

#if you're using Swift
 use_frameworks!

target 'YourProjectName' do
  pod 'JSQMessagesViewController'
end
{% endhighlight %}

Save your file and close it. Now back in terminal type: `pod install` This will add the `JSQMessagesViewController` library to your project.

<h4>Step 5. Open Workspace</h4>
Pods do an interesting thing where they manage the configuration of your project for you so you do not have to. The way that they do this is by generating a `.workspace` for you. So if you had your project open in `XCode` previously, Close it and open the `YourProjectName.workspace` file that was generated.

At this point you should be able to hit run and your project builds. You will not see anything because we have not added anything yet but you should not have any build errors.

<h4>Step 6. Adding JSQMessagesViewController to your project</h4>
Now let's code, modify the UIViewController that comes with crating a new project.

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

The last function in this code snippit is not required is is just a helper to show how you can add messages to your feed.

That's it 🏁, the minimum amount of code you need to get a chat feature in your own app. There are tons of things that you can do from this point but we'll save that for another time. Don't be afraid to explore and change things. That's how we learn. 🖖

If you have any questions or critiques open an issue on GitHub for this article and Ill see what I can do to help.

[stackoverflow]:http://stackoverflow.com/questions/tagged/jsqmessagesviewcontroller
[cocoapods]:https://cocoapods.org/
