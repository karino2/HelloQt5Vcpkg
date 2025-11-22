# minimum project for vcpkg-Qt with cmake

all sources and resources is copied from qtbase notepad examples from [notepad « tutorials « widgets « examples - qt/qtbase.git - Qt Base (Core, Gui, Widgets, Network, ...)](https://code.qt.io/cgit/qt/qtbase.git/tree/examples/widgets/tutorials/notepad?h=5.15)


## on Windows

qt5-base needs to place vcpkg directory to very short path (like P:/build/vcpkg_installed).
So we need to use subst to assign current dir to P:.

### setup

```
PS> subst P: $PWD
PS> cd P:
```

### generate

```
PS> mkdir build
PS> cmake . -B build -G "Visual Studio 17 2022" -A x64
```

### build


```
PS> cmake --bild ./build --config Debug
```


## on Mac

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