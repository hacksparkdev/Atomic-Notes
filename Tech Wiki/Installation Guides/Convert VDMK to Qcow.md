Tag: [[Proxmox]] #proxmox


### Image Files
```bash
#Image files are in 
/var/lib/vz/images
```

### Convert the File

```bash
qemu-img convert -f vmdk Metasploitable.vmdk Metasploitable.vmdk -O qcow2 Metasploitable.qcow2
```

### Move file back a directory

```bash
mv Metasploitable.qcow2 ../
```

### VM Configuration files location

```bash
/etc/pve/quemu-server
```

### Change the ide0

```bash
# Example
ide0: file=local: 600/Metasploitable.qcow2, size=32G
```

