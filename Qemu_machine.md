## Created VM of linux/ARM64 using qemu on below environment

Host OS version:Name="Ubuntu linux"

Version="14.4"

Architecture:x86_64

Ram:8 GB


<h1 align=center> How do we install QEMU and install an OS on QEMU?</h1>



<h5> Step - 1 ==> To launch an aarch64 VM we first need to install a few dependencies</h5>

<p> apt-get install qemu-system-arm <br>
apt-get install qemu-efi-aarch64 <br>
apt-get install qemu-utils</p>

<h5> Step - 2 ==> Install qemu-system-aarch64</h5>
<p> wget https://download.qemu.org/qemu-2.11.0.tar.xz <br>
  tar xvJf qemu-2.11.0.tar.xz<br>
  cd qemu-2.11.0<br>
./configure –-target-list=aarch64-softmmu<br>
make<br>
sudo make install<p>




<h5> Step - 3 ==> Download the image you want to boot. <br> For our example we use an Ubuntu installer.</h5>

<p> wget http://ports.ubuntu.com/ubuntu-ports/dists/bionic-updates/main/installer-arm64/current/images/netboot/mini.iso </p>





<h5> Step - 4 ==> Create the empty Ubuntu image file we will install Ubuntu into. <br> We will use 20 gigabytes for this file.</h5>

<p> qemu-img create ubuntu-image.img 20G </p>





<h5> Step - 5 ==> Start QEMU with the installer.</h5>

<p> qemu-system-aarch64 -nographic -machine virt,gic-version=max -m 512M -cpu max -smp 4 \
-netdev user,id=vnet,hostfwd=:127.0.0.1:0-:22 -device virtio-net-pci,netdev=vnet \
-drive file=ubuntu-image.img,if=none,id=drive0,cache=writeback -device virtio-blk,drive=drive0,bootindex=0 \
-drive file=mini.iso,if=none,id=drive1,cache=writeback -device virtio-blk,drive=drive1,bootindex=1 \
-drive file=flash0.img,format=raw,if=pflash -drive file=flash1.img,format=raw,if=pflash  </p>






<h5> Step - 6 ==> Follow the instructions to install Ubuntu to the ubuntu-image.img file. <br> Once the install is finished you can exit QEMU with -a x. <br> Then restart QEMU without the installer image with the following command.</h5>

<p> qemu-system-aarch64 -nographic -machine virt,gic-version=max -m 512M -cpu max -smp 4 \
-netdev user,id=vnet,hostfwd=:127.0.0.1:0-:22 -device virtio-net-pci,netdev=vnet \
-drive file=ubuntu-image.img,if=none,id=drive0,cache=writeback -device virtio-blk,drive=drive0,bootindex=0 \
-drive file=flash0.img,format=raw,if=pflash -drive file=flash1.img,format=raw,if=pflash  </p>


**Source Link  ===>** https://futurewei-cloud.github.io/ARM-Datacenter/qemu/how-to-launch-aarch64-vm/
