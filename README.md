# Investigating Dynamic Types

This is a working workspace to test the features of dynamic type introspection from the different DDS vendors.

This features a selection of example packages that are immediately relevant.

# Setup

## RTI ConnextDDS 6.1.1

- [Install RTI ConnextDDS 6.1.1](https://www.rti.com/free-trial/dds-files)

And ensure you source it appropriately:
```shell
source ~/rti_connext_dds-6.1.1/resource/scripts/rtisetenv_x64Linux4gcc7.3.0.bash
export CONNEXTDDS_DIR=${NDDSHOME}
```

The examples in RTI ConnextDDS are for C++11.
