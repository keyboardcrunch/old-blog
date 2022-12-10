---
title: "VMRay Guest Performance"
date: 2022-11-17T16:07:01-06:00
draft: false

# HelloFriend Specific
#hideReadMore: false
#cover = "img/default.jpg"
#description = "description"
---

## Warning
At this time VMRay doesn't officially support changing the CPU, they don't seem to plan on supporting it, and they won't help you to get it working.
As of release 4.7 this is not working, you can get a VM guest to boot (and maybe even snapshot, though bootstrap exe may need to be triggered manually) but when you attempt to run an analysis (which boots from a snapshot) it'll fail. The failure makes it look like a driver issue, but I haven't found a workaround and lost interest after working with support.

## The Original Post

I recently had the privilege to work with VMRay, a sandbox and malware analysis platform which uses qemu for virtualization, but I quickly noticed that the default settings used for creating virtual machines was grossly underwhelming. All of the VMs were running with a single core, and as far as I know each one of these machines was built without passing any custom qemu arguments during the creation process.

It appears that the default is `-smp 1`, meaning one vCPU socket/core is assigned. To view how many CPU cores your host machine has available you can run `nproc` to get the value. So to have a 4 core system we just need to configure the guest to use the qemu argument `-smp 4`.

If you're creating a new virtual machine then VMRay provides some configuration options with `vm_setup.py` most of it is hardware emulation, disk and memory size, with the final option to pass some qemu arguments. If you're trying increase CPU resources on the machines after the fact you follow the below steps, in our example we'll tell VMRay to launch the machine with 2 sockets and 4 cores (note that if you do define socket/cores then you need to use the maxcpus value as well).

1. `sudo /opt/vmray/bin/vm_setup.py`
2. Select 2, VM Operations
3. Select 8, Change hardware info of existing VM
4. Select your virtual machine
5. Select 10, Miscellaneous settings
6. Select 1, Additional QEMU command line (current value: )
7. Enter `-smp 4,cores=4,sockets=2,threads=1,maxcpus=8`

Your guests will now have much more resources, and the core count will reflect in the guest. Now, this may break some of the virtualization countermeasures but I'd rather have a usable analysis machine. You can read more about this setting in the [qemu manpage](https://www.qemu.org/docs/master/system/qemu-manpage.html).