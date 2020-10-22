The latest release of Genesis supports parallel computer architecture,
based on the Message Passing Interface (MPI) protocol.

# Precompiled

## Anaconda

```shell script
conda install -c conda-forge genesis2
```

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