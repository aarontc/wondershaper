# Wonder Shaper 1.3.1

## About

`wondershaper` is an old helper script that allows users to limit/shape the bandwidth of one or more network adapters.

It does so by using iproute2 `tc` command, but greatly simplifies its operation.

The original version was first released by bert hubert in 2002.  See AUTHORS for all the credits.

From version 1.2, the supposedly missing command line interface was added.

From version 1.3, the HTB queuing was used instead of CBQ, allowing better bandwidth management on high speed links (>10 Mbps).

The original README is a rather lengthy document and saved under README-1.1a.txt, for those who'd like some more background information.

Except any notes on operation in this document is considered up-to-date.

**Currently attempting to add new features to the old script, see CHANGELOG for details.**

Licensed under the GNU General Public License v2

## Installation

You can run `wondershaper` (as any user with sufficient permissions) without installation.

However if you want to install the script onto your system you can simply run:

    sudo make install

## Usage

    wondershaper [-hcs] [-a <adapter>] [-du <rate>] [-fg <rate>]

The following command line options are allowed:

- `-h` Display help

- `-a <adapter>` Set the adpter

- `-d <rate>` Set maximum download rate (in kbps)

- `-u <rate>` Set maximum upload rate (in kbps)

- `-f <rate>` **EXPERIMENTAL** Set maximum download rate (in kBps)

- `-g <rate>` **EXPERIMENTAL** Set maximum upload rate (in kBps)

- `-p` Use the presets in /etc/conf.d/wondershaper.conf

- `-c` Clear the limits from adapter

- `-s` Show the current status of adapter

The different modes are:

    wondershaper -a <adapter> -d <rate> -u <rate>

    wondershaper -a <adapter> -f <rate> -g <rate>

    wondershaper -c -a <adapter>

    wondershaper -s -a <adapter>

Some examples:

    wondershaper -a eth0 -d 94000 -u 94000 # can be used on a 100Mbps link

    wondershaper -c -a eth0

    wondershaper -a wlp3s0f0 -f 130 -g 100 # can accept kBps values
