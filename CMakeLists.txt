cmake_minimum_required(VERSION 3.10.0)

if(DEFINED ENV{VCPKG_ROOT} AND NOT DEFINED CMAKE_TOOLCHAIN_FILE)
    set(CMAKE_TOOLCHAIN_FILE "$ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake")
endif()

project(HelloQt5Vcpkg VERSION 0.1.0)


set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

find_package(Qt5 REQUIRED COMPONENTS
 Core
 Widgets
#  Gui
# Network
# Concurrent
)

set(QT_DEPS
	Qt5::Widgets
	Qt5::Core
	# Qt5::Gui
	# Qt5::Network
	# Qt5::Concurrent
	)

# qt_standard_project_setup()

# 勝手に動くと困る事多いので、qt_wrap_uiで直接指定
set(CMAKE_AUTOUIC OFF)
# めちゃ遅いので必要な所だけqt_wrap_cppする。
set(CMAKE_AUTOMOC OFF)


include_directories(
	${PROJECT_SOURCE_DIR}
	${CMAKE_CURRENT_BINARY_DIR} #qt_wrap_uiがui_mainwindow.hをbuildのディレクトリに作るので。
)

set(QT_SOURCES
	notepad.cpp
	mainwindow.cpp
    main.cpp)

# このファイルだけUIC
qt_wrap_ui(QT_SOURCES notepad.ui)


# mocで処理、結果をQT_SOURCESに加える
qt_wrap_cpp(QT_SOURCES
 notepad.h
)

qt_add_resources(QT_SOURCES
  notepad.qrc
)

add_executable(HelloQt5Vcpkg
	${QT_SOURCES}
)

target_link_libraries(HelloQt5Vcpkg PRIVATE Qt5::Widgets)

set_target_properties(HelloQt5Vcpkg PROPERTIES
    WIN32_EXECUTABLE ON
    MACOSX_BUNDLE ON
)
if(CMAKE_HOST_APPLE)
	# Releaseだけユニバーサルバイナリに
	set_target_properties(HelloQt5Vcpkg PROPERTIES OSX_ARCHITECTURES_RELEASE "arm64;x86_64")
endif ()



# set(CPACK_PROJECT_NAME ${PROJECT_NAME})
# set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
# include(CPack)
