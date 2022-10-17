

# Partitioning, LVM

- `dd`
  - `dcfldd` - enhanced version of dd
  - **blocksize?** - default=512bytes, *bs=4M* for img to sd or usb ??









# Questions

- initramfs (`mkinitramfs`)
  - compressed cpio archive
  - the kernel unpacks that archive into RAM disk, mounts and uses it as
    initial root file system
