# Cloudstress: Minimal version of Spirent Cloudstress
Details of Spirent Cloudstress can be found [here](https://www.spirent.com/Products/Temeva/CloudStress)

In this repository, there are two different avatars of simplified cloudstress -
1. Application.
2. VM - (qemu)

## Using cloudstress as application on linux:
1. Modify the config.zpl file according to your requirements - configure the required amount of CPU and Memory stresses.
2. Run the cloudstress application as
```sh
$ ./cloudstress --conffile config.zpl
```
3. Kill the cloudstress, when you are done.

## Using cloudstress as VM:
There are multiple options, (a) Using virt-manager or (b) using qemu-system-x86_64 command. Example:
```sh
$ sudo -E taskset -c 2,3 qemu-system-x86_64 -m 4096 -smp 2 -cpu host,migratable=off -drive if=scsi,file=cloudstress.qemu -boot c --enable-kvm -monitor unix:/tmp/vm0monitor,server,nowait -nographic -vnc :4 -name NN0 -snapshot -net none -no-reboot -drive if=scsi,format=raw,file=fat:rw:/tmp/qemu0_share,snapshot=off
```
###### NOTE: The VM is pre-configured to create stress according to the configuration found in config.zpl. If you need a different version- generating different stress load - contact sridhar.rao@spirent.com
