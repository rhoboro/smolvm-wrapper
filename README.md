# smolvm-wrapper

A small personal wrapper around [smolvm](https://github.com/smol-machines/smolvm).

## Setup

```bash
ln -sf ${PWD}/smol ${HOME}/.local/bin/smol

# Add the following to ~/.ssh/config
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

## My workflow

```bash
smol create myvm -p 8080:8080 -p 2222:22
smol clone myvm rhoboro/events
smol setup mise  # install my favorite tools such as uv
smol zed myvm  # open /root/app in zed editor via ssh
```

## Usage

```bash
$ smol
usage: smol {clone,create,edit,editor,exec,git,list,ls,mount,remove,restart,rm,setup,shell,start,stop,zed}
smol: error: the following arguments are required: action
```

```bash
smol create myvm -p 8080:8080 -p 2222:22

# git clone (repository is positional; --dest is optional)
smol clone myvm git@github.com:org/repo.git --dest /root/app

# Or mount a local directory
smol stop myvm
smol mount myvm --volume /path/to/app:/root/app
smol restart myvm

# Install Docker and start its daemon
smol setup myvm docker

# Start the daemon again after a VM restart
smol start myvm --docker

# Run Docker commands
smol exec myvm -- docker compose up

# Mise is pre-installed.
smol shell myvm
/ # mise use uv ty
/ # uv --help
^D

# Edit files via SSH
smol zed myvm

# Cleanup
smol rm myvm -f
```

