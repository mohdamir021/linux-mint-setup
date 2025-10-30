Ctrl+Shift+V To Preview in VSCode

# Software Development Setup in Linux Mint

## Dependencies

Verify if you have this installed first:
```
git wget curl xclip
```

Usually in Linux Mint, you already have `wget` and `curl` you only need to run install `git` and `xclip`.

## Personal Setup with ZSH and Oh My Zsh

### Setup Zsh

To confirm whether you have Zsh or not, run:
```
zsh --version # Expected output: zsh 5.0.8 or more recent
```

Assuming if you don't have Zsh installed, run the following and confirm previous steps:
```
apt install zsh # or sudo apt install zsh
```

If you're planning to install `Oh My Zsh` either way, you can skip the following and head over to `Installing Oh My Zsh`.

Note that Zsh should be the default, and run the following to confirm:
```
echo $SHELL # Expected output: /usr/bin/zsh or similar
```

If you don't see the expected output. That means you it's not your default shell and you have to make default manually.

To make it your default shell, run the following:
```
chsh -s $(which zsh) # or use sudo if you don't have permission
```

If needed, restart your computer or run `/bin/zsh` to see the new shell changes.

### Installing Oh My Zsh

You can refer to Oh My Zsh official web page [here](https://ohmyz.sh/) or head over to read the documentation [here](https://github.com/ohmyzsh/ohmyzsh/wiki) for more detailed installation breakdown.

For my personal Linux Mint 22 setup, run the following:

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

You will be prompted to change your default shell to zsh. Enter `Y` to confirm your changes.

If somehow you see you don't have terminal startup to zsh, refer to the steps of setting up zsh here where you set zsh as the default shell, or search up how to make your default shell as the zsh, or making your terminal run custom command instead of the shell to the following:
```
/usr/bin/zsh
```

After that, install the following plugins for Oh My Zsh with the following commands:

Zsh-auto Suggestions
```
git clone github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

Zsh-Syntax-Highlighting
```
git clone github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

After that, edit `~/.zshrc` using `nano` or any text-editor. It's preferable to use `nano` instead, and run the following:

```
nano ~/.zshrc
```

Head to following line `plugins=(git ...)`. And inside the parenthesis `()`
add `zsh-autosuggestions` and `zsh-syntax-highlighting`.

Your line should be as follows:
```
plugins=(git ... zsh-autosuggestions zsh-syntax-highlighting)
```

Lastly, setup `Powerlevel10k` theme. Run the following command to get it:
```
git clone github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```

Then open `~/.zshrc` again and go the line `ZSH_THEME=robbyrussell` or similar, and set the value to `powerlevel10k/powerlevel10k` as follows:
```
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Then restart shell or just run `source ~/.zshrc`.

Setup Powerlevel10k however you like.

If you somehow ever want to reconfigure `Powerlevel10k`, use the following command:
```
p10k configure
```


## Install Visual Studio Code

1. Get Linux download and install it directly

2. Optionally you want to turn off telemetry if you want by setting up this settings:

```
{
    "redhat.telemetry.enabled": false,
    "telemetry.telemetryLevel": "off",
    "telemetry.feedback.enabled": false,
    "telemetry.editStats.enabled": false,
    "git.autofetch": true
}
```

## Docker Setup

You can read the full website guide for installing Docker in Linux Mint 22 [here](https://linuxiac.com/how-to-install-docker-on-linux-mint-22/).

If you want a to manage docker as I do as well, download the deb package by going through the Docker Page for installing Docker Desktop in Linux [here](https://docs.docker.com/desktop/setup/install/linux/ubuntu/).

