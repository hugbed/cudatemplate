cmake_minimum_required(VERSION 2.8)
find_package(CUDA QUIET REQUIRED)

MESSAGE(STATUS "${CUDA_NVCC_FLAGS}")

set(CUDA_64_BIT_DEVICE_CODE ON)
set(CUDA_NVCC_FLAGS "${CUDA_NVCC_FLAGS} -std=c++11 -arch=sm_52" )

MESSAGE(STATUS "${CUDA_NVCC_FLAGS}")

INCLUDE_DIRECTORIES(
    include
)

CUDA_ADD_LIBRARY(
    simplecuda
    src/init.cu
)
TARGET_LINK_LIBRARIES(simplecuda ${CUDA_LIBRARIES})
TARGET_INCLUDE_DIRECTORIES(simplecuda PUBLIC include)
