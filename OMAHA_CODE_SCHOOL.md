# Start Here

Download **iTerm**. This is a command-line utility that you'll use on your Mac.

Click to download: https://iterm2.com/downloads/stable/iTerm2-2_1_4.zip

Then install iTerm. Here is a video showing how to install it: http://cl.ly/el8i/iterm.mov

---

Once it's installed, open iTerm.

(Press **Command + Spacebar** to activate **Spotlight**. Start typing "iTerm" into it, and you'll see it appear. Then just click on it to open.)

Into iTerm, copy/paste these lines...

```bash
curl --remote-name https://raw.githubusercontent.com/omahacodeschool/laptop/master/mac
sh mac 2>&1 | tee ~/laptop.log
```

...and then hit the `return` key on your keybord.

You'll be asked to enter your password. This is the password for your Mac. While you type it in, nothing will be shown. It's weird, but rest assured that your characters are being typed.

Next, you will probably be asked to install some software. Go ahead and install it. It should be fairly quick (just a few minutes).

When it finishes, you might need to re-enter your password to continue the main installation script.

Once you resume the script, it'll probably take 5-20 minutes to complete. You can do things from the **Other Setup** section below while it's working. But check back every couple minutes to see if the terms "error" or "fatal error" have appeared. That means there's a problem, and you should let someone know.

The term "warning" is fine–you can ignore any warnings.

Also check back occasionally to see if it's asking for your password again (It's okay if it does).

You'll know the script is complete if you saw no _errors_ and it's back to the "prompt" (which is where one types new commands).

## Other Setup

You can do the following while the main Laptop installation script is running.

1. System Preferences
  1. Enable unverified software installs (**System Preferences > Security**).  
  ![](http://cl.ly/ZPqP/Screen%20Shot%202015-01-22%20at%201.20.46%20PM.png)
  2. Speed up keyboard settings (**System Preferences > Keyboard**)  
  ![](http://cl.ly/ZPnC/Screen%20Shot%202015-01-22%20at%201.21.45%20PM.png)
  3. Enable tap-for-click (**System Preferences > Trackpad**).  
  ![](http://cl.ly/ZQdH/Screen%20Shot%202015-01-22%20at%201.23.37%20PM.png)
2. Slack
  1. You should already have received an invitation to Slack, which is a tool we use to chat with each other. We use this _a lot_--everyone needs to set it up.
  2. [Download](https://itunes.apple.com/us/app/slack/id803453959) the Slack application so that you can run it on your Mac. There is a website version too, but everyone in class should use the Mac version from now on.
  3. Open the **Slack** application and sign in.
    - Domain: omahacodeschool
    - Username/Email: The email address you used when you applied to OCS.
    - Password: You should know this, but you can use the 'Forgot Password' feature if you need to.
3. Registrations (If you've already signed up for something and confirmed your account, you don't need to do it again.)
  - Heroku: https://signup.heroku.com/www-header
    - Confirm your account by clicking the link they email you. That's when you'll choose a password as well.
  - Hacker News: https://news.ycombinator.com/login?whence=news

That's everything you can do until the main installation script is complete.
  
---

**Do not do the following until the main Laptop installation script is complete.**

Once the main installation script is completed, do the following steps in order:

4. OhMyZSH
  1. Quit/Restart iTerm.
  2. `curl -L http://install.ohmyz.sh | sh`
  3. Quit/Restart iTerm.
5. GitHub
  1. Into iTerm: `ssh-keygen -t rsa -C "your_email@example.com"` - Use your real email address! (The same one you used to sign up for GitHub.com.) Don't delete the quotes. They're important.
    - So, if I did this, I would type the following exactly: `ssh-keygen -t rsa -C "sumeet@sumeetjain.com"`
    - It'll ask you some stuff and then for more stuff. Just keep hitting **Enter** until you're back at the prompt.
  2. `eval "$(ssh-agent -s)"`
  3. `ssh-add ~/.ssh/id_rsa`
  4. `pbcopy < ~/.ssh/id_rsa.pub` - This copies a bunch of text for you, without you even realizing it. Magic.
  5. Go to https://github.com/settings/ssh
    - Click "Add SSH Key"
    - Leave the 'Title' field blank.
    - In the 'Key' section, paste the stuff that was magically copied from earlier. Don't modify it in any way – not even to delete an extra blank line that you think is unimportant.
    - Save by clicking the green "Add Key" button.
  6. `ssh -T git@github.com`
    - Type "yes" or "y" for any questions it asks you.
    - If the message it gives you now contains the word "successfully", you're good.
6. Heroku
  1. `heroku login`
    - Use the Heroku email address and password from earlier.
  2. `heroku keys:add`
    - Type "yes" or "y" for any questions it asks you.
7. Sublime Text
  1. Click https://download.sublimetext.com/Sublime%20Text%20Build%203083.dmg
    - This downloads a "DMG" file into your **Downloads** folder.
    - Click on the downloaded DMG file to open it.
    - Drag the Sublime Text application icon into the **Applications** folder to install it.
    - Here is a video showing that done: http://cl.ly/ekey/st.mov
  2. Open **Sublime Text**
    - Then go to the User Settings by clicking **Sublime Text** > **Preferences** > **Settings - User**. (Here's a video showing how to get to that file: http://cl.ly/ell5/stprefs.mov)
    - Erase all content from that document (There shouldn't be much).
    - Copy/Paste all of the content from [this link](https://raw.githubusercontent.com/omahacodeschool/laptop/master/sublime_text_prefs) into that document.
    - Save the document, and then close the document.
  3. In **iTerm**, run the following line of code: `ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/subl`
    - Then quit and re-open **iTerm**.
7. Git Setup
  1. `git config --global core.editor "subl -w"`
  2. `git config --global user.name "Your Name"` - Use your real name!
  3. `git config --global user.email "your_email@example.com"` - Use the email address that you used to sign up for GitHub.com.
  4. `git config --global core.excludesfile ~/.gitignore`
7. Gems
  1. `mate ~/.gemrc`
    - Into the blank document that just opened up, paste the following:
    `gem: --no-rdoc --no-ri`
    - Then save the file and close it.
  2. Quit/Restart iTerm.
  3. `gem install jekyll`
  4. `gem install rails`
    - If it asks whether you want to "overwrite some executables", you do.
  5. `gem install pry`
  6. `gem install bundler`
8. `rbenv rehash` (and then quit/restart iTerm)
9. A folder for your work.
  - `cd ~`
  - `mkdir Code`
  - Set up your **Finder** window.
    - Drag your **Code** folder into the sidebar. Do the same for any other major folders you use often.
10. Testing Rails
  - `cd ~/Code`
  - `rails new temp -d postgresql`
    - This makes a new Ruby on Rails project, called "Temp". It makes the project in a new folder, named "temp".
  - `cd temp`
  - `rake db:create`
  - `rails server`
    - Go to <http://localhost:3000>. You should be welcomed to a new Rails project.
  - Back in iTerm, press **Control + C** to "cancel" (exit) the Rails program.
  - Make sure you are in **~/Code/temp** by typing `pwd` (which tells you what your current location is).
  - Then type:
    - `git init`
    - `git add .`
    - `git commit -m "Test application"`
    - `heroku create`
    - `heroku addons:create heroku-postgresql:dev`
    - `git push heroku master`
      - If there are no errors, you're done!  
      ![](http://cl.ly/ZPYM/18rm2xn1of2b9gif.gif)
