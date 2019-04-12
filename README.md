# androidbuildlib
Script to build autotools-based library project for Android with configurable settings

# Install

Place `androidbuildlib` at your executable path i.e. `/usr/local/bin/` or even sym-link it as per your convenient.
Then you're ready to use it.

# How to use

`cd` to your target autotools-based library project.
Then execute `androidbuildlib`.

By default it will build the libraries according to what has been set in Makefile.am according to autotools way; into `build/` directory for 4 target architectures namely `armeabi-v7a`, `x86`, `arm64-v8a` and `x86_64`.

You have the following configurable settings

* `out_path` - target installation path to install generated library files for all archs, it need to be in relative path from the directory executing this script [**default** is `build`]
* `host_tag` - host value that will build the library (hint: you can take a look for this value at your `$ANDROID_NDK_HOME/toolchains/llvm/prebuilt/` [**default** is `linux-x86_64`]
* `minsdkversion`   - minimum sdk version to support, this is value of api level [**default** is 18]
* `target_abis` - target abis to build for, separated by space [**default** is "armeabi-v7a x86 arm64-v8a x86_64"]

To execute with custom settings, you do it like this

```
out_path=mybuild target_abis="armeabi-v7a x86" androidbuildlib
```

That will build for target `armeabi-v7a` and `x86`, then put the result library files into `mybuild` directory. Other default settings are applied, so it is built against api level 18, and on linux 64-bit as host.

# Note

For now, it only works for a library project that depends on standard libraries which Android already provided like libz etc. But it won't work if the library project depends on something else custom.

# License
[MIT](https://github.com/abzico/androidbuildlib/blob/master/LICENSE) Angry Baozi ([https://abzi.co](https://abzi.co))
