## Basic scripts for booting a Devuan with Dinit

## What is this?
These files are scripts for dinit, and you can use them to boot a Devuan using Dinit.

## What is included?
This project includes any script needed to boot a Devuan with Dinit.

| Service name  | Description                                                  | Note                          |
| --------------|--------------------------------------------------------------|-------------------------------|
| boot          | First service started by dinit at boot time                  | Its start other services      |
| pseudofs      | Mounting /proc & other kernel virtual file systems           |                               |
| udevd         | Udev device (/dev) manager                                   | eudev used on Devuan          |
| udev-trigger  | Trigger udev events for already-present devices              |                               |
| udev-sttele   | Wait for the udevd childs to finish                          |                               |
| modules       | Loading kernel modules from /etc/modules                     |                               |
| cgroups       | Mounting cgroups filesystem                                  |                               |
| hostname      | Setting system hostname from /etc/hostname                   |                               |
| tmpfs         | Mounting /tmp                                                |                               |
| swap          | Mount swap partition/files                                   | NOT enabled by default!       |
| single        | Single-user mode. This just starts a shell on the console    |                               |
| fsck          | Checking filesystem's via fsck                               | Waits for mount.d [1]         |
| mount-all     | Mounting all filesystems                                     | Waits for mount.d [1]         |
| root-rw       | Remounting root (/) filesystem as read-write                 |                               |
| mount         | Internal service waits for root-rw, cgroups, pseudofs, tmpfs |                               |
| networking    | Raise network interfaces                                     | Based on sysvinit script [2]  |
| hwclock       | Seting system time from hardware clock                       |                               |
| rsyslog       | enhanced syslogd                                             | Based on sysvinit scirpt [2]  |
| loginready    | Waits for system become ready for loading ttys               |                               |
| ttys          | Console login                                                | tty1,tty2,tty3,tty4,tty5,tty6 | 

[1] Its started after cryptsetup &...
[2] Based on Debian/Devuan [Service name] sysvinit script