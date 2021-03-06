# Eager
An Ogre3D 1.9 and C++ project template that uses cmake to generate project files.

You can fork this repo and work on the files in the source directory.

# Building your Project

Check the prerequisites section if anything fails here.

#### GNU Make (Linux)

First, clone the repo (or fork it!):

```bash
git clone https://github.com/matthewjberger/eager		
```		

Then to build, use [CMake](https://cmake.org/):

```bash
cd eager
mkdir build
cd build

# To generate makefiles and build
cmake .. 
make

# Alternatively, to generate an eclipse project
cmake -G "Eclipse CDT4 - Unix Makefiles" -D CMAKE_BUILD_TYPE=Debug .. 
```    

This will generate a makefile in the `build` directory. 

You can open this folder as a project in eclipse if you generated eclipse project files, using the following instructions from the cmake wiki:

To import the created project file into Eclipse:

    1.) Import project using Menu File->Import
    2.) Select General->Existing projects into workspace:
    3.) Browse where your build tree is and select the root build tree directory. Keep "Copy projects into workspace" unchecked.
    4.) You get a fully functional eclipse project 

Finally, when you compile, your project can be found in the `bin` directory.

# Vagrant

This will generate an ubuntu virtual machine with eclipse, cmake, and the Ogre3D library built from source and installed.

After loading up this virtual machine, you can follow the build instructions above for working on your project.

1.) [Install Vagrant](https://www.vagrantup.com/downloads.html)

2.) [Install Virtualbox](https://www.virtualbox.org/wiki/Downloads)

3.) Clone this repo with:

```bash
git clone https://github.com/matthewjberger/eager 
cd eager
```

4.) Enter the following command: 

```bash
vagrant up
```
> Username: `vagrant`

> Password: `vagrant`

The virtual machine will be downloaded and then opened in VirtualBox. You can login with the password `vagrant`. The files in this repo are in the folder `~/Code/eager` which is also shared with the host.

####Note: If there is an issue with the mouse while running a 3D program that captures the mouse, hit `ctrl+home` and then go to `input->mouse integration` and disable it. This can be re-enabled when you're finished running the program.

# Prerequisites

####Note: If you're using the ecc computers at the University of Nevada, Reno, the following steps are not required. The library has already been built from source and installed. However, if you are using NoMachine the code will compile but to run you must use the command below:
> /usr/NX/scripts/vgl/vglrun \<your project's .bin path here\>

Ogre 3D must be installed. If it isn't installed you should build it from the source with the following commands.  Mercurial is required to clone the repo.


#### Ubuntu (or any Debian-Based Linux distribution)

Download the required dependencies:

``` bash
sudo apt-get install libfreetype6-dev libfreeimage-dev libzzip-dev libxrandr-dev libxaw7-dev freeglut3-dev libgl1-mesa-dev libglu1-mesa-dev libcppunit-dev libboost-thread-dev libois-dev mercurial cmake g++ gdb doxygen
```

Clone the repo and grab version 1.9:
```bash
hg clone https://bitbucket.org/sinbad/ogre
cd ogre
hg pull
hg update v1-9
```

Use cmake to generate a makefile:

```bash
mkdir build
cd build
cmake ..
```

Build OGRE:
```bash
make -j5
```

Install the library:
```bash
sudo make install
```
