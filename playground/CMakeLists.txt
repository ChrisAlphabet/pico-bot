# modified from https://github.com/raspberrypi/pico-examples.git

if (TARGET tinyusb_device)
    add_executable(playground
            playground.c
            )

    # pull in common dependencies
    target_link_libraries(playground pico_stdlib)

    # enable usb output, disable uart output
    pico_enable_stdio_usb(playground 1)
    pico_enable_stdio_uart(playground 0)

    # create map/bin/hex/uf2 file etc.
    pico_add_extra_outputs(playground)

elseif(PICO_ON_DEVICE)
    message(WARNING "not building playground because TinyUSB submodule is not initialized in the SDK")
endif()
