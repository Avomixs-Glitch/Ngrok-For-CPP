# cppngrok
a cpp wrapper for ngrok

<br/>

### basic usage

```cpp

// warning - you are in testing branch, so some things arent complete stable or implemented

#include <iostream>
#include "cppngrok.h" // or <ccpngrok.h> if instaled cppngrok.h in includes

int main(){
        CppngrokHandler handler(true); // "true" is a argument for constructor to enable logger, use false to deactivate
        struct address_handler *recv_addr;

        recv_addr = handler.bind(methods::http, 1337); // binding http for port 1337
        std::cout << "HTTP ADDRESS :: " << recv_addr->ext_http << endl;

        recv_addr = handler.bind(methods::tcp, 1338); // binding tcp for port 1338
        std::cout << "TCP ADDRESS :: " << recv_addr->ext_tcp << endl;
        std::cout << "TCP PORT :: " << recv_addr->ext_tcp_port << endl;
        
        recv_addr = handler.bind(methods::tcp); // binding tcp for default port (1337)
        std::cout << "TCP ADDRESS :: " << recv_addr->ext_tcp << endl;
        std::cout << "TCP PORT :: " << recv_addr->ext_tcp_port << endl;
        
        recv_addr = handler.bind(); // binding http for port 80
        std::cout << "HTTP ADDRESS :: " << recv_addr->ext_http << endl;
}
```

### requeriments
```
https://ngrok.com/
```

### simple static build

```
make
g++ your_project.cpp build/cppngrok_lib.a
make clean
```

