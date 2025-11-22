# minimum project for vcpkg-Qt with cmake

all sources and resources is copied from qtbase notepad examples from [notepad « tutorials « widgets « examples - qt/qtbase.git - Qt Base (Core, Gui, Widgets, Network, ...)](https://code.qt.io/cgit/qt/qtbase.git/tree/examples/widgets/tutorials/notepad?h=5.15)


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