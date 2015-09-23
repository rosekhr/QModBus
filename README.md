# QModBus is wrapper over libmodbus for Qt


## Description
QModBus is abstract C++ class for Qt. QModBus is wrapper over libmodbus for Qt. 
From this abstract class inherited two specific classes: **QModBus_TCP** and **QModBus_RTU**. 
This class provides the opportunity to work with the library [(libmodbus ver 3.1.2)](http://www.libmodbus.org) in not blocking mode.



**The class has the following public methods:**
```C++
bool        is_connected() { return connect_done; }
const char *get_strerror() { return strerror; }


void set_slave(int new_slave);
int  get_slave() { return slave; }

void set_response_timeout(uint32_t sec, uint32_t usec);
void get_response_timeout(uint32_t *sec, uint32_t *usec);
```


**The class has the following public signals:**
```C++
signals:

    void connected();
    void disconnected();
    void error(QModBus::ModBusError error);

    void response_to_read_regs(int status);
    void response_to_write_reg(int status);
    void response_to_write_regs(int status);
```


**The class has the following public slots:**
```C++
public slots:

    virtual void connect();
    virtual void disconnect();

    virtual void read_regs(int addr, int num_regs, uint16_t *dest);
    virtual void write_reg(int addr, uint16_t value);
    virtual void write_regs(int addr, int num_regs, const uint16_t *data);
```


**The class has the following public enums:**
```C++
enum ModBusError
{
    NoConnectionError,
    CreateError,
    ConnectionError,
    SetSlaveError,
    ReadRegsError,
    WriteRegError,
    WriteRegsError,

    UnknownError = -1
};
```

More details see: **[qmodbus.h](.src/include/qmodbus.h)**


***
<br/>
## Usage

**To start working, perform the following steps:**

1. You need to include **[qmodbus.h](.src/include/qmodbus.h)** file in your **.cpp** file.
2. And add file **[qmodbus.cpp](.src/qmodbus.cpp)** to list of source files to compile (to qmake project file). (see an example)


***
<br/>
## Examples

1. test_tcp - how to work with the class QModBus_TCP
2. test_rtu - how to work with the class QModBus_RTU


## Note:
> In OS Linux Device for test_rtu is: **/dev/tty\***  default is: **/dev/ttyUSB0**

> In OS Windows Device for test_rtu is: **\\\\.\COM\***


***
<br/>
## License

[BSD](./LICENSE).
