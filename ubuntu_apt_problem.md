# About Ubuntu unable to install package
## Background
I can not run `apt-get install vim`, it shows `"Unable to locate package xxx"`. Also, after i run `apt-get update`, part of console shows `404`. 



I tried to echo the following

`"deb https://mirror.tuna.tsinghua.edu.cn/help/ubuntu/ jessie main non-free contrib"`


`"deb https://mirror.tuna.tsinghua.edu.cn/help/ubuntu/ jessie-proposed-updates main non-free contrib"`

to `source.list`, it also doesn't work

## Solution 
1. back up for original source.list and rename it to source.list_bk
2. echo the following
```bash
# deb cdrom:[Ubuntu 21.10 _Impish Indri_ - Release amd64 (20211012)]/ impish main restricted
 
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirrors.ustc.edu.cn/ubuntu-old-releases/ubuntu impish main restricted
# deb-src http://cn.archive.ubuntu.com/ubuntu/ impish main restricted
 
## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.ustc.edu.cn/ubuntu-old-releases/ubuntu impish-updates main restricted
# deb-src http://cn.archive.ubuntu.com/ubuntu/ impish-updates main restricted
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirrors.ustc.edu.cn/ubuntu-old-releases/ubuntu impish universe
# deb-src http://cn.archive.ubuntu.com/ubuntu/ impish universe
deb http://mirrors.ustc.edu.cn/ubuntu-old-releases/ubuntu impish-updates universe
# deb-src http://cn.archive.ubuntu.com/ubuntu/ impish-updates universe
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.ustc.edu.cn/ubuntu-old-releases/ubuntu impish multiverse
# deb-src http://cn.archive.ubuntu.com/ubuntu/ impish multiverse
deb http://mirrors.ustc.edu.cn/ubuntu-old-releases/ubuntu impish-updates multiverse
# deb-src http://cn.archive.ubuntu.com/ubuntu/ impish-updates multiverse
 
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirrors.ustc.edu.cn/ubuntu-old-releases/ubuntu impish-backports main restricted universe multiverse
# deb-src http://cn.archive.ubuntu.com/ubuntu/ impish-backports main restricted universe multiverse
 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu impish partner
# deb-src http://archive.canonical.com/ubuntu impish partner
 
deb http://mirrors.ustc.edu.cn/ubuntu-old-releases/ubuntu impish-security main restricted
# deb-src http://security.ubuntu.com/ubuntu impish-security main restricted
deb http://mirrors.ustc.edu.cn/ubuntu-old-releases/ubuntu impish-security universe
# deb-src http://security.ubuntu.com/ubuntu impish-security universe
deb http://mirrors.ustc.edu.cn/ubuntu-old-releases/ubuntu impish-security multiverse
# deb-src http://security.ubuntu.com/ubuntu impish-security multiverse
 
# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
```
3. run `apt-get update` and it can run `apt-get install -y xxx`!
