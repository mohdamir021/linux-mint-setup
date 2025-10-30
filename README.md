Ctrl+Shift+V To Preview in VSCode

# Linux Mint Setup

This is a small detailed guide on my personal Linux mint setup for my day-to-day work, personal usage, and for software development. As of writing this, I'm currently on Linux Mint 22.2 'Zara' - Cinnamon Edition. I switched from Windows 11 to Linux for various reasons but I'm going to outline what actually drives me and take a leap of faith to jump straight away to Linux.

1. Simple, straight-forward and freedom. I love Windows for what it is, but recently, I started to notice that Windows especially Windows 11, started to bloat so much and it seems suspicious to me that it lag so much and heat up easily. Although, there's a way to remove that much bloat, I still feel that the more I use it, the more things happens and I don't know what's going on. And since I already have learnt about the existance of Linux Mint and have things to sacrifice.

2. The curiosity to learn Linux first-hand. I found out through the years that most servers and computers today are running Linux. Since I was curious as well, I want to learn it but I can't sacrifice my OS for terminal. That's when I found out there's a bunch of called Linux Distributions or Linux Distros, which is basically a Linux Desktop Environment that can provide a GUI for the user to use Linux. Linux Mint, is one of the easiest to migrate to, from Windows, if you have no prior experience to Linux. There's WSL for Window, but I don't think the learning curve for it is for me, since I want to experience Linux first-hand.

3. Open source alternatives. Will explain here later ... trust

4. The mindset. Simply having a mindset change had drive me to hop into Linux, like having to want to know every single thing that's happening to my computers, the developer experience, control you can enforce, "you own the hardware that you buy" type shi.

### Important Note

(Tell windows user what to take notes of, be aware, and warned)


# Before The Setup

Once you, fully understand what you're getting into, time to dive into the first step of getting Linux in your device.

1. Prepare one (Sacrificial / Empty) USB drive (Min: 8GB or maybe 16GB).

2. Get Ventoy (For storing multiple Linux Distros ISO files).

3. Flash Ventoy either using BelenaEtcher or Rufus (I use Rufus in this case).

4. Download the Linux Distros' ISO files and just copy/paste or move it to the flashed drive.

5. Setup in UEFI setup (Remove the B1tl0ck3r as well).


# The Setup

1. Turn on Bootloader and select the USB drive.


# Desktop / Workspace Setup

## Terminal Installation
- git
- wget (need to verify)
- curl (need to verify)
- xclip
- wipe
- nvim

### Important Note

To set your Git username and email, use the following commands in your terminal: 
```
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

A detailed setup for the listed below are [here](/readme-dev-setup.md):
- zsh to oh my zsh
- docker

## Backup
- Mostly 1 or 2 batch weekly.

## App Checklist
- XFCE Terminal
- Steam + Qt Proton
- VSCode Local Install
- Gimp
- Audacity
- Kdenlive
- OBS Studio
- -Tube
- /Flex
- Qbt
- _|_ Browser


## Extensions
- Blur Cinnamon by klangman
- Cinnamon Dynamic Wallpaper by TobiZog

