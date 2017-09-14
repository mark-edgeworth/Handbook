#### PortOut

Use the PortOut interface to write to an underlying GPIO port as one value. This is much faster than [BusOut](/docs/v5.4/reference/api-references.html#busout) because you can write a port in one go, but it is much less flexible because you are constrained by the port and bit layout of the underlying GPIO ports.

A mask can be supplied so only certain bits of a port are used, allowing other bits to be used for other interfaces.

##### PortOut class reference

[![View code](https://www.mbed.com/embed/?type=library)](https://docs.mbed.com/docs/mbed-os-api/en/mbed-os-5.5/api/classmbed_1_1PortOut.html)

##### PortOut Hello World!

[![View code](https://www.mbed.com/embed/?url=https://developer.mbed.org/teams/mbed_example/code/PortOut_HelloWorld/)](https://developer.mbed.org/teams/mbed_example/code/PortOut_HelloWorld/file/e4e6fab14d21/main.cpp)