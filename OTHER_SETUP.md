# Other Setup

You can do the following while the main Laptop installation script is running.

1. Settings
  1. Enable unverified software installs (**Settings > Security**).  
  ![](http://cl.ly/ZPqP/Screen%20Shot%202015-01-22%20at%201.20.46%20PM.png)
  2. Speed up keyboard settings (**Settings > Keyboard**)  
  ![](http://cl.ly/ZPnC/Screen%20Shot%202015-01-22%20at%201.21.45%20PM.png)
  3. Enable tap-for-click (**Settings > Trackpad**).  
  ![](http://cl.ly/ZPnC/Screen%20Shot%202015-01-22%20at%201.21.45%20PM.png)
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
  4. `gem install rails -v 3.2.21`
    - If it asks whether you want to "overwrite some executables", you do.
  5. `gem install pry`
  6. `gem install bundler`
8. `rbenv rehash` (and then quit/restart **Terminal**)
9. Testing Rails
  - `cd ~`
  - `mkdir Code`
  - `cd Code`
  - `rails new temp -d postgresql`
  - `cd temp`
  - `mate .` - This will open the entire Rails project in TextMate.
    - In TextMate, click the arrow next to 'config' to reveal its files. Then click the icon next to 'database.yml' to open that file.  
    ![](http://cl.ly/ZQLk/2015-01-22%2015_20_58.gif)
    - In that file...
      - find any lines with `username` or `password` as the key, and comment those lines out.
      - find any lines with `host` or `port` as the key, and **uncomment** them.
    - Save the file.
  - Back in **Terminal**, type `rails server`.
    - Go to <http://localhost:3000>. You should be welcomed to a new Rails project.
  - Back in **Terminal** again, press **Control + C** to "cancel" (exit) the Rails program.
  - Then type...
    - `git init`
    - `git add .`
    - `git commit -m "Test application"`
    - `heroku create`
    - `heroku addons:add heroku-postgresql:dev`
    - `git push heroku master`
      - If there are no errors, you're done!