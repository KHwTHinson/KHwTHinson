# Setup the package environment without admin right
* The below setup is built on mac environment (M1)
* The whole idea is to utilize `homebrew` as package manager and build it in the directory not requiring admin right. Then export the path to make it work.

## Step by step guide
1. Create a path to store the brew packages to be downloaded.
>```
>cd ~/Desktop
>```

2. Follow the official documentation to build the packages.
>```
>mkdir homebrew && curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew
>```

>```
>eval "$(homebrew/bin/brew shellenv)"
>brew update --force --quiet
>chmod -R go-w "$(brew --prefix)/share/zsh"
>```

3. Go to the shell profile script and open `nano` editor.
* For example here we use the `bash` shell the most, so adding it to the path of `bash shell`
>```
>cd ~
>nano .bash_profile
>```

4. Find the sapce below, and paste the path below (if you have anaconda download, it is after `# <<< conda initialize <<<`)
>```
>export PATH="/Users/SIDANWhatever/Desktop/homebrew/bin:$PATH"
>```
* Please replace `SIDANWhatever` with your own user name.

The whole `.bash_profile` would look like this:
>```
># >>> conda initialize >>>
># !! Contents within this block are managed by 'conda init' !!
>__conda_setup="$('/opt/anaconda3/bin/conda' 'shell.bash' 'hook' $
>if [ $? -eq 0 ]; then
>    eval "$__conda_setup"
>else
>    if [ -f "/opt/anaconda3/etc/profile.d/conda.sh" ]; then
>        . "/opt/anaconda3/etc/profile.d/conda.sh"
>    else
>        export PATH="/opt/anaconda3/bin:$PATH"
>    fi
>fi
>unset __conda_setup
># <<< conda initialize <<<
>
>export PATH="/Users/SIDANWhatever/Desktop/homebrew/bin:$PATH
>```

* Side note: for any other path issue, you can always do something similar above by locating the executable path (e.g. the `brew` executable resides in `/Users/SIDANWhatever/Desktop/homebrew/bin` this path so we do the above)

5. Open a new terminal then see the version
>```
>brew --version
>```
* Then you can always use `brew install` to manage the packages.

6. Enjoy!


