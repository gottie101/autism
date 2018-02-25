# vidya's Lord Autism

This setup was tested on Debian Wheezy (old as fuck but cba to break my over 650 days uptime kek).
I couldn't get most of the stuff from the pkg repo so I had to compile those from sources.
I almost felt like I was using Gentoo. kill me.

Update: I compiled it on Ubuntu 16.04 LTS recently

### Compilers and other shit
because others may not work due to some deprecated and/or not implemented features
* cmake `>= 3.0.2` (required by StormLib)
* g++ `<= 4.6` (required by Boost 1.38.0 and GHost)
* python `== 2.7` (required by Boost 1.38.0)

### Ghost libraries dependencies
* BncsUtils (included in the repository)
* pthreads (required by Boost library)
* zLib (required by Ghost++)
* libmysqlclient-dev (required by Ghost++)
* libbzip2 (rquired by StormLib)
* GMPlib (required by i forgot what)
* Storm (included in the repository)
* Boost 1.38.0 components: date_time-mt, filesystem-mt, system-mt, thread-mt (included in the repository)

### Getting this
```
git clone https://github.com/mike-code/autism.git
git submodule update --recursive --init
```

### Stuff that I got from the repository
* g++-4.6 (took it from Trusty repo)
* python2.7
* zlib1g-devb
* libc6-dev (includes pthreads)

### Building CMake 3.7.2 
```
cd 
./bootstrap
make
sudo make install
```

### Building GNU-GMP 6.1.2
```
cd gnu-gmp/
./configure
make
sudo make install
```

### Building Boost 1.38.0
```
cd boost_1_38_0
cmake -G "Unix Makefiles" -DCMAKE_IS_EXPERIMENTAL=YES_I_KNOW  -DCMAKE_CXX_COMPILER=/usr/bin/g++-4.6 -DCMAKE_C_COMPILER=/usr/bin/gcc-4.6 -B./build/ -H.
cd build
make boost_date_time-mt-shared boost_thread-mt-shared boost_system-mt-shared boost_filesystem-mt-shared
sudo cp lib/*.so /usr/local/lib
```

### Building StormLib
It might be a good idea to replace g++ with g++-4.6 in the Makefile
```
cd StormLib
mv Makefile.linux Makefile
make
sudo make install
```

### Building BncsUtils
It might be a good idea to replace g++ with g++-4.6 in the Makefile
```
cd bncsutil/src/bncsutil
make
sudo make install
```

### Building Ghost++
It might be a good idea to replace g++ with g++-4.6 in the Makefile
```
cd hostbot/ghost
make
move ghost++ ../
```

---
WIZARD
