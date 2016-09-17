# Startup Systems Virtual Machine

A common VM for the class.

## Goals

* We don't want to waste time troubleshooting differing configuration for students' machines.
* We cannot assume everyone will run a UNIX box (Linux, OSX, etc.).
* We should make work doable locally as much as we can, for convenience reasons.

The idea is to have students run a VM on whatever their environment is, i.e. Windows, OSX or Linux.

## Installation

You will want to have a good internet connection for these. This should only need to be done once.

1. If you’re on Windows, try the following, in order (find the first one that works for you):
    1. [cmder](http://cmder.net/)
    1. [conemu](https://conemu.github.io/)
    1. [cygwin](https://cygwin.com/)
1. [Install VirtualBox](https://www.virtualbox.org/wiki/Downloads) (5.1.2 or later).
1. [Install Vagrant](https://www.vagrantup.com/downloads.html).
1. Download (or `git clone`) this repository to your computer.
    * Put it wherever you keep your other projects—we recommend a `startup-systems` folder.
1. Run the one-time setup from a terminal (if on Windows, make sure you use the terminal you installed above going forward, e.g. cmder):

    ```bash
    cd path/to/this/repository/
    vagrant up
    ```

1. The VM should now be running. You can verify this with `vagrant status`.

## Usage

`host>` means you run the command on your host computer, `guest>` means it should be run within the VM. Within the VM, the terminal prompt will actually look something like `vagrant@vagrant-ubuntu-trusty-64:~$`.

```bash
host> cd path/to/this/repository/

# Start the VM (if it isn't already running).
host> vagrant up

# Connect to the VM.
host> vagrant ssh
# You are now inside the guest VM.
guest>

# Go back to your host.
guest> exit

# To stop the guest VM (and recover CPU and memory resources on your host):
host> vagrant suspend
```

## Assignments

TODO

## Troubleshooting

If you’re on Windows and you get a **BIOS error**, you may need to change a setting on your machine (in VirtualBox, Control Panel, and/or the BIOS itself) to allow virtual machines to run. Google the error and the make and model of your computer (e.g. `"VT-x is disabled in the BIOS for both all CPU modes" sony vaio`) to find how to enable virtualization. The problem is often that Intel Virtualization Technology needs to be [enabled](http://www.howtogeek.com/213795/how-to-enable-intel-vt-x-in-your-computers-bios-or-uefi-firmware/) in your BIOS settings.

## Guest (the VM) vs Host (your existing machine)

The "host machine" is the operating system that your computer is running directly (likely Windows or OSX), whereas the “virtual machine” is the one running through Vagrant+VirtualBox, which will be [Ubuntu](http://www.ubuntu.com/desktop) (Linux).

Vagrant lets you share folder between guest and host via the /vagrant folder by default. From the guest VM, you can write to the host machine under /vagrant. In other words, you can open the `Building-Startup-Systems` directory in your editor on your computer, and any added/changed files will appear in the `/vagrant` directory within the virtual machine.