INCLUDE_DIRECTORIES(src)
INCLUDE_DIRECTORIES(src/gflags)

set(SRC
	src/gflags.cc
	src/gflags_completions.cc
	src/gflags_reporting.cc

	src/config.h
	src/gflags/gflags_completions.h
	src/gflags/gflags_declare.h
	src/gflags/gflags_gflags.h
	src/gflags/gflags.h
	src/mutex.h
	src/util.h)

if(WIN32)
  	list(APPEND SRC
		src/windows_port.cc
    	src/windows_port.h)
endif()

find_package(Threads)
add_library(${GFLAGS_LIBRARY} ${SRC})
target_link_libraries(${GFLAGS_LIBRARY} ${CMAKE_THREAD_LIBS_INIT})
