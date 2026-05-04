# All of here was "fixed" and "optimized" by AI, so if it looks weird, that's why.

cmake_minimum_required(VERSION 3.21)

project(Template VERSION 1.0.0)

# Configuraciones de C++
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_VISIBILITY_PRESET hidden)

# Configuraciones de Arquitectura (Apple)
if ("${CMAKE_SYSTEM_NAME}" STREQUAL "iOS" OR IOS)
    set(CMAKE_OSX_ARCHITECTURES "arm64")
else()
    set(CMAKE_OSX_ARCHITECTURES "arm64;x86_64")
endif()

# 1. Buscar Geode (Forma estándar)
find_package(Geode CONFIG REQUIRED)

# 2. Recolectar fuentes
file(GLOB_RECURSE SOURCES CONFIGURE_DEPENDS src/*.cpp)

# 3. Definir el mod (CORREGIDO: Usando add_geode_mod)
add_geode_mod(${PROJECT_NAME} 
    SOURCES ${SOURCES}
)

# 4. Configurar metadatos y recursos
# Esto vincula automáticamente las librerías de Geode y prepara el archivo .geode
setup_geode_mod(${PROJECT_NAME})
