# Setup my Mac

## Terminal

### Rewritten in Rust

cf., https://zaiste.net/posts/shell-commands-rust/

```bash
brew install bat fd procs ripgrep hugo awscli

```

#### YTop

```bash
brew tap cjbassi/ytop
brew install ytop
```

#### EKSCTL

```bash
brew tap weaveworks/tap
brew install weaveworks/tap/eksctl
```


### iTerm2

- [color schemes](https://iterm2colorschemes.com/)

## Fish

- install [oh-my-fish](https://github.com/oh-my-fish/oh-my-fish)
- install [powerline fonts](https://github.com/powerline/fonts)
- `omf install https://github.com/blackjid/plugin-kubectl`
- `omf install https://github.com/jhillyerd/plugin-git`
- `omf install <theme-name>` (cf., [themes](https://github.com/oh-my-fish/oh-my-fish/blob/master/docs/Themes.md))

## Dock

The Dock reappears with a huge delay, but it's nice to have it discppear automatically.

Settings -> Dock & Menu Bar -> check "Automatically hide and show the Dock"

```bash
defaults write com.apple.dock autohide-delay -float 0.005; killall Dock
```

To reset to the default:
```bash
defaults write com.apple.dock autohide-delay; killall Dock
```

## Karabiner-Elements

This is important for custom keymappings (like `CapsLk` -> `Esc`)

#### References

- https://techviewleo.com/configure-fish-shell-with-oh-my-fish/
- https://github.com/oh-my-fish/oh-my-fish/blob/master/docs/Themes.md

## Work

### Kubernetes

#### Get Cluster Access

The aws-iam-authenticator for M1 is too new (cf., [stackoverflow](https://stackoverflow.com/a/71319893)).
Replacing `client.authentication.k8s.io/v1alpha1` with `client.authentication.k8s.io/v1beta1` in the `KUBECONFIG` does
the trick for our "old" clusters.

#### Show Cluster on CL

With [bobthefish](https://github.com/oh-my-fish/oh-my-fish/blob/master/docs/Themes.md#bobthefish) theme, set
`set -g theme_display_k8s_context yes`
