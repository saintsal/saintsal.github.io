---
layout: post
title:  "Forcing myself to take Pomodoro breaks"
date:   2013-11-23 15:13:33
tags:   personal
---

I'm awful at taking breaks once I get in the zone, but I've noticed that this is counter-productive by the end of the day.  What's "in the zone" earlier in the day ends up being staring at the screen by the end of the day.

So today, I hacked together a solution. At the end of each Pomodoro, my Pomodoro software loads <a href="http://calm.com">calm.com</a> in full screen, and starts the 2-minute mediation thingy. What a wonderful way to break away!

* Update: Much simpler way!

You can run this little AppleScript, which gives you a 10 and 20 minute warning in Growl, then runs Calm.com after 25 minutes.

Copy this into AppleScript Editor. Modify the script if you like. Then File -> Export and save it as an Application called Countdown. You can run Countdown whenever you start a Pomodoro.

<code>
-- Wait 10 minutes before the first warning (change this if you want)
delay 10 * 60
growlNotification("10 minutes elapsed.")
-- Wait another 10 minutes for another warning
delay 10 * 60
growlNotification("5 minutes to go.")
-- After 25 minutes, load calm.com
delay 5 * 60
makeMeCalm()

on makeMeCalm()
	do shell script "open '/Applications/Google Chrome.app' http://calm.com"
	tell application "Google Chrome" to activate
	tell application "System Events"
		keystroke "f" using {command down, shift down}
		delay 8
		keystroke tab
		keystroke tab
		keystroke tab
		keystroke tab
		delay 1
		keystroke return
	end tell
end makeMeCalm

on growlNotification(message)
	tell application "System Events"
		set isRunning to (count of (every process whose bundle identifier is "com.Growl.GrowlHelperApp")) > 0
	end tell
	
	
	
	if isRunning then
		tell application id "com.Growl.GrowlHelperApp"
			-- Make a list of all the notification types 
			-- that this script will ever send:
			set the allNotificationsList to ¬
				{"Timer", "Another Timer"}
			
			-- Make a list of the notifications 
			-- that will be enabled by default.      
			-- Those not enabled by default can be enabled later 
			-- in the 'Applications' tab of the Growl preferences.
			set the enabledNotificationsList to ¬
				{"Timer"}
			
			-- Register our script with growl.
			-- You can optionally (as here) set a default icon 
			-- for this script's notifications.
			register as application ¬
				"Growl Timer" all notifications allNotificationsList ¬
				default notifications enabledNotificationsList ¬
				icon of application "Script Editor"
			
			--       Send a Notification...
			notify with name ¬
				"Timer" title ¬
				"Timer" description ¬
				message application name "Growl Timer"
			
		end tell
	end if
end growlNotification
</code>


