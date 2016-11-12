---
layout: post
title:  "Make a Post!"
date:   2016-10-16 16:46:28 -0600
categories: jekyll update
---
Recently I have been working on a project for my kids. Of coarse since it was a new project I decided to do it in the newest version of Swift. I wanted to make some simple games that could help my young ones learn.
I love playgrounds and all that they enable us to do. I came across this project that [@uraimo][uraimo] which has a running list of [Awesome Swift Playgrounds][Awesome-Swift-Playgrounds]. There is one for spriteKit Which I really wanted to make a game with but of coarse it was written in swift 2.2 I was not about to let that hold me back so I went ahead and started trying to  convert it to swift 3. I went through all the changes that Xcode suggested and finally made it to a point where I had no errors. The issue was that the example did not preform the way it did previously. After going back and converting each function 1 by 1. I determined the function that was not being called.

{% highlight swift linenos %}
func didBeginContact(contact: SKPhysicsContact) {
        // Executed if the ball makes contact with the block.
        if contact.bodyA.categoryBitMask == CategoryBitMask.Ball && contact.bodyB.categoryBitMask == CategoryBitMask.Block {
            let block = contact.bodyB.node as! SKSpriteNode
            // Turn the block gray if it hasn't been hit yet.
            if block.name == "Block" {
                block.color = SKColor.darkGray
                block.name = "HalfBlock"
            }
            // Remove the block from the scene if it has already been hit.
            else {
                block.removeFromParent()
            }
        }
    }
{% endhighlight %}

Then the next step was to figure out what I am missing but when I would try and find something it was already outdated. Even Apples documentation was for `objectiveC`. Then it hit me that this function was not that `swifty` which is what allot of the changes for swift 3 were all about. There is to much redundancy `func didBeginContact(contact: SKPhysicsContact) {` and there in lies the solution. See Xcode suggested to add the perimeter `contact:` and technically the method is valid so no errors were thrown. But this method is key for detecting collision between two objects and is the method that conforms to `SKPhysicsContactDelegate`.
  So since swift is aiming to be super readable if you take out the brackets it should read like a sentence of sorts. "did Begin Contact contact SKPhysicsContact" is a supper redundant sentence in my book. Take out the first contact and all is well. I don't know why Xcode did not remove it when it added the parameter label like it does in many other instances but that is neither here nor there.

So I corrected my mistake and everything works just as it should.
Corrected Code :
{% highlight swift linenos %}
func didBegin(_ contact: SKPhysicsContact) {
        // Executed if the ball makes contact with the block.
        if contact.bodyA.categoryBitMask == CategoryBitMask.Ball && contact.bodyB.categoryBitMask == CategoryBitMask.Block {
            let block = contact.bodyB.node as! SKSpriteNode

            // Turn the block gray if it hasn't been hit yet.
            if block.name == "Block" {
                block.color = SKColor.darkGray
                block.name = "HalfBlock"
            }
            else {
                block.removeFromParent()
            }
        }
    }
{% endhighlight %}


Now I can explore changing variables and learn about `SpriteKit` more if you would like to check out the playground you can get the [updated Swift 3 version here][swift3Version]


[Awesome-Swift-Playgrounds]: https://github.com/uraimo/Awesome-Swift-Playgrounds
[uraimo]: https://twitter.com/uraimo
[swift3Version]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
