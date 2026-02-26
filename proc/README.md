# /proc - Everything via Your Custom /bin/busybox

If /bin/busybox already exists, create symlinks:
```
mkdir -p /sbin
ln -s /bin/busybox /sbin/init
ln -s /bin/busybox /sbin/modprobe
ln -s /bin/busybox /sbin/reboot
ln -s /bin/busybox /sbin/poweroff
ln -s /bin/busybox /sbin/switch_root
```

Then extend your /bin/busybox script:
```
case "$cmd" in
    init)
        exec /init
        ;;
    reboot)
        echo b > /proc/sysrq-trigger
        ;;
    poweroff)
        echo o > /proc/sysrq-trigger
        ;;
    modprobe)
        echo "Module loading not implemented"
        ;;
```

# /proc - True Minimal Static Tools

