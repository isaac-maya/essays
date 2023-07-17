---
title: "Advanced GREP"
date: 2023-07-17T13:55:28-06:00
draft: false
---

![Retro PC Picasso Style](../../images/advanced_ssh.png)

## 1. Remote Command Execution

Run command on a remote server without logging in. 

```bash
ssh username@remote_server 'ls /tmp'
```

## 2. SSH with a Specific Private Key

Specify which private key to use.

```bash
ssh -i ~/.ssh/id_rsa_specific username@remote_server
```

## 3. Jump Host

SSH into machine A, and from there into machine B.

```bash
ssh -J username@machineA username@machineB
```

## 4. Tunneling/Port Forwarding

Forward a port on your local machine to a port on a remote server. For example, access a remote database as if it was local.

```bash
ssh -L 3306:localhost:3306 username@remote_server
```

## 5. SSH Config File

Create an SSH config file (~/.ssh/config) to simplify log in.

```bash
Host server1
    HostName server1.com
    User username1
    Port 2222
    IdentityFile ~/.ssh/id_rsa_server1
```
    Now, to SSH run `ssh server1`

## 6. Creating an SSH SOCKS Proxy for Secure Browsing

You can set up a SOCKS proxy on a given port using SSH. This tunnel can encrypt and redirect your web traffic through the remote machine when you configure your web browser to use it:

    ```bash
    ssh -D 8080 -C -q -N username@remote_server
    ```

    `-D 8080` sets up a SOCKS proxy on port 8080.
    `-C` compresses the data before sending it.
    `-q` makes the operation quiet.
    `-N` tells SSH that no command will be sent once the tunnel is up.

    After running this, you can set your browser's SOCKS proxy to `localhost` with port `8080` and your browsing will be encrypted and tunneled.

## 7. Automate SSH Login with SSH Key-Pair

For scripting purposes, it's often beneficial to automate the SSH login process. You can do this by generating an SSH key-pair and copying the public key to the remote server. 

    First, generate a new SSH key-pair:

```bash
ssh-keygen -t rsa
```

    Then, copy the public key to the remote server:

```bash
ssh-copy-id username@remote_server
```

    Now, you can login to the remote server without entering a password.

## 8. Mount Remote Directories

SSHFS (SSH File System) allows you to mount remote filesystems over SSH, letting you interact with remote files as though they were on your local machine.

```bash
sshfs username@remote_server:/remote/directory/path /local/mount/point
```

    To unmount the directory when you're done, you can use:

```bash
fusermount -u /local/mount/point
```

