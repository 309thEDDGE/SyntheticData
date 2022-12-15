cmake_minimum_required(VERSION 3.15)

project(irig106)

add_library(irig106 STATIC
    ./src/i106_data_stream.c
    ./src/i106_decode_1553f1.c
    ./src/i106_decode_16pp194.c
    ./src/i106_decode_arinc429.c
    ./src/i106_decode_can.c
    ./src/i106_decode_discrete.c
    ./src/i106_decode_ethernet.c
    ./src/i106_decode_index.c
    ./src/i106_decode_pcmf1.c
    ./src/i106_decode_time.c
    ./src/i106_decode_tmats_b.c
    ./src/i106_decode_tmats_c.c
    ./src/i106_decode_tmats_d.c
    ./src/i106_decode_tmats_g.c
    ./src/i106_decode_tmats_m.c
    ./src/i106_decode_tmats.c
    ./src/i106_decode_tmats_p.c
    ./src/i106_decode_tmats_r.c
    ./src/i106_decode_uart.c
    ./src/i106_decode_video.c
    ./src/i106_index.c
    ./src/i106_time.c
    ./src/irig106ch10.c
    ./src/sha-256.c
)

target_compile_definitions(irig106
    PRIVATE
    _FILE_OFFSET_BITS=64
    _LARGEFILE64_SOURCE
    IRIG_NETWORKING
    SHA256ENABLE
    )
target_include_directories(irig106 PUBLIC ./src)
set_property(TARGET irig106 PROPERTY POSITION_INDEPENDENT_CODE ON)


