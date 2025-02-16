cmake_minimum_required(VERSION 3.10.2 FATAL_ERROR)

if(${CMAKE_SYSTEM_NAME} STREQUAL "Linux")
  find_package(ignition-transport11 QUIET REQUIRED OPTIONAL_COMPONENTS log)
  set(IGN_TRANSPORT_VER ${ignition-transport11_VERSION_MAJOR})

  find_package(sdformat12 REQUIRED)
  set(SDF_VER ${sdformat12_VERSION_MAJOR})

  find_package(ignition-msgs8 REQUIRED)
  set(IGN_MSGS_VER ${ignition-msgs8_VERSION_MAJOR})

  find_package(ignition-common4 REQUIRED)
  set(IGN_COMMON_VER ${ignition-common4_VERSION_MAJOR})

  add_executable(keyboard keyboard.cc)
  target_link_libraries(keyboard
    ignition-transport${IGN_TRANSPORT_VER}::core
    sdformat${SDF_VER}::sdformat${SDF_VER}
    ignition-msgs${IGN_MSGS_VER}
    ignition-common${IGN_COMMON_VER}::ignition-common${IGN_COMMON_VER}
    stdc++fs
    )
endif()
