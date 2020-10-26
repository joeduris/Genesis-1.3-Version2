The latest release of Genesis supports parallel computer architecture,
based on the Message Passing Interface (MPI) protocol.

# Precompiled

## Anaconda

The command below will install by default a `nompi` version of the package.
```shell script
conda install -c conda-forge genesis2
```

You can force a MPI implementation when installing via:
```shell script
# for OpenMPI
conda install -c conda-forge genesis2=*=mpi_openmpi*

# for MPICH
conda install -c conda-forge genesis2=*=mpi_mpich*
```

For usage with External MPI (common with HPC systems), please refer to the conda-forge notes on this
[link here](https://conda-forge.org/docs/user/tipsandtricks.html#using-external-message-passing-interface-mpi-libraries).

# Compiling The Code

## Unix

### Single Processor Code:

```shell script
mkdir build
cd build
cmake .. -DUSE_MPI=OFF
make
make install
```

### Multi Processor Code:

```shell script
mkdir build
cd build
cmake .. -DUSE_MPI=ON
make
make install
```

## Windows

### Single Processor Code:

```shell script
mkdir build
cd build
cmake -G "MinGW Makefiles" .. -DUSE_MPI=OFF
cmake --build .
cmake --install
```

### Multi Processor Code:

**Not Supported**

Original Author: Sven Reiche - UCLA 9/30/05


## Testing

```shell script
# Generate template file
genesis2
# Execute template file
genesis2 template.in
```