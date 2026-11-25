# SSH keys and config

```bash
ssh-keygen -t ed25519 -C "hema@laptop"      # create key pair
ssh-copy-id user@server                     # install public key on a server
ssh -T git@github.com                       # test GitHub auth
```

`~/.ssh/config` saves typing:

```text
Host prod
    HostName 203.0.113.10
    User ubuntu
    IdentityFile ~/.ssh/id_ed25519
    Port 22
```

Now `ssh prod` works, and so does `scp file prod:/tmp/`.

**Port forwarding** (reach a remote DB as if local):

```bash
ssh -L 5432:localhost:5432 prod
```

**Never** share or commit the private key (the file without `.pub`).
