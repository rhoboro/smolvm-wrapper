# smolvm-wrapper

```bash
ln -sf ~/go/src/github.com/rhoboro/smolvm-wrapper/smol ~/.sd/smol
```

```bash
smol create myvm -p 8080:8080 -p 2222:22
smol mount myvm --volume /path/to/app:/root/app
smol clone myvm --repo git@github.com:org/repo.git
smolvm machine exec -it --name myvm -w /root/app -- docker compose up
smol shell myvm
/ # mise use uv ty
/ # uv --help
^D

zed ssh://myvm.smolvm:2222/root/app
```

```bash
# ~/.ssh/config
Host *.smolvm
    User root
    HostName 127.0.0.1
    IdentityFile ~/.ssh/id_smolvm
    IdentitiesOnly yes
    StrictHostKeyChecking no
    UserKnownHostsFile /dev/null
```

