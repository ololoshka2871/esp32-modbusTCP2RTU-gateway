set(sources
    main.cpp

    mDNSServer.cpp
)

idf_component_register(SRCS ${sources}
                    INCLUDE_DIRS "."
                    REQUIRES
                        esp32-wifi-manager
                        esp32-modbusTCP2RTU-gateway-lib

                        mdns
)

component_compile_options(-std=c++17)

target_compile_definitions(${COMPONENT_LIB}
    PRIVATE
        #-DTEST_MODE
)

target_link_libraries(${COMPONENT_LIB} PUBLIC ${LIBC})

