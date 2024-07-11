# httpd.h

A header-only c library that helps you put together an HTTP server

## Dependencies

The only dependency of this library is the [clib.h](https://github.com/KDesp73/clib.h) utilities library which you can easily include in your project

## Examples

### Server

```c
#define HTTPD_IMPLEMENTATION
#include "httpd.h"

int main(void){
    server_t server = server_init("127.0.0.1", 8080, "./docs");
    
    run_server(server); 

    return 0;
}
```

### Daemon

```c
#define HTTPD_IMPLEMENTATION
#include "httpd.h"

int main(int argc, char** argv){
    server_t server = server_init("127.0.0.1", 8080, "./docs");
    
    DaemonAction action = -1;
    if(strcmp(argv[1], "START") == 0) action = DAEMON_START;
    else if(strcmp(argv[1], "STOP") == 0) action = DAEMON_STOP;
    else if(strcmp(argv[1], "RESTART") == 0) action = DAEMON_RESTART;
    else {
        printf("Usage: %s [START | STOP | RESTART]\n", argv[0]);
        exit(1);
    }

    run_daemon(action, server);

    return 0;
}
```


## LICENSE

[MIT](./LICENSE)
