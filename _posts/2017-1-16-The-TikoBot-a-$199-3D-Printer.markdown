---
layout: post
title:  "$179 Tiko 3D printer - Getting Started"
date:   2017-1-16 12:44:28 -0600
categories: jekyll update
---


So if you don't know there is a $179 3D printer out on the market called the [Tiko][Tiko]. I backed it on Kickstarter, This is probably my 3rd `3D printer`-esque projects that I have backed. I started with the [3Doodler][3Doodler] it was so good I backed the second version also. I have backed a few projects on Kickstarter some have been successful others have failed and the company does not exist any longer.

Finally got this thing and I was pumped. Unfortunately it arrived over Christmas and I was 3000 miles away. Once I got back I really wanted to get printing. It was a year late but its Kickstarter so you kinda expect things like that to happen. If you don't you should not user Kickstarter you will be disappointed. This is early backing so you can get something by helping the company get started and off the ground. So with that in mind you have to realize that these are not final products, if you want final products wait till it is backed and they have delivered to all of their backers. That is a relatively safe"er" time to purchase a product but you may miss out on special discounts and getting your hands on it first.

Tips and Tricks Learned.

It took me 2 days to actually get the first things printed. I figured since the instructions was a trifold brochure with 6 instructions that it would be relatively simple to get up and going.

>Step 1. Plug it in.

>Step 2. Connect to the printer.

  They have some pretty cool ideas on making the print process very simple with cloud printing you should be able to connect to your printer from any where and queue up a print but it is not there just yet. Cloud Printing is disabled and being worked on so the only way to connect to the printer is by going to your wifi and connecting to the wifi hotspot it is broad casting. I found that it takes a second for the printer to boot up and actually start casting the hotspot and be connectable.
  Once you have done this you will open a web browser ([Tiko][Tiko]. suggests you use chrome)
  Then type in the url print.tiko/ this will give you the ability to setup your printer the first time and the print interface once you have done that.

>Step 3. Load the PLA.

This is where I made my first mistake. So once you select `Manual Controls` on the upper left a few options appear. This is where you can adjust the brightness of the LED's that light up the print bed. `Load/unload filament` and `Heat Nozzle`. So unwrap your PLA that came with the printer and and uncoil it a few times. Click the `Load Filament` option and the printer should make some sort of noise. This is the motor that pulls the filament into the printer. Then you need to push the filament into the white straw on the inside. You will feed about 18 to reach the nozzle. So my first attempt I put it in and made it all the way to the motor that is supposed to pull it in and subsequently push it all the way to the nozzle. ✔︎ That you push it far enough that is starts to pull the filament. I got it right up to the motor but not to the point it was pulling it. There is some sort of sensor that tells the printer if filament is loaded or not. But this sensor is not located at the nozzle nor is it on the second half of the feed tube. So if your filament is fed half way in the printer will thing the filament is loaded but while you are printing there with be no plastic coming out of the nozzle.

>Step 4. Heat the Nozzle.

This step held me up for a while, would hit the giant `Print` button at the bottom of the interface and it would dismiss the view but nothing would happen with the printer. Super frustrating I hope that they do some improvements on their UX. Come to find out that you have to hit the `Heat Nozzle` and wait the full min before you hit the `Print` button that then takes more then that mount of time to render the object gCode and post that data to the printer.

Not super difficult and I was able to make a print with the default settings but you can play around with those and see how it affects your prints. I was supper impressed on how easy it was to get things going. I do hope that they improve the interface to give a little more feedback when things are not working but I am sure that will evolve. There was really only one major hangup besides that.

> The Design Flaw.

There is an issue with the way that the filament supply tube that runs from the driver motor to the nozzle. What is strange to me is that there is no way that this [Tiko][Tiko]. was tested and printed the demo structure that comes with it because they would have run into this issue. Unless of coarse they did not do the calibration step that they do now where the nozzle goes to each corner and presses into the print base. Because every time it would do that the black section of the supply tube would loop itself around one of the arm motors. This causes the nozzle to pull all the way to the side of the bot and error out because it cannot go back to the `Zero` position. Do not fret though I have a solution. It is super advanced and took a ton of R&D. </sarcasm> if you take a piece of scotch Tape and tape the black section of the tube loosely to the wall of the printer you don't run into the problem. Bam you are all ready to print to your hearts content.

There are some flaws to this but looking at how much I have paid for it I am ok with having to make some adjustments to it myself. I do think it is something [Tiko][Tiko]. could and should fix but its not a deal breaker. I would suggest to anyone wanting to get into 3D printing that the [Tiko][Tiko]. bot is a great starter printer. If you have used a more expensive printer you may be disappointed but that is what makes the [Tiko][Tiko]. bot great. Also I absolutely love the way that it looks. they definitely have some design guys at [Tiko][Tiko]. that know what they are doing.

Share your comments and experiences in the comments.

Happy Printing

[Tiko]:https://www.tiko3d.com/
[KickStarter]:https://www.kickstarter.com
[3Doodler]:https://www.kickstarter.com/profile/1351910088/created
