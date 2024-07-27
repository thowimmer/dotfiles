# My dotfiles managed by chezmoi

## Installation
1. Install brew as non-root (see [instructions](https://docs.brew.sh/Installation#untar-anywhere-unsupported])
    * `cd ~`
    * `mkdir .homebrew && curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip-components 1 -C .homebrew`
    * eval "$(.homebrew/bin/brew shellenv)"
    * brew update --force --quiet
    * chmod -R go-w "$(brew --prefix)/share/zsh"
2. Install chezmoi using brew 
    * `brew install chezmoi`
3. Init chezmoich
    * `chezmoi state reset`
    * `chezmoi state delete-bucket --bucket=entryState`
    * `chezmoi state delete-bucket --bucket=scriptState`
    * `chezmoi init`
4. Change to chezmoi dir and remove all content
    * `chezmoi cd`
    * `find . -name . -o -prune -exec rm -rf -- {} +`
5. Checkout chezmoi repo into current directory
    * git clone https://github.com/thowimmer/dotfiles .
6. Configure .chezmoidata.toml
    * `touch ./home/.chezmoidata.toml`
    * Configuration:
    ```
    gitEmail = "<EMail for Git>"
    gitName = "<Name for Git>"
    gitSigningKey = "<Signingkey for Git>"
    isPriviledged = false
    ```
7. Apply config
    * `chezmoi apply -v`