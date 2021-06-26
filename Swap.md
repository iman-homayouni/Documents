# Create an encrypted filesystem inside a file using LUKS

## 1. Create 2GB file
```
# fallocate -l 2G /swapfile
```

## 2. Change permission
```
# chmod 600 /swapfile
```

## 3. Use mkswap command
```
# mkswap /swapfile
```

## 4. Open fstab file using vim text editor
```
# vim /etc/fstab
```


## 5. Insert this line
```
/swapfile swap swap defaults 0 0
```
