cmake_minimum_required(VERSION 3.10)
project(Mondis)

set(CMAKE_CXX_STANDARD 17)
AUX_SOURCE_DIRECTORY(src SRC_DIRS)
IF (WIN32)
    LINK_DIRECTORIES("D:\\mingw64\\x86_64-w64-mingw32\\lib" "C:\\Windows\\System32")
ENDIF ()
add_compile_options(-w -o2 -D_GLIBCXX_HAS_GTHREADS -D_GLIBCXX_USE_C99_STDINT_TR1 -D_GLIBCXX_USE_NANOSLEEP)
set(CMAKE_EXE_LINKER_FLAGS -static)


add_executable(Mondis ${SRC_DIRS})
IF (WIN32)
    target_link_libraries(Mondis ws2_32)
ELSEIF(UNIX)
    target_link_libraries(Mondis pthread)
ENDIF ()