
add_executable(createspec createspec.c)
set_module_type(createspec win32cui)
target_link_libraries(createspec wine)
if(CMAKE_C_COMPILER_ID STREQUAL "GNU")
    target_compile_options(createspec PRIVATE $<$<COMPILE_LANGUAGE:C>:-Wno-stringop-overflow>)
endif()
add_importlibs(createspec dbghelp msvcrt kernel32)
add_cd_file(TARGET createspec DESTINATION reactos/system32 FOR all)
