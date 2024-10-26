# Basics
    Install VSCode, Python, Git, Git LFS, Docker
    Have E-mail Address, Phone Number, Credit Card, Password Manager :P
# Basic VS Code Keyboard Shortcuts
    Ctrl+K, Ctrl+S to open Keyboard Shortcuts
    Ctrl+Shift+E to bring up Files in VS Code
    Ctrl+Shift+F/H to bring up find/replace in files (The 2nd Source Control ... has many git commands)
    Ctrl+Shift+G to bring up github commit/graph/create pull request
    Ctrl+Shift+X to bring up extensions
    Alt+Z Toggle Text Wrapping (Helpful if you are scrolling left and right)
# Installing Extensions:
    Markdown
    Python
        PyLance
        Flake8
        Jupyter
        ?Markdown ALl in One?
    Docker
    Dev Containers
    Remote SSH
    GitHub Copilot (Make sure to shut off training)
        GitHub Copilot Chat
    GitHub Pull Requests
        ?GitHub Actions? Maybe autoinstalled.
    Code Spell Checker
    Optional
# Git Privacy and SSH things
    Goto https://github.com/settings/emails and check "Keep my email addresses private" & "Block command line pushes that expose my email"
        https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address
    Create SSH Key (ssh-keygen -t ed25519 -C "your_email@example.com")
        Put the public key in at https://github.com/settings/keys
        Extra Doc Refence:
            - https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
            - https://docs.github.com/en/authentication/connecting-to-github-with-ssh
## Git Config
    git config --global user.email your-no-reply-email
    git config --global user.name your-name
    git config --global url.ssh://git@github.com/.insteadOf https://github.com/
    git config --global rerere.enabled true
    git config --global branch.sort -committerdate
    git config --global submodule.recurse true
    git config --global status.submoduleSummary true
    git config --global diff.submodule log
    git config --global core.editor "code --wait"
    git config --global core.fscache=true
    git config --global color.interactive=true
    git config --global color.ui=auto
    More info https://jvns.ca/blog/2024/02/16/popular-git-config-options/
# GitHub Good to Knows
    Basically impossible to remove secrets from github repository besides deleting it, all it's forks, and maybe more.
        This says it can be done, but it isn't accurate: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository
            https://stackoverflow.com/questions/68825239/does-github-save-all-commits-ever-pushed-to-remote
    