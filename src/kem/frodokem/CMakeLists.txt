# SPDX-License-Identifier: MIT

if(OQS_ENABLE_KEM_frodokem_640_aes)
    set(SRCS kem_frodokem640aes.c external/frodo640aes.c)
endif()
if(OQS_ENABLE_KEM_frodokem_640_shake)
    set(SRCS ${SRCS} kem_frodokem640shake.c external/frodo640shake.c)
endif()

if(OQS_ENABLE_KEM_frodokem_976_aes)
    set(SRCS ${SRCS} kem_frodokem976aes.c external/frodo976aes.c)
endif()
if(OQS_ENABLE_KEM_frodokem_976_shake)
    set(SRCS ${SRCS} kem_frodokem976shake.c external/frodo976shake.c)
endif()

if(OQS_ENABLE_KEM_frodokem_1344_aes)
    set(SRCS ${SRCS} kem_frodokem1344aes.c external/frodo1344aes.c)
endif()
if(OQS_ENABLE_KEM_frodokem_1344_shake)
    set(SRCS ${SRCS} kem_frodokem1344shake.c external/frodo1344shake.c)
endif()

add_library(frodokem OBJECT ${SRCS})
if(OQS_USE_AES_INSTRUCTIONS AND OQS_USE_AVX2_INSTRUCTIONS AND NOT OQS_PORTABLE_BUILD)
    target_compile_options(frodokem PRIVATE -maes -mavx2)
endif()
