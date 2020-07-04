## Prepare the build environment:

```sh
sudo apt-get install -y libmnl-dev libelf-dev build-essential pkg-config bc git
```

## Get kernel source:

```
cd ~/mv1000-ubuntu/
git clone https://github.com/gl-inet/mv1000-ubuntu-kernel.git ubuntu-kernel
```

## Setup toolchan:
```
mkdir -p ~/mv1000-ubuntu/toolchain
cd ~/mv1000-ubuntu/toolchain
wget https://releases.linaro.org/components/toolchain/binaries/7.4-2019.02/aarch64-linux-gnu/gcc-linaro-7.4.1-2019.02-x86_64_aarch64-linux-gnu.tar.xz
tar -xvf gcc-linaro-7.4.1-2019.02-x86_64_aarch64-linux-gnu.tar.xz
export PATH=$PATH:~/mv1000-ubuntu/toolchain/gcc-linaro-7.4.1-2019.02-x86_64_aarch64-linux-gnu/bin
```

## Compile kernel:
```
cd ~/mv1000-ubuntu/ubuntu-kernel
export ARCH=arm64
export CROSS_COMPILE=aarch64-linux-gnu-
make mvebu_v8_lsp_defconfig
make -j4
```

Original reference:

http://wiki.espressobin.net/tiki-index.php?page=Build+From+Source+-+Toolchain

http://wiki.espressobin.net/tiki-index.php?page=Build+From+Source+-+Kernel
