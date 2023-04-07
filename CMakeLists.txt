cmake_minimum_required(VERSION 3.12)
project(linapple)
set(TARGET_NAME linapple)

find_package(Threads REQUIRED)
find_package(SDL REQUIRED)
find_package(SDL_image REQUIRED)
find_package(CURL REQUIRED)
find_package(ZLIB REQUIRED)
find_package(X11 REQUIRED)

# No Find module for libzip, fallback to pkg-config
find_package(PkgConfig REQUIRED)
pkg_check_modules(ZIPLIB libzip REQUIRED)

add_subdirectory(src)
