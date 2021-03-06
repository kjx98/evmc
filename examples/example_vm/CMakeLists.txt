# EVMC: Ethereum Client-VM Connector API.
# Copyright 2019-2020 The EVMC Authors.
# Licensed under the Apache License, Version 2.0.

add_library(example-vm SHARED example_vm.c example_vm.h)
add_library(evmc::example-vm ALIAS example-vm)
target_link_libraries(example-vm PRIVATE evmc::evmc)

add_library(example-vm-static STATIC example_vm.c example_vm.h)
add_library(evmc::example-vm-static ALIAS example-vm-static)
target_link_libraries(example-vm-static PRIVATE evmc::evmc)

set_source_files_properties(example_vm.c PROPERTIES
    COMPILE_DEFINITIONS PROJECT_VERSION="${PROJECT_VERSION}")

if(EVMC_INSTALL)
    install(TARGETS example-vm
        ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
        RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
    )
endif()
