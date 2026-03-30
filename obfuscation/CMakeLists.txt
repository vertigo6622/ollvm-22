cmake_minimum_required(VERSION 3.20)
project(Obfuscation)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if(NOT DEFINED LLVM_DIR AND EXISTS "/opt/homebrew/opt/llvm/lib/cmake/llvm")
  set(LLVM_DIR "/opt/homebrew/opt/llvm/lib/cmake/llvm")
endif()

find_package(LLVM REQUIRED CONFIG)

include_directories(${LLVM_INCLUDE_DIRS})
separate_arguments(LLVM_DEFINITIONS_LIST NATIVE_COMMAND ${LLVM_DEFINITIONS})
add_definitions(${LLVM_DEFINITIONS_LIST})

llvm_map_components_to_libnames(llvm_libs core support ipo transformutils scalaropts irreader)

add_library(Obfuscation MODULE
  CryptoUtils.cpp
  Substitution.cpp
  BogusControlFlow.cpp
  Utils.cpp
  SplitBasicBlock.cpp
  Flattening.cpp
  Plugin.cpp
)

target_include_directories(Obfuscation PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})

if(APPLE)
  set_target_properties(Obfuscation PROPERTIES
    LINK_FLAGS "-undefined dynamic_lookup"
  )
else()
  target_link_libraries(Obfuscation ${llvm_libs})
endif()
