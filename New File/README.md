# New File

1. Open Automator
2. Create a new file and select "Quick Action"
3. Go to search (⌥⌘F) and enter: "applescript"
4. Move the code there and save!
5. I recommend making Shortcuts to create files faster, it's convenient!

## Code
```applescript
set title to "untitled"
set extension to ".txt"
set newfile to title & extension -- "file" is reserved by the system, so "newfile"
set isDesktop to false

try
	tell application "Finder"
		set isFolder to (folder of the front Finder window) as alias
	end tell
on error
	-- if no windows are open "Finder"
	set isFolder to path to desktop folder as alias
	set isDesktop to true
end try

-- block of code with settings for the dialog box for specifying the file name
-- to open the directory with icons, go to the terminal and enter
-- open /System/Library/CoreServices/CoreTypes.bundle/Contents/Resources
set displayText to "Enter file name and extension:"
set newfile to text returned of (display dialog displayText ¬
	with icon file ¬
	":System:Library:CoreServices:CoreTypes.bundle:Contents:Resources:GenericApplicationIcon.icns" default answer newfile)

tell application "System Events"
	set fileList to get the name of every disk item of isFolder
end tell

-- if such a file already exists, then the number will be added to the name of the new file
-- search for an unoccupied number will be found by iterating over all files with the same name
set x to 1
repeat
	if newfile is in fileList then
		set newfile to title & " " & x & extension
		set x to x + 1
	else
		exit repeat
	end if
end repeat

tell application "Finder"
	activate
	set thefile to make new file at folder isFolder with properties {name:newfile}
	if isDesktop is false then
		reveal thefile
	else
		select window of desktop
		set selection to thefile
	end if
end tell

tell application "System Events"
	tell process "Finder"
		open thefile -- to open the file in the default editor
		-- keystroke return -- to rename the new file
	end tell
end tell
```
