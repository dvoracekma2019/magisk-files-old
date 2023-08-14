# Magisk Delta Internal Documentation

## Early-init mount

- Check if Magisk Delta support `early-mount.d/v2`:

```
EARLYMOUNTV2=false
if grep "$(magisk --path)/.magisk/early-mount.d" /proc/mounts | grep -q '^early-mount.d/v2'; then
    EARLYMOUNTV2=true
fi
```

### General

- Some files requires to be mounted earliest in the boot process, Magisk Delta has provided the way to mount files in `pre-init` stage, before `init` is executed
- Since Magisk Delta v26.0+ with `early-mount.d/v2`, the general early-mount partition will be mounted at `$MAGISKTMP/.magisk/early-mount.d` due the new sepolicy rules implementation. The early-mount partition is same as the preinit partition. Magisk will hardcode perinit partition while patching boot image. The preinit partition could be: `data`, `cache`, `metadata` / `cust`, `persist`, ...

> (*) Be careful when device use persist or metadata for early-mount, these partitions are very limited in size. Filling up them might cause device unable to boot.

- You can place your files into the corresponding location under `early-mount.d` directory. For example, you want to replace `/vendor/etc/vintf/manifest.xml`, copy your `manifest.xml` to `$MAGISKTMP/.magisk/early-mount.d/system/vendor/etc/vintf/manifest.xml` , Magisk Delta will mount your files in the next reboot​. Other files are not in `early-mount.d/system` will be ignored.

### Module

- Since Magisk Delta v26.0+ with `early-mount.d/v2`, you can now place your early-mount files to `/data/adb/modules/<module_id>/early-mount`

**Early-init mount only support simple mount, which means it can replace files but cannot add new files, folders or replace folders**

## init.rc inject

- Feel annoying when you must repack boot image to inject custom `*.rc` script by using `overlay.d`? Magisk Delta has provide the way to inject custom `*.rc` script systemlessly!
- The chose location of custom `*.rc` script is `$PRENITDIR/early-mount.d/initrc.d`. Magisk Delta will inject all scripts in this folder into `init.rc` every boot.
- You can use `${MAGISKTMP}` to refer to Magisk tmpfs folder. Every occurrence of the pattern `${MAGISKTMP}` in your `*.rc` scripts will be replaced with the Magisk tmpfs folder when magiskinit injects it into `init.rc`.
- Magisk's mirror will not be available while booting, in order to access to the copy of `early-mount.d` directory. You can use this pattern `${MAGISKTMP}/.magisk/early-mount.d`.

- Here is an example of the `custom.rc` if you use `initrc.d`:

```
# Use ${MAGISKTMP} to refer to Magisk's tmpfs directory

on early-init
    setprop sys.example.foo bar
    insmod ${MAGISKTMP}/.magisk/early-mount.d/libfoo.ko
    start myservice

service myservice ${MAGISKTMP}/.magisk/early-mount.d/myscript.sh
    oneshot
```

### Module

- Since Magisk Delta v26.0+ with `early-mount.d/v2`, you can now place your initrc.d files to `/data/adb/modules/<module_id>/early-mount/initrc.d`


## Remove files and folders

- Using Magisk module is the easy way to modify system partitions without actually making changes to the system partitions, and the changes can be easily. Magisk modules can replace and add any file or folder to system. However, removing files by Magisk modules is still not allowed.

- In Magisk documentation:

> It is complicated to actually remove a file (possible, not worth the effort). Replacing it with a dummy file should be good enough

> It is complicated to actually remove a folder (possible, not worth the effort). Replacing it with an empty folder should be good enough. Add the folder to the replace list in "config.sh" in the module template, it will replace the folder with an empty one

- In some case, replacing file or folder with empty one is not enough and might cause issue, some modding require files to be disappeared in order to take effect. So Magisk Delta has added removal support for modules: Create the broken symlink which points to `/xxxxx` into the corresponding location of module directory

- Example creating symbolic link as `/data/adb/modules/mymodule_id/system/vendor/etc/thermal-engine-normal.conf`, the target `/vendor/etc/thermal-engine-normal.conf` will be ignored and disappeared

```
ln -s "/xxxxx" /data/adb/modules/mymodule_id/system/vendor/etc/thermal-engine-normal.conf
```

