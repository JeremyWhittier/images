sudo genisoimage -output centos_1.iso -volid cidata -joliet -rock user-data meta-data

virt-install --name CentOS_2 --ram 2048 --disk centos_1.qcow2 --vcpus 2 --os-variant centos7.0 --connect qemu:///system --network bridge:virbr0,model=virtio --cdrom centos_1.iso --boot hd &

sudo virsh list --all
sudo virsh destroy CentOS_2
sudo virsh undefine CentOS_2

virt-install --name CentOS_2 --ram 2048 --disk centos_1.qcow2 --vcpus 2 --os-variant centos7.0 --connect qemu:///system --network bridge:virbr0,model=virtio --cdrom centos_1.iso --boot hd &
