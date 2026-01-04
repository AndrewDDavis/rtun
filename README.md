# rtun

Open an SSH tunnel to a target machine through an intermediary. Facilitates opening SSH tunnels through a machine such as a DMZ or gateway.

Usage: `rtun <target> [options ...]`

Create a config file at `~/.config/rtun/rtun.conf`. The file is made of blocks
for each target, separated by blank lines. Each block begins with a target name, and is followed by configuration names and values, as:

    [targetName]
    name1 = value1
    name2 = value2

Lines beginning with `#` are treated as comments, and ignored. The following names are usually required:

- `tgtUser`: login name on the target machine
- `tgtLoc`: IP or URL of target machine
- `tgtPort`: port to access on target machine (e.g. 22=SSH, 80=HTTP)
- `lport`: port to open on local machine (an unused port above 1024)
- `tunUser`: login name on intermediary machine
- `tunLoc`: URL or IP of intermediary machine
- `tunPort`: port on intermediary machine

The tun names may be omitted for a block, to define a SOCKS tunnel.

Options:

- `-v` : verbose mode for ssh connection
- `--ssh` : initiate default ssh connection through the tunnel
- `--sshX` : initiate ssh connection with -X option
- `--sftp` : initiate default sftp connection through the tunnel
- `--sshfs` : initiate default sshfs connection through the tunnel
