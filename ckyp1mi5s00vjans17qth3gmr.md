## iOS Simulator / Live Preview unable to type using physical keyboard

You are beginner iOS developer and are trying to run your application in the simulator. Now you got your app running in your simulator, and you are trying to text out your text field, but darn it! You can't use your keyboard? What a piece of crap!

# Simulator

Well, this is most likely because you by mistake disabled it. I did this several times in my short span of iOS development. Apparently you can disable the by pressing Cmd+Shift+K

Or you can go the Simulator -> I/O -> Keyboard -> Connect Hardware Keyboard

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1642806392899/WM8lDvE37.png)

# Live Preview

So it seems that in the latest version of the Xcode 13.2.1 and using iOS 15 in your live preview, you can't type.

But you can bring the iPhone keyboard, but you won't be able to see it! Ha! Pretty useless, huh? However, it should be fine to write gibberish. You can bring the invisble keyboard by pressing Command+K. If you want to read more about this, you can read more [here](https://developer.apple.com/forums/thread/681571).



