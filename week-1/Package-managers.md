https://hackmd.io/k_PidO0tRHGwtLWIbsWnVA?both

## Customising Your Command Line (for Mac)

### Aesthetic Changes

Terminal -> Preferences -> Profiles 

You can customise:
background colour
text colour
text-rendering options
text size
typeface
cursor type
selection colour
ANSI colours (used when a Terminal command displays coloured output)

There are pre-existing profiles, and you can also make and customise your own.

Click the "default" button to set a profile as your default.

To open Terminal windows in a specific profile, use Shell -> New Window.

### Functional Changes

You can customise your Mac Terminal, for example to display your current git branch and status.

If .bash_profile does not already exist, create it. This is the file that holds a variety of your preferences. There are various sources on the internet that give you examples of snippets of code that you can copy and save as .bash_profile for the purposes of fulfilling various functions. For example, you can customize the default command line prompt to show you different information.

There are also resources such as ezprompt.net, which generates code for you - all you have to do is choose which information you want in your prompt.

If you want to do all this yourself, you can also find a list of available options and their corresponding code, such as:
username - \u
hostname - \h
shell - \s
current directory - \W

Follow these steps:
1. make sure you're in your home directory
2. create bash profile (type "nano .bash_profile")
3. add this line of code - export PS1=" "
4. add commands such as those listed above in between the quotes
5. save the file

You can also achieve some functional changes in a more user-friendly way by downloading a new command line interface with more features. Alternatives to Terminal include iTerm2, which lets you split your session into multiple panes, Hyper, which supports JS, HTML and CSS, Terminator, which gives you the option of different tabs and panes and Alacritty, which is designed for better performance.

<br><br>

## Command line research 
### How to customise your Command Line.

- There are many plugins and tools available to get this job done easily and quickly. 
 
- However, we still can do some basic customization:

1) you can customize and change the BASH prompt as the way you want by changing the value of PS1 environment variable

(PS1  is the primary prompt which is displayed before each command)

1) Modify your user name and hostname;
there is a specif list of command to follow that can be easily found on (obviusly) goole.
Check out this:
https://www.ostechnix.com/hide-modify-usernamelocalhost-part-terminal/

2) Display date in BASH prompt:

- you can display date with your username and hostname in the BASH prompt: 
~/.bashrc file.

- Date and time in 12 hour format in BASH prompt:
export PS1="\u@\h>\d\@ "

- Date and 12 hour time hh:mm:ss format:
export PS1="\u@\h>\d\T "

- Date and 24 hour time:
export PS1="\u@\h>\d\A "

- Date and 24 hour hh:mm:ss format:
export PS1="\u@\h>\d\t "

3) You can hide your username too:
Edit your “~/.bashrc” file:

$ vi ~/.bashrc
Add the following at the end:

PS1="\W> "
Type :wq to save and close the file.

Then, run the following command to take effect the changes.

$ source ~/.bashrc

4) Change colors:
You can enhance the foreground (text) and background color of BASH prompt’s elements by adding some code to the ~/.bashrc file.

- For example, to change the foreground color of all texts to Red, add the following code:
export PS1="\u@\[\e[31m\]\h\[\e[m\] "

- for example, to change the backgrounc color we can add:
export PS1="\u@\[\e[31;46m\]\h\[\e[m\] "

5) We can add an emo by placing the following code in the ~/.bashrc file:

PS1="\W 🔥 >"

<br><br>

# Install using a package manager

## What is a package manager?

A package manager has a similar purpose to a mobile app store - it will retrieve the piece of software you tell it to download. 

You also could compare a package manager to a librarian that fetches a specific book (the package) form the library (the software repository).

If you tell the package manager to install software it will automatically download the appropriate package from its configured software repositories. 

You can install the software and set it up without you having to click through installation wizards or hunt down .exe files on websites (like on Windows).

## npm and Yarn
npm and Yarn are two well-known JavaScript package managers. 

npm is the Javascript node package manager. It is the default method for managing packages in the Node.

Yarn was developed by Facebook in attempt to resolve some of npm’s shortcomings. Yarn isn’t technically a replacement for npm since it relies on modules from the npm registry. Think of Yarn as a new installer that still relies upon the same npm structure. 

## What is a software repository?

Software repositories are a centralised listing of all of the available software configured for a specific system.

Repositories are essentially a collection of packages with an informative index file detailing which packages they include. Repoistories will be downloaded from a web- or a ftp-server. 

While there have been several attempts at making an attractive UI for software repositories, the vast majority of Linux users still use the command line to install packages from a software repository.

GitHub is a software repository.

## Why do I need a package manager?
* Easier to find software as it's all in one place
* Manage dependencies - make sure you and your team always have the right version of every piece of software that your project needs. 

## Example package manager commands

### APT (Linux)
Advanced Package Tool, or APT, is a free-software user interface that works with core libraries to handle the installation and removal of software on Debian, Ubuntu, and related Linux distributions.
```
$ sudo apt-get update
```
*Update package database with apt-get*
### Homebrew (mostly Mac)
Homebrew is a free and open-source software package management system that simplifies the installation of software on Apple's macOS operating system and Linux.
```
$ brew install python
```
*Install python*
### npm (Mac or Linux (or windows?))
npm (originally short for Node Package Manager) is a package manager for the JavaScript programming language
```
$ npm install react
```
*Install react*

