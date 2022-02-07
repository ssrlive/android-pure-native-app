cmake_minimum_required(VERSION 3.6)

set(NATIVE_APP_GLUE_PATH ${ANDROID_NDK}/sources/android/native_app_glue)

add_library(native_app_glue STATIC ${NATIVE_APP_GLUE_PATH}/android_native_app_glue.c)

set(SOURCE_DIR ${CMAKE_CURRENT_LIST_DIR}/src/main/cpp)

add_library(nativedemo
  SHARED
    ${SOURCE_DIR}/main.cpp
    )

target_include_directories(nativedemo
  PRIVATE
    ${NATIVE_APP_GLUE_PATH}
    ${SOURCE_DIR}
    )

target_link_libraries(nativedemo
    native_app_glue
    android
    EGL
    GLESv1_CM
    log
    )
