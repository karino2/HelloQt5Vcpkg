# minimum project for vcpkg-Qt with cmake

main.cpp is copied from https://code.qt.io/cgit/qt/qtbase.git/plain/examples/widgets/tutorials/gettingStarted/gsQt/part1/main.cpp?h=5.15


### setup

```
vcpkg install qt5-base
```

Set VCPKG_ROOT environment variables.

### generate

```
mkdir build;
cmake . -B build -G "Ninja Multi-Config";
```

### build

```
cmake --build build --config Debug
```

### execute

```
open build/Debug/HelloQt5Vcpkg.app
```