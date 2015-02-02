# Talk 1: Kernel Development Basics

## Presentation

### 0: Where to start?

* [Linux Foundation](http://www.linuxfoundation.org/) - sponsors the work of Linus Torvalds
* [Download kernel here](https://www.kernel.org/)
* [Lot's of interesting resources about kernel](http://kernelnewbies.org/)

### 1: Tools

* gcc
* git
* make
* vim (or some other inferior editor)

They tried to use g++ to compile the kernel, but it turned out to be serious source of inefficiencies, so they fixed on gcc.
Other tools, like Mr. Proper, are used to clean the project.
The less GUIy the more Linuxy.

### 2: Submitting patches

* must adhere to coding style
* must add valuer
* run [check patch](http://www.checkpatch.pl)
* contact maintainer and send to LKML ([the Linux Kernel Mailing List](https://lkml.org/))

[more info about submitting patches](http://kernelnewbies.org/FirstKernelPatch)

Code pushes are done via git diff mailed to the mailing list. Sounds dinosaur, but proved to work and allows for many eyeballs to review the code. If you submit patches of lesser quality, the community can give up on you and you will be waiting long time before anyone reviews your code.

Linus Torvalds must accept any change to the kernel.

### 3: Coding style

* 80 columns
* tab-indent (8 columns)
* avoid more than 3 lvls of indentation
* spaces after keywords
* ...

[more info about the coding style](https://www.kernel.org/doc/Documentation/CodingStyle)
The crazy indentation width may have to do with Linus phobia of nesting [source needed].

### 4: Writing patches

* C (with very occasional assembly sprinkled in)
* modular vs core
* GPL is preferred

[useful tutorial](http://www.linuxvoice.com/be-a-kernel-hacker/)

Because of GPL and monolitic kernel (all drivers are in it, the modular ones kinda too) many companies don't bother with writing drivers (to avoid exposing proprietary information). Other reason, of course being that user group is often much smaller. The drivers are most often developed on need base by companies using given hardware and shared with the community or offered in enterprise editions of Linux (look RedHat). Moreover, Linux do not give any architectural advantage to any hardware producer. The hardware needs to adhere to a general model and kernel will not be modified to give any company an edge, and this keeps it more open to anyone willing to write drivers.

Kernel is monolitic, what means that drivers are part of the kernel (everything loads during the boot), or if they are modules they can be loaded later (useful when it is driver for a hardware currently not in the system). Modules still are closely coupled with the kernel.
### 5: Kernel debugging

Methods:
 * printk() read with dmesg
 * filesystems:
   * debugfs - must useful, but requires the most of additional work; no limitations of values per file
   * sysfs
   * procfs

### 6: Code review

* LKML
* [Gerrit](https://code.google.com/p/gerrit/) - a web based code review system siting between a developer and centralized git repo. Before the push is accepted it has to undergo review.

### Testing

* no formal test plans
* community testing (reading the other people's code)
* existing frameworks (created to test Linux kernel):
  * http://autotest.github.io/
  * http://linux-test-project.github.io/
  * http://elinux.org/Ktest#Git_Bisect_type

### 7: Thank you and questions

* [forking the Linux kernel](http://linux-beta.slashdot.org/story/07/09/18/131240/fork-the-linux-kernel)
* [difference between mrproper and make clean](http://www.linuxquestions.org/questions/slackware-14/difference-between-make-mrproper-and-make-clean-473144/)