# set minimum cmake version
cmake_minimum_required(VERSION 3.5 FATAL_ERROR)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

# project name and language
project(Genesis2 LANGUAGES Fortran)

# BUILD_SHARED_LIBS is a global flag offered by CMake
# to toggle the behavior of add_library
# With OFF it will create a static library
set(BUILD_SHARED_LIBS OFF)

option(USE_MPI "Activate MPI build" OFF)

list(APPEND _sources
    main.f
    check.f
    diagno.f
    esource.f
    field.f
    incoherent.f
    math.f
    partsim.f
    pushp.f
    loadbeam.f
    loadrad.f
    magfield.f
    tdepend.f
    track.f
    string.f
    rpos.f
    scan.f
    source.f
    stepz.f
    timerec.f
    initrun.f
    input.f
    output.f
)

if(USE_MPI)
    find_package(MPI REQUIRED)
    add_definitions(${MPI_Fortran_COMPILE_FLAGS} -DUSE_MPI)
    include_directories(${MPI_Fortran_INCLUDE_PATH})
    list(APPEND _sources mpi_multi.f)
    add_executable(genesis2 ${_sources})
    target_link_libraries(genesis2 ${MPI_Fortran_LIBRARIES})
else()
    configure_file(mpif.h.single mpif.h COPYONLY)
    list(APPEND _sources mpi_single.f)
    add_executable(genesis2 ${_sources})
endif()

install(TARGETS genesis2
        RUNTIME DESTINATION bin)

