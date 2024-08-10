Install ZFS in Debian
    apt update
    apt install linux-headers-amd64
    apt install -t stable-backports zfsutils-linux

see all disk 
 lsblk


mirror pool (similar to raid-1, ≥ 2 disks, 1:1 redundancy)
 zpool create tank mirror scsi-35000cca2735cbc38 scsi-35000cca266cc4b3c

    
raidz1 pool (similar to raid-5, ≥ 3 disks, 1 disk redundancy)
 zpool create tank raidz scsi-35000cca2735cbc38 scsi-35000cca266cc4b3c scsi-35000cca26c108480

    
raidz2 pool (similar to raid-6, ≥ 4 disks, 2 disks redundancy)
 zpool create tank raidz2 scsi-35000cca2735cbc38 scsi-35000cca266cc4b3c scsi-35000cca26c108480 scsi-35000cca266ccbdb4

    
stripe pool (similar to raid-0, no redundancy)
 zpool create tank scsi-35000cca2735cbc38 scsi-35000cca266cc4b3c

   
single disk stripe pool
 zpool create tank scsi-35000cca26c108480

making a snapshot of tank/data
 zfs snapshot tank/data@2019-06-24

    
