# boot2docker-ntp

Re-sync boot2docker's system clock.

### Problem:

Boot2Docker's internal clock falls out of sync with your Mac's system clock.

Friendly #docker dev [@cpuguy83](https://github.com/cpuguy83) explained it thus:

"That's the problem. Since it's running in virtualbox, when your system is sleeping or whatever, it can't re-sync the time. The issue is this... ntp is already running in boot2docker, but do to sleep/resume issues with virtualbox, the time gets too far out of sync for ntp to correct."

### Solution:

`boot2docker-ntp`!


### Installation

Clone the repo.

```sh
$ git clone git@github.com:beechnut/boot2docker-ntp.git
```

Copy the boot2docker-ntp script to someplace in your `PATH`. I keep mine in `/usr/local/bin`.

If you don't know about path, run

```sh
$ echo $PATH
```

and put the script in one of the folders listed there.

Change the permissions so the script is executable. I use `$ chmod 751 /usr/local/bin/boot2docker-ntp`.


### Usage

```sh
$ boot2docker-ntp
```

will update the time on your Boot2Docker VM by downloading and running [cpuguy83/ntpdate](https://registry.hub.docker.com/u/cpuguy83/ntpdate/).

If you want to use a different NTP time server from the default (0.pool.ntp.org), you can specify it with the `-s` flag, for example:

```sh
$ boot2docker-ntp -s 1.pool.ntp.org
```