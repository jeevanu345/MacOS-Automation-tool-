🚀 Setup Guide (Final Copy Version)
📥 1. Clone the Repo
git clone https://github.com/your-username/macos-automation.git
cd macos-automation

📦 2. Move automation.app Anywhere You Want

Example:

/Users/jeevan/automation.app


If you rename it, remember to update the path in the .plist.

📝 3. Edit com.jeevans.backupscript.plist

Open the plist:

open -a "Visual Studio Code" com.jeevans.backupscript.plist


Edit this section:

<key>ProgramArguments</key>
<array>
    <string>/usr/bin/open</string>
    <string>/Users/jeevan/automation.app</string>
</array>


➡️ Replace the path if your app is somewhere else.

⏰ 4. Change the Scheduled Time
<key>StartCalendarInterval</key>
<dict>
    <key>Hour</key>
    <integer>7</integer>
    <key>Minute</key>
    <integer>30</integer>
</dict>


Examples:

10:00 PM → Hour: 22, Minute: 00

6:45 AM → Hour: 6, Minute: 45

🔐 5. Remove or Update Any Passwords Inside automation.app

Open the automator app:

open -a Automator /Users/jeevan/automation.app


If you find:

echo "OldPassword" | sudo -S some-command


➡️ Replace or remove it.

⚙️ 6. Install the LaunchAgent (Final Ready Code)

Copy the plist:

cp com.jeevans.backupscript.plist ~/Library/LaunchAgents/


Load and activate it:

launchctl load ~/Library/LaunchAgents/com.jeevans.backupscript.plist
