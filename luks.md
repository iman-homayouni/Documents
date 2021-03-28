# Create an encrypted filesystem inside a file using LUKS

## 1. Create 2GB file
```
# fallocate -l 2048M /path/to/file
```

## 2. Create LUKS partition
```
# cryptsetup -y luksFormat /path/to/file
```

## 3. Open encrypted container
```
# cryptsetup luksOpen /path/to/file data
```

## 4. Create ext4 filesystem
```
# mkfs.ext4 /dev/mapper/data
```

## 5. Mount device to /mnt
```
# mount /dev/mapper/data /mnt/
```

## 6. Unmount filesystem
```
# umount /mnt/
```

## 7. Close LUKS device
```
# cryptsetup luksClose data
```

## 8. Increase container file size
```
# dd if=/dev/zero of=/path/to/file bs=384M count=1 oflag=append conv=notrunc
```

## 9. Open LUKS device
```
# cryptsetup luksOpen /path/to/file data
```

## 10. Resize LUKS device
```
# cryptsetup resize data
```

## 11. Resize ext4 filesystem
```
# e2fsck -f /dev/mapper/data
# resize2fs /dev/mapper/data
```

## 12. Mount device to /mnt
```
# mount /dev/mapper/data /mnt/
```

## 13. Check disk space usage
```
# df -h
```
