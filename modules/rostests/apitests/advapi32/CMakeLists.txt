
list(APPEND SOURCE
    CreateService.c
    DuplicateTokenEx.c
    eventlog.c
    Hash.c
    HKEY_CLASSES_ROOT.c
    IsTextUnicode.c
    LockServiceDatabase.c
    QueryServiceConfig2.c
    RegCreateKeyEx.c
    RegEnumKey.c
    RegEnumValueW.c
    RegOpenKeyExW.c
    RegQueryInfoKey.c
    RegQueryValueExW.c
    RtlEncryptMemory.c
    SaferIdentifyLevel.c
    ServiceArgs.c
    ServiceEnv.c
    ServiceNetwork.c
    svchlp.c)

list(APPEND PCH_SKIP_SOURCE
    testlist.c)

add_executable(advapi32_apitest
    ${SOURCE}
    ${PCH_SKIP_SOURCE})

target_link_libraries(advapi32_apitest wine ${PSEH_LIB})
set_module_type(advapi32_apitest win32cui)
add_importlibs(advapi32_apitest advapi32 iphlpapi ws2_32 msvcrt kernel32 ntdll)
add_pch(advapi32_apitest precomp.h "${PCH_SKIP_SOURCE}")
add_rostests_file(TARGET advapi32_apitest)
