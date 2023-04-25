SailrMC <img src="program_info/org.sailrmc.SailrMC.Source.svg" align=right style="width:96px;"/>
=======

### Description
SailrMC is a **DRM-free** Minecraft launcher for managing multiple instances at once.   
This is a fork of [PrismLauncher](https://github.com/PrismLauncher/PrismLauncher). We are not endorsed by them.


### Differences
Some differences between SailrMC and PrismLauncher are: 
- no DRM
- CurseForge support w/o the need for an API key (via [curse.tools](https://curse.tools))
- skin preview in the `Upload Skin` menu


### Installation

#### via source
Compiling SailrMC should be easy if you have the build dependencies to do so:
- C++17-compliant compiler
- `cmake`
- `cmake-extra-modules`
- Java Development Kit (17 is recommended)
- Qt5/6 Development tools

Here are the Linux instructions to compile SailrMC:
```sh
$ git clone --recurse-submodule https://github.com/SailrMC/SailrMC
$ cd SailrMC
$ cmake -S . -B build \
	-DCMAKE_INSTALL_PREFIX="/usr/local" \  # you can change this to "/usr" or to any preferred directory
	-DENABLE_LTO=ON
$ cmake --build build -j$(nproc)
$ cmake --install build
```
Note: if you are using FreeBSD, use `-j$(sysctl -n hw.ncpu)` instead.

#### via releases
As of current, there are no packages inside Linux distributions' repositories; however, 
you may visit the [Releases](https://github.com/SailrMC/SailrMC/releases) page.  
All you need to do is decompress the corresponding `.zip` file and use the binary inside of it.


### Licensing
This software is available under the GNU GPLv3 license. View `LICENSE` and `COPYING.md` for more information.
