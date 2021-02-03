cmake_minimum_required(VERSION 3.10)

# set the project name
project(strophe_cmake)

include(FindEXPAT)
find_package(EXPAT REQUIRED)
message(STATUS ${EXPAT_INCLUDE_DIRS})

include(FindOpenSSL)
find_package(OpenSSL)
message(STATUS ${OPENSSL_INCLUDE_DIR})

set(CMAKE_BUILD_TYPE Release)

# Set the output folder where your program will be created
set(CMAKE_BINARY_DIR ${CMAKE_SOURCE_DIR}/bin)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR})
set(LIBRARY_OUTPUT_PATH /usr/local/lib_JPS)

# sources
set(source_files
  src/auth.c
  src/conn.c
  src/crypto.c
  src/ctx.c
  src/event.c
  src/handler.c
  src/hash.c
  src/jid.c
  src/md5.c
  src/rand.c
  src/resolver.c
  src/sasl.c
  src/scram.c
  src/sha1.c
  src/sha256.c
  src/sha512.c
  src/snprintf.c
  src/sock.c
  src/stanza.c
  src/util.c
  src/uuid.c
  src/parser_expat.c
  src/tls_openssl.c
    )

include_directories("${PROJECT_SOURCE_DIR}/include"
  ${EXPAT_INCLUDE_DIRS}
  ${OPENSSL_INCLUDE_DIR}
  )

# add the executable
add_library(strophe STATIC ${source_files})
#target_link_libraries(strophe} ${EXPAT_LIBRARIES})

# install targets
#install(TARGETS strophe DESTINATION ${PROJECT_SOURCE_DIR}/lib)
install(TARGETS strophe DESTINATION /usr/local/lib_JPS)

install(FILES include/strophe.h DESTINATION /usr/local/include_JPS)
