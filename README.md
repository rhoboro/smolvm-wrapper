# smolvm-wrapper

A tiny personal wrapper script for [smolvm](https://github.com/smol-machines/smolvm)

## Setup

```bash
ln -sf ${PWD}/smol ${HOME}/.local/bin/smol

# Add to ~/.ssh/config
Host *.smolvm
    User root
    HostName 127.0.0.1
    IdentityFile ~/.ssh/id_smolvm
    IdentitiesOnly yes
    StrictHostKeyChecking no
    UserKnownHostsFile /dev/null

export SMOL_GIT_USER_NAME=<your name>
export SMOL_GIT_USER_EMAIL=<your email address>
```

## How to use

```bash
$ smol
usage: smol {clone,create,mount,remove,restart,rm,setup,shell,stop} name
smol: error: the following arguments are required: action, name
```

```bash
smol create myvm -p 8080:8080 -p 2222:22

# git clone
smol clone myvm --repo git@github.com:org/repo.git --dist /root/app

# Or mount a local dir
smol stop myvm
smol mount myvm --volume /path/to/app:/root/app
smol restart myvm

# Docker and Docker Compose are available.
smolvm machine exec -it --name myvm -w /root/app -- docker compose up

# Mise is pre-installed.
smol shell myvm
/ # mise use uv ty
/ # uv --help
^D

# Edit files via SSH
zed ssh://myvm.smolvm:2222/root/app

# Cleanup
smol rm myvm -f
```

