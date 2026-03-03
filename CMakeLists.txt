set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

file(GLOB_RECURSE component_srcs "src/*.cpp")

idf_component_register(
    SRCS ${component_srcs}
    INCLUDE_DIRS "include"
    REQUIRES driver
)

# Suppress warnings-treated-as-errors for this specific older library
target_compile_options(${COMPONENT_LIB} PRIVATE 
    "-Wno-error=narrowing" 
    "-Wno-error=missing-field-initializers"
)