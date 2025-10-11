# Manual mounting

```bash
sudo lsblk
sudo mount /dev/<device> /mnt
```
# Automatic mounting

```bash
sudo blkid
sudo nano /etc/fstab
sudo mount -a
```

# Unmounting
```bash
sudo umount /dev/<device>
```