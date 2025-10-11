# 🍎 macOS File Automation Script 

Ever wished your Mac could do boring file tasks *automagically* every day? 🪄  
This little project is for you!

I built a simple but powerful Automator-based app that runs on a schedule and handles repetitive file tasks — like backups, organizing files, or cleaning folders — without you having to click a thing. It's like a personal robot, but without the metal arms 🤖.

---

## 🛠️ What’s in the Box?

- **`automation.app`** – This is your custom-built Automator app. It contains the magic (scripts, file moves, etc.) and can be edited in Automator.
- **`com.haris.backupscript.plist`** – This is a LaunchAgent configuration file. It tells macOS:  
  👉 “Run `automation.app` every day at a specific time.”

---

## 🔍 What Does It Actually Do?

The current version runs a workflow that I use for:
- Backing up files from one folder to another
- Automatically organizing downloads
- Cleaning up old junk

But you can **edit it to do anything**:
- Move, copy, or delete files
- Open apps
- Run shell or AppleScript commands
- Sync folders, tag files, even play sounds (why not?)

---

## 🚀 Setup Guide (Super Simple, I Promise!)

Follow these steps to get your Mac doing chores for you:

---

### 📥 1. Download or Clone the Repo
You can use Git or just click "Download ZIP".

```
git clone https://github.com/your-username/macos-automation.git
cd macos-automation
```

📦 2. Move the automation.app to a Folder of Your Choice
Pick a folder like:
```
/Users/yourname/automation.app
```

💡 You can also rename the app if you want — just make sure you update the path in the next step.


📝 3. Edit the LaunchAgent .plist File
Open com.jeevans.backupscript.plist in TextEdit, VS Code, or any text editor.
Find this block:
```
<key>ProgramArguments</key>
<array>
    <string>/usr/bin/open</string>
    <string>/Users/yourname/automation.app</string>
</array>
👉 Change /Users/yourname/automation.app to the full path where your .app is located.
⏰ 4. Change the Run Time
Still in the .plist, find this block:
<key>StartCalendarInterval</key>
<dict>
    <key>Hour</key>
    <integer>7</integer>
    <key>Minute</key>
    <integer>30</integer>
</dict>
```

Change the <integer> values to whatever time you want the app to run (24-hour format).
Example:
```
22:00 for 10:00 PM
6:45 for 6:45 AM
```

🔐 5. Update or Remove the Password (Important!)
Open the automation.app file in Automator:
```
open -a Automator /Users/yourname/automation.app
```
If you see anything like this:
```
echo "YourOldPassword" | sudo -S some-command
```

🗂 6. Install the LaunchAgent
Now copy your updated .plist file to the correct system folder:
```
cp com.haris.backupscript.plist ~/Library/LaunchAgents/
```
Then load it to activate:
```
launchctl load ~/Library/LaunchAgents/com.haris.backupscript.plist
```
