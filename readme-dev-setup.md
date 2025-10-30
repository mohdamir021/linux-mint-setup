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

### Installing `Oh My Zsh`

You can refer to `Oh My Zsh` official web page [here](https://ohmyz.sh/) or head over to read the documentation [here](https://github.com/ohmyzsh/ohmyzsh/wiki) for more detailed installation breakdown.

For my personal Linux Mint 22 setup, run the following:

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

You will be prompted to change your default shell to zsh. Enter `Y` to confirm your changes.

If somehow you see you don't have terminal startup to zsh, refer to the steps of setting up zsh here where you set zsh as the default shell, or search up how to make your default shell as the zsh, or making your terminal run custom command instead of the shell to the following:
```
/usr/bin/zsh
```

After that, install the following plugins for `Oh My Zsh with` the following commands and `Powerlevel10k`:

#### Zsh-auto Suggestions
```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

#### Zsh-Syntax-Highlighting
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

### Powerlevel10k
```
git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
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

Lastly, setup `Powerlevel10k` theme in `~/.zshrc` again and go the line `ZSH_THEME=robbyrussell` or similar, and set the value to `powerlevel10k/powerlevel10k` as follows:
```
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Then restart shell or just run `source ~/.zshrc`.

Setup Powerlevel10k however you like.

If you somehow ever want to reconfigure `Powerlevel10k`, use the following command:
```
p10k configure
```

And now you're done with your terminal setup.


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

3. If you're on Linux, you might encounter something like this:

    ![gnome error](/assets/gnome-error.png)

    If so, then consider the following guide [here](https://forums.linuxmint.com/viewtopic.php?t=439152).

    In short, basically, the keyrings aren't auto starting. If you open Seahorse (aka Passwords and Keys), and it doesn't have "Passwords" or "Certificates" on the left, or "Keys" for that matter, then GNOME Keyring is not launching at startup.
    
    Go to `Menu > Preferences > Startup Applications`

    And add a new startup application, and enter the following dialogue:
    ```
    Name: Secrets Key Agent (or whatever you want)
    Command: /usr/bin/gnome-keyring-daemon --start --components=ssh,secrets,pkcs11
    Description: GNOME Keyring Secrets Agent (or whatever you want)
    ```

    Or you may edit what's already there which is called `SSH Key Agent` and just add `,secrets,pkcs11` to the end of command at `--components=ssh` so it looks more like the following:
    ```
    /usr/bin/gnome-keyring-daemon --start --components=ssh,secrets,pkcs11
    ```

    Be sure to restart your device as well, to see the changes.

    

## Docker Setup

You can read the full website guide for installing Docker in Linux Mint 22 [here](https://linuxiac.com/how-to-install-docker-on-linux-mint-22/).

It's recommended you read it and understand, and you can't blindly paste any command or script you found on the internet.

Either way here's a breakdown of what you need to do, if you prefer to skip reading it.

```
sudo apt update
sudo apt install apt-transport-https ca-certificates curl gnupg
```

Add run the following, to add Docker's Official GPG Key.
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker.gpg
```
As this is the security feature, that ensures that the software installed is authentic

Now, add the repo:
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu noble stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Then run the following to refresh the package list:
```
sudo apt update
```

You should see no error, and you may proceed to run the following to install docker.
```
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

This installs the following Docker components:
 - docker-ce: The Docker engine itself.
 - docker-ce-cli: A command line tool that lets you talk to the Docker daemon.
 - containerd.io: A container runtime that manages the container’s lifecycle.
 - docker-buildx-plugin: This extension for Docker enhances the capabilities of building images, mainly focusing on multi-platform builds.
 - docker-compose-plugin: A configuration management plugin that helps manage multi-container Docker applications using a single YAML file.

That’s all! Docker should now be installed, service enabled, and set to start automatically on boot. In addition, check its status using the command below to confirm that everything is as expected:
```
sudo systemctl is-active docker # Expected output: active
```

After that, test the following either with:
```
sudo docker run hello-world
```
or
```
docker run -d -p 8080:80 docker/welcome-to-docker
```

Now, you may encounter some issues where you need to `sudo` every docker command.

If so, you may need to enable non-root users to run docker commands.

You can do this with the following commands:
```
sudo usermod -aG docker ${USER}  # add your user to the “docker” group
newgrp docker                    # activate the changes to the group
```

You can now run Docker commands without `sudo` but it is important to note that:

- this solution will work only for your current terminal session,
- if you close the terminal, you will either have to execute the `newgrp` command above again or prefix docker commands with sudo, and,

To make this change last permanently, just restart your Mint system.

By now, you are done with the terminal setup for Docker.


If you want a to manage docker as I do as well, download the deb package by going through the Docker Page for installing Docker Desktop in Linux [here](https://docs.docker.com/desktop/setup/install/linux/ubuntu/).

