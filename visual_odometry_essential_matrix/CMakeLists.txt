include_directories('/Users/francis/local/Open3D/include/Open3D')

find_package(Open3D HINTS '/Users/francis/local/Open3D/lib/cmake/Open3D')
list(APPEND Open3D_LIBRARIES dl)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${Open3D_C_FLAGS}")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${Open3D_CXX_FLAGS}")
set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${Open3D_EXE_LINKER_FLAGS}")

add_definitions(-DUNIX)
add_compile_options(-Wno-deprecated-declarations)
add_compile_options(-Wno-unused-result)
add_definitions(-O3)

link_directories(${Open3D_LIBRARY_DIRS})
add_executable(EssentialMatrix main.cpp EssentialMatrix.cpp EssentialMatrix.h)
target_link_libraries(EssentialMatrix ${Open3D_LIBRARIES})
target_include_directories(EssentialMatrix PUBLIC ${Open3D_INCLUDE_DIRS})
