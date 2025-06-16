set(CURL_INCLUDE_DIR ${CMAKE_SOURCE_DIR}/external/curl/include)
add_definitions(-DCURL_STATICLIB)
include_directories(${CURL_INCLUDE_DIR})

if (WIN32)
    set(CURL_LIBRARY ${CMAKE_SOURCE_DIR}/external/curl/lib/libcurl_a.lib)
    set(CURL_LIBRARIES ${CURL_LIBRARY} ws2_32 winmm wldap32 crypt32 normaliz)
elseif(UNIX)
    # No action needed here, will link after add_library
endif()

find_package(CURL REQUIRED)
add_library(imgur STATIC
    imgur.cpp
    imgur.h
)

if (WIN32)
    target_link_libraries(imgur ${CURL_LIBRARIES})
elseif(UNIX)
    target_link_libraries(imgur PUBLIC CURL::libcurl)
endif()