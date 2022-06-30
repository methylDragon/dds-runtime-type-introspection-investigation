# Investigating Dynamic Types

This is a working workspace to test the features of dynamic type introspection from the different DDS vendors.

This features a selection of example packages that are immediately relevant.

# Running the Examples

## Pre-requisites

I think you'll need to install and source all the dependencies since the workspace is set up to build all the examples at once...

### RTI ConnextDDS

- [Install RTI ConnextDDS 6.1.1](https://www.rti.com/free-trial/dds-files)

And ensure you source it appropriately:

```shell
source ~/rti_connext_dds-6.1.1/resource/scripts/rtisetenv_x64Linux4gcc7.3.0.bash
export CONNEXTDDS_DIR=${NDDSHOME}
```



### Build The Workspace

```shell
$ colcon build
```



## RTI ConnextDDS 6.1.1

The examples in RTI ConnextDDS are for C++11.

Then running the examples is easy!

```shell
$ ./install/rtiexamples-connext-dds/bin/<EXAMPLE>/<EXAMPLE_BINARY>
```

