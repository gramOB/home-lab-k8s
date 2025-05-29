# filesystem-prep

## commands used to format disks
### confirm which disk the OS is on, so you don't delete yourself
```
lsblk -f
df /
lsblk -f | grep -v loop
```

***don't touch sda***

