# protobuf-ios-android

Generate protobuf-3.6.1 for iOS/Android.  

This repository extracts only the protobuf compile script from tensorflow.  
Original full source code is here.

* https://github.com/tensorflow/tensorflow/tree/master/tensorflow/contrib/makefile

I saw the last comment here and found that tensorflow is maintaining protobuf's script.

* https://gist.github.com/BennettSmith/9487468ae3375d0db0cc 

## Setup

```bash
$ git clone https://github.com/jnst/protobuf-ios-android.git
$ cd protobuf-ios-android
```

```bash
$ tensorflow/contrib/makefile/download_dependencies.sh
```

## Compile

### iOS

Make sure that the build tools is installed in Mac.

```bash
$ xcode-select --install
$ brew install automake
$ brew install libtool
```

```bash
$ tensorflow/contrib/makefile/compile_ios_protobuf.sh
```

### Android

You need to download `android-ndk` and Environment variable of `NDK_ROOT`.

```bash
$ echo $NDK_ROOT
/Users/jnst/android-ndk-r12b
```

By the way I tried it with `android-ndk-r16b` but it failed.

```bash
$ tensorflow/contrib/makefile/compile_android_protobuf.sh
```

## Generated artifacts

```bash
$ tree -I 'compiler|io|stubs|util|pkgconfig|*.h|*.pc|*.proto' tensorflow/contrib/makefile/gen/
tensorflow/contrib/makefile/gen/
├── protobuf-host
│   ├── bin
│   │   └── protoc
│   ├── include
│   │   └── google
│   │       └── protobuf
│   └── lib
│       ├── libprotobuf-lite.a
│       ├── libprotobuf-lite.la
│       ├── libprotobuf.a
│       ├── libprotobuf.la
│       ├── libprotoc.a
│       └── libprotoc.la
├── protobuf_android
│   └── armeabi-v7a
│       ├── bin
│       │   └── protoc
│       ├── include
│       │   └── google
│       │       └── protobuf
│       └── lib
│           ├── libprotobuf-lite.a
│           ├── libprotobuf-lite.la
│           ├── libprotobuf.a
│           ├── libprotobuf.la
│           ├── libprotoc.a
│           └── libprotoc.la
└── protobuf_ios
    └── lib
        ├── ios_arm64
        │   ├── bin
        │   │   └── protoc
        │   ├── include
        │   │   └── google
        │   │       └── protobuf
        │   └── lib
        │       ├── libprotobuf-lite.a
        │       ├── libprotobuf-lite.la
        │       ├── libprotobuf.a
        │       ├── libprotobuf.la
        │       ├── libprotoc.a
        │       └── libprotoc.la
        ├── ios_arm7
        │   ├── bin
        │   │   └── protoc
        │   ├── include
        │   │   └── google
        │   │       └── protobuf
        │   └── lib
        │       ├── libprotobuf-lite.a
        │       ├── libprotobuf-lite.la
        │       ├── libprotobuf.a
        │       ├── libprotobuf.la
        │       ├── libprotoc.a
        │       └── libprotoc.la
        ├── ios_arm7s
        │   ├── bin
        │   │   └── protoc
        │   ├── include
        │   │   └── google
        │   │       └── protobuf
        │   └── lib
        │       ├── libprotobuf-lite.a
        │       ├── libprotobuf-lite.la
        │       ├── libprotobuf.a
        │       ├── libprotobuf.la
        │       ├── libprotoc.a
        │       └── libprotoc.la
        ├── iossim_386
        │   ├── bin
        │   │   └── protoc
        │   ├── include
        │   │   └── google
        │   │       └── protobuf
        │   └── lib
        │       ├── libprotobuf-lite.a
        │       ├── libprotobuf-lite.la
        │       ├── libprotobuf.a
        │       ├── libprotobuf.la
        │       ├── libprotoc.a
        │       └── libprotoc.la
        ├── iossim_x86_64
        │   ├── bin
        │   │   └── protoc
        │   ├── include
        │   │   └── google
        │   │       └── protobuf
        │   └── lib
        │       ├── libprotobuf-lite.a
        │       ├── libprotobuf-lite.la
        │       ├── libprotobuf.a
        │       ├── libprotobuf.la
        │       ├── libprotoc.a
        │       └── libprotoc.la
        ├── libprotobuf-lite.a
        └── libprotobuf.a

45 directories, 51 files
```
