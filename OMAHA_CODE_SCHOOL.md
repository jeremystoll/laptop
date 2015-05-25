# Main Installation Script

Open **Terminal**.

(Press **Command + Spacebar** to activate **Spotlight**. Start typing "Terminal" into it, and you'll see some magic.)

Into **Terminal**, copy/paste these lines:

```bash
curl --remote-name https://raw.githubusercontent.com/omahacodeschool/laptop/master/mac
sh mac 2>&1 | tee ~/laptop.log
```

You'll be asked to enter your password. This is the password for your Mac. While you type it in, nothing will be shown. It's weird, but rest assured that your characters are being typed.

Next, you will probably be asked to install some software. Go ahead and install it. It'll take 5-10 minutes.

While that installation is going on, you can do the first few steps from the "Other Setup" section below.

Keep checking back on that installation though. When it finishes, return to **Terminal** to continue the main installation script. You might need to re-enter your password.

Once you resume the main installation script, it'll probably take 5-15 minutes to complete.

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
  1. Enable/Invite the student.
  2. Use invitation or Forgot Password to get logged in via Web.   (https://omahacodeschool.slack.com/forgot)
  3. [Download](https://itunes.apple.com/us/app/slack/id803453959)
  4. Open **Slack** application and sign in.
    - Domain: omahacodeschool
    - Username/Email: The email address you used when you applied to OCS.
    - Password: The password you just set for Slack.
3. Registrations
  - Heroku: https://signup.heroku.com/www-header
    - Confirm your account by clicking the link they email you. That's when you'll choose a password as well.
  - Hacker News: https://news.ycombinator.com/login?whence=news
  - Treehouse: Expect an email invitation.
  
---

**Do not** do the following until the main Laptop installation script is complete.

4. OhMyZSH
  1. Quit/Restart **Terminal.**
  2. `curl -L http://install.ohmyz.sh | sh`
  3. Quit/Restart **Terminal.**
5. GitHub
  1. `ssh-keygen -t rsa -C "your_email@example.com"` - Use your real email address! (The same one you used to sign up for GitHub.com.) Don't delete the quotes. They're important.
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
7. TextMate
  1. Click https://api.textmate.org/downloads/release
    - This downloads a "ZIP" file into your **Downloads** folder.
    - Unzip the file to reveal the TextMate application (Its icon is a bright purple/pink flower).  
    ![](http://cl.ly/ZPhF/2015-01-22%2015_03_33.gif)
    - Drag that application into your **Applications** folder.  
    ![](http://cl.ly/ZQNx/2015-01-22%2015_03_50.gif)
  2. Open **TextMate**
    - Go to the Preferences. (It might ask for access to your contacts, which is fine to allow or deny.)
    - In Preferences, go to the 'Terminal' tab and click the 'Install' button.
  3. Configuration
    - Into **Terminal**: `mate ~/.tm_properties` - This will open up a blank document in TextMate.
    - Copy/Paste all of the content from [this link](https://raw.githubusercontent.com/omahacodeschool/laptop/master/tm_properties_example) into that blank document.
    - Type **Command + S** to save the document, and then close the document.
7. Git Setup
  1. `git config --global core.editor "mate -w"`
  2. `git config --global user.name "Your Name"` - Use your real name!
  3. `git config --global user.email "your_email@example.com"` - Use the email address that you used to sign up for GitHub.com.
  4. `git config --global core.excludesfile ~/.gitignore`
7. Gems
  1. `mate ~/.gemrc`
    - Into the blank document that just opened up, paste the following:
    `gem: --no-rdoc --no-ri`
    - Then save the file and close it.
  2. Quit/Restart **Terminal**.
  3. `gem install jekyll`
  4. `gem install rails`
    - If it asks whether you want to "overwrite some executables", you do.
  5. `gem install pry`
  6. `gem install bundler`
8. `rbenv rehash` (and then quit/restart **Terminal**)
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
  - Back in **Terminal**, press **Control + C** to "cancel" (exit) the Rails program.
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
