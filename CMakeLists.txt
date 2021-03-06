cmake_minimum_required(VERSION 3.10.2 FATAL_ERROR)

#============================================================================
# Initialize the project
#============================================================================
project(ignition-transport9 VERSION 9.0.0)

#============================================================================
# Find ignition-cmake
#============================================================================
# If you get an error at this line, you need to install ignition-cmake
find_package(ignition-cmake2 REQUIRED)
set(IGN_CMAKE_VER ${ignition-cmake2_VERSION_MAJOR})

#============================================================================
# Configure the project
#============================================================================
ign_configure_project(VERSION_SUFFIX pre1)

#============================================================================
# Set project-specific options
#============================================================================

# ignition-transport currently has no options that are unique to it

if (UNIX AND NOT APPLE)
  set (EXTRA_TEST_LIB_DEPS stdc++fs)
else()
  set (EXTRA_TEST_LIB_DEPS)
endif()

#============================================================================
# Search for project-specific dependencies
#============================================================================
message(STATUS "\n\n-- ====== Finding Dependencies ======")

#--------------------------------------
# Find Protobuf
set(REQ_PROTOBUF_VER 3)
ign_find_package(IgnProtobuf
                 VERSION ${REQ_PROTOBUF_VER}
                 REQUIRED
                 PRETTY Protobuf)

#--------------------------------------
# Find ZeroMQ
ign_find_package(ZeroMQ VERSION 4 REQUIRED PRIVATE)

#--------------------------------------
# Find cppzmq
ign_find_package(CPPZMQ REQUIRED PRIVATE
  PKGCONFIG_IGNORE # NOTE: cppzmq does not seem to offer a pkg-config file
  PRETTY CppZMQ)

#--------------------------------------
# Find uuid
if (MSVC)
  message (STATUS "UUID: Using Windows RPC UuidCreate function\n")
else()
  ign_find_package(UUID REQUIRED)
endif()

#--------------------------------------
# Find ignition-msgs
ign_find_package(ignition-msgs5 REQUIRED)
set(IGN_MSGS_VER ${ignition-msgs5_VERSION_MAJOR})

#--------------------------------------
# Find ifaddrs
ign_find_package(IFADDRS QUIET)
if (IFADDRS_FOUND)
  set (HAVE_IFADDRS ON CACHE BOOL "HAVE IFADDRS" FORCE)
else ()
  set (HAVE_IFADDRS OFF CACHE BOOL "HAVE IFADDRS" FORCE)
endif()

#--------------------------------------
# Find ignition-tools
ign_find_package(ignition-tools QUIET)

#--------------------------------------
# Find SQLite3
ign_find_package(SQLite3
  VERSION 3.7.13
  REQUIRED_BY log
  PRIVATE_FOR log
  PRETTY sqlite3)


#============================================================================
# Configure the build
#============================================================================
ign_configure_build(QUIT_IF_BUILD_ERRORS
  COMPONENTS log)

#============================================================================
# ign command line support
#============================================================================
add_subdirectory(conf)

#============================================================================
# Create package information
#============================================================================
ign_create_packages()

#============================================================================
# Configure documentation
#============================================================================
configure_file(${CMAKE_SOURCE_DIR}/api.md.in ${CMAKE_BINARY_DIR}/api.md)
configure_file(${CMAKE_SOURCE_DIR}/tutorials.md.in ${CMAKE_BINARY_DIR}/tutorials.md)

ign_create_docs(
  API_MAINPAGE_MD "${CMAKE_BINARY_DIR}/api.md"
  TUTORIALS_MAINPAGE_MD "${CMAKE_BINARY_DIR}/tutorials.md")
