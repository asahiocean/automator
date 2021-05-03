# Typesetter

Have you also had moments when copy-paste doesn't work?

For example, here. There was such a situation when pasting from the clipboard does not work.

![](https://media.giphy.com/media/BUm95s6HNl3UARSFQ6/giphy.gif)

### Ok, I accept the challenge!  🔥

### 1. Launching Automator.

![](https://i.imgur.com/5htAsb4.png)

### 2. Creating a "Quick Action"

![](https://i.imgur.com/yUpBHxD.png)

### 3. Search for “AppleScript” and drag & drop on to the right pane

![](https://i.imgur.com/htAVCew.png)

### 4. You will see a window with a standard script:

![](https://i.imgur.com/6LjJnXk.png)

### Update the script like below:

```applescript
on run {input, parameters}
	tell application "System Events" to keystroke (the clipboard as text)
	return input
end run
```

### 5. Save it! Cool job! 👍

You can also bind a hotkey to it:

```
Keyboard -> Shortcuts -> Services
```

![](https://i.imgur.com/AOxSjZr.png)

**At startup script, you may see a system window where you will need to allow the computer to be managed using the universal access function.**

You will need to give permissions so that the script can run.

### As a result, when you run the script, the text from the clipboard will print itself! 🎉

![](https://media.giphy.com/media/BUm95s6HNl3UARSFQ6/giphy.gif)

### Good luck!
