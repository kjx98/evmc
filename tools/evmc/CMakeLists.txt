# EVMC: Ethereum Client-VM Connector API.
# Copyright 2019-2020 The EVMC Authors.
# Licensed under the Apache License, Version 2.0.

hunter_add_package(CLI11)
find_package(CLI11 REQUIRED)

add_executable(evmc-tool main.cpp)
add_executable(evmc::tool ALIAS evmc-tool)
set_target_properties(evmc-tool PROPERTIES
    OUTPUT_NAME evmc
    RUNTIME_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/bin)
set_source_files_properties(main.cpp PROPERTIES
    COMPILE_DEFINITIONS PROJECT_VERSION="${PROJECT_VERSION}")
target_link_libraries(evmc-tool PRIVATE evmc::tool-utils evmc::mocked_host evmc::loader CLI11::CLI11)
