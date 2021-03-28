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
