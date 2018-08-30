# Cross Compile Nginx with RTMP Module for Android
See full Chinese explanation blog here: https://zhangtom.com/2017/07/11/交叉编译带RTMP模块的Nginx到Android/

Succeed on macOS Sierra 10.12.5, macOS High Sierra 10.13.6, Ubuntu 14.04.5, with **Android NDK r15c**

Feel free to open issue if you have any question.

# Prerequisites

* Download latest stable version source code **tarball** of [Nginx](http://nginx.org/en/download.html) (`make_nginx.sh` will extract it automatically)
* Download latest stable version source code of [nginx-rtmp-module](https://github.com/arut/nginx-rtmp-module)
* Download and extract latest LTS version source code of [openssl](https://www.openssl.org/source/) and openssl-fips(no need for openssl-1.1.0 series)
* Download this repo and place source codes as following:
    ```
    .
    ├── Setenv-android.sh
    ├── glob (glob.c and glob.h will be copied to nginx/src/os/unix/ by make_nginx.sh)
    │   ├── glob.c
    │   └── glob.h
    ├── portable_cmds.sh
    ├── make_nginx.sh
    ├── make_openssl.sh
    │
    ├── nginx-1.12.0/ (this directory is generated by make_nginx.sh during extracting the counterpart tarball file)
    │   └── ...
    ├── nginx-1.12.0.tar.gz (Nginx source code tarball file, the version could be different)
    ├── nginx-rtmp-module/
    │   └── ...
    ├── openssl-1.1.0f/ (openssl source code directory, the version could be different)
    │   └── ...
    ├── openssl-fips-2.0.16/ (openssl-fips source code directory, the version could be different, no need for openssl-1.1.0 series)
    │   └── ...
    └── sdcard (this directory will be generated if compile successfully)
        └── nginx
    ```
* Download and install `Android SDK` if never installed before, make sure `adb` path is added to environment PATH and it works well
* Download and install `Android NDK` if never installed before, modify `Setenv-android.sh` if needed (`ANDROID_NDK_ROOT`, `_ANDROID_EABI`, `_ANDROID_API`, etc.)

# Build

execute these commands in Terminal:
```bash
# the leading period is important
. ./make_openssl.sh
. ./make_nginx.sh
```

# License

`Setenv-android.sh`: [OpenSSL license]  
`glob.c` and `glob.h`: [BSD-3-Clause License]  
`other files`: [WTFPL]  

[OpenSSL license]:http://www.openssl.org/source/license.html
[BSD-3-Clause License]:https://opensource.org/licenses/BSD-3-Clause
[WTFPL]: http://www.wtfpl.net/