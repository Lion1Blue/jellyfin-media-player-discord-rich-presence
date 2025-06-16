set(CURL_ROOT ${CMAKE_SOURCE_DIR}/external/curl)
set(CURL_INCLUDE_DIR ${CURL_ROOT}/include)
set(CURL_LIBRARY ${CURL_ROOT}/lib/libcurl_a.lib)
set(CMAKE_PREFIX_PATH ${CMAKE_PREFIX_PATH} ${CURL_ROOT})

# Add necessary Windows libraries
set(OS_LIBS ws2_32 winmm dwmapi IPHLPAPI)

include_directories(include)

add_library(curl STATIC ${CURL_INCLUDE_DIR}/curl/curl.h)

install(FILES "${CURL_ROOT}/bin/libcurl_a.lib" DESTINATION .)