cmake_minimum_required(VERSION 3.14)

project(CUDA_Map LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Core)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Core)
find_package(Qt6 REQUIRED COMPONENTS OpenGL)

add_executable(CUDA_Map
  main.cpp
  window.cpp window.h
  vertex.h
  resources.qrc
  shaders/simple.vert shaders/simple.frag
  transform3d.cpp transform3d.h
  input.cpp input.h
  camera3d.cpp camera3d.h
)
target_link_libraries(CUDA_Map PRIVATE
    Qt${QT_VERSION_MAJOR}::Core
    Qt6::OpenGL
)


install(TARGETS CUDA_Map
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)
