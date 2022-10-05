Stop the instance that you can’t connect to. In the Oracle Cloud Infrastructure Console, go to the details page for the instance and click Stop. 
Detach the boot volume. In the Boot Volume section, click the Actions icon and choose Detach. See "Detaching a Boot Volume" for additional details if needed.
Attach the boot volume to another Linux instance by going to the details page of a different VM, clicking Attach Block Volume, and then selecting the boot volume that you just detached in the previous step. Be sure to select Read/Write access.
After the boot volume attachment is completed (the BV icon is green), connect through SSH in the running VM and run the iSCSI commands to make that new disk available and visible by the OS.
Your boot-volume should appear as /dev/sdb.
Make /dev/sdb3, which is the root (/) partition where you can recover the opc SSH key file, available to the local operating system using "mount" command. Be sure to use the -o nouuid option; otherwise, you will see the "mount: wrong fs type, bad option, bad superblock on /dev/sdb3" error message.
$  sudo mount -o nouuid /dev/sdb3 /mnt
Fix the opc SSH key by editing the /mnt/home/opc/.ssh/authorized_keys file and adding your SSH key public file.
$  sudo vi /mnt/home/opc/.ssh/authorized_keys
After you add or change the SSH public key you need to use, save and exit it.
$  sudo umount /mnt
Detach the iSCSI boot volume by running the detach iSCSI commands.
Ensure that the /dev/sdb disk is no longer available or visible through the SSH connection, and then detach it.
Reattach the boot volume to the instance where you wanted to recover the SSH key, wait for it to become operational (green icon) and start it.
That's it. You recovered your opc user SSH key and you can now log back in to the instance. You can also use this process for troubleshooting the root (/) partition.
