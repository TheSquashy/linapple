cmake_minimum_required(VERSION 3.12)
project(linapple)
set(TARGET_NAME linapple)
set(VERSION 2.3.0)

set(SOURCES
  res/splash.xpm
  res/charset40_british.xpm
  res/charset40_french.xpm
  res/charset40_german.xpm
  res/charset40_IIplus.xpm
  res/charset40.xpm
  res/font.xpm
  res/icon.xpm
  res/splash.xpm

  Debugger/Debug.cpp
  Debugger/Debugger_Color.cpp
  Debugger/Debugger_Console.cpp
  Debugger/Debugger_DisassemblerData.h
  Debugger/Debugger_Help.cpp
  Debugger/Debugger_Parser.h
  Debugger/Debugger_Symbols.cpp
  Debugger/Debugger_Assembler.cpp
  Debugger/Debugger_Color.h
  Debugger/Debugger_Console.h
  Debugger/Debugger_Display.cpp
  Debugger/Debugger_Help.h
  Debugger/Debugger_Range.cpp
  Debugger/Debugger_Symbols.h
  Debugger/Debugger_Assembler.h
  Debugger/Debugger_Commands.cpp
  Debugger/Debugger_DisassemblerData.cpp
  Debugger/Debugger_Display.h
  Debugger/Debugger_Parser.cpp
  Debugger/Debugger_Range.h
  Debugger/Util_MemoryTextFile.cpp


  6821.cpp inc/6821.h
  Applewin.cpp inc/AppleWin.h
  asset.cpp inc/asset.h
  AY8910.cpp inc/AY8910.h
  Clock.cpp inc/Clock.h
  inc/Common.h
  CPU.cpp inc/CPU.h
  inc/Debugger_Types.h
  inc/Debug.h
  DiskChoose.cpp inc/DiskChoose.h
  Disk.cpp inc/Disk.h
  DiskFTP.cpp inc/DiskFTP.h
  DiskImage.cpp inc/DiskImage.h
  inc/file_entry.h
  Frame.cpp inc/Frame.h
  ftpparse.cpp inc/ftpparse.h
  Harddisk.cpp inc/Harddisk.h
  Joystick.cpp inc/Joystick.h
  Keyboard.cpp inc/Keyboard.h
  Log.cpp inc/Log.h
  Memory.cpp inc/Memory.h
  Mockingboard.cpp inc/Mockingboard.h
  MouseInterface.cpp inc/MouseInterface.h
  ParallelPrinter.cpp inc/ParallelPrinter.h
  Registry.cpp inc/Registry.h
  inc/resource.h
  Riff.cpp inc/Riff.h
  SaveState.cpp inc/SaveState.h
  SerialComms.cpp inc/SerialComms.h
  shim.cpp inc/shim.h
  SoundCore.cpp inc/SoundCore.h
  Speaker.cpp inc/Speaker.h
  stretch.cpp inc/SSI263Phonemes.h
  inc/stdafx.h
  inc/stretch.h
  inc/Structs.h
  Timer.cpp inc/Timer.h
  inc/Util_MemoryTextFile.h
  inc/Util_Text.h
  Video.cpp inc/Video.h
  inc/wincompat.h
  wwrapper.cpp inc/wwrapper.h
)

add_executable(${TARGET_NAME} ${SOURCES})

target_compile_definitions(${TARGET_NAME} PRIVATE VERSIONSTRING="${VERSION}")
target_include_directories(${TARGET_NAME} PRIVATE inc ${SDL_INCLUDE_DIRS} ${SDL_IMAGE_INCLUDE_DIRS}
  ${CURL_INCLUDE_DIRS} ${ZLIB_INCLUDE_DIRS} ${ZIPLIB_INCLUDE_DIRS} ${X11_INCLUDE_DIRS})
target_link_libraries(${TARGET_NAME} PRIVATE ${SDL_LIBRARIES} ${SDL_IMAGE_LIBRARIES} ${CURL_LIBRARIES}
  ${ZLIB_LIBRARIES} ${ZIPLIB_LIBRARIES} ${CMAKE_THREAD_LIBS_INIT} ${X11_LIBRARIES})

target_compile_options(${TARGET_NAME} PRIVATE -Wall -Werror)

# Install stuff
install(TARGETS ${TARGET_NAME} RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})
install(FILES res/linapple.conf DESTINATION ${CMAKE_INSTALL_SYSCONFDIR}/linapple)
install(FILES res/Master.dsk DESTINATION ${CMAKE_INSTALL_DATADIR}/linapple)
