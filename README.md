# SteamOS dual boot cheat sheet for fixing corrupted bootloader

## Command 1 - Show Status of the NVME SSD's Partition Table:
```
sudo fdisk -l /dev/nvme0n1
```

## Command 2 - Select Primary NVME SSD to Operate on:
```
sudo fdisk /dev/nvme0n1
```

Once you hit `Enter` (you should see red text suggesting the partition table is busted)
Now type a `w` which stands for write. This command will re-write the partiion table using the backup that is still available.

## Command 3 - Fix SteamOS EFI boot loader:
```
sudo efibootmgr -c -d /dev/nvme0n1 -p 1 -L "SteamOS" -l "\EFI\steamos\steamcl.efi"
```

## Command 4 - Adjust Windows boot configuration data:
```
bcdedit.exe -set {globalsettings} highestmode on
```

# Note that this eventually will become a set of software tools to add some automation to help with the dual boot setup, if there is enough interest.
