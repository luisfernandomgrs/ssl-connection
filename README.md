# ssl-connection
Project C++, to learning about ssl-connection on Linux

This project has code based at publishing by [yuanhui360/CPP-Programming-on-Linux](https://github.com/yuanhui360/CPP-Programming-on-Linux/tree/main/YH-59)

# Notes about my setup
I used Windows 10/11 Pro with WSL and VSCode / Visual Studio Community

## You need to
1. Forever check if you has used tab control and not space char to align your Makefile.

2. How do I install the OpenSSL libraries?
  sudo apt-get install libssl-dev

3. How do I install the Boost libraries?
  sudo apt-get install libboost-all-dev

  :: see more at: [geeksforgeeks.org](https://www.geeksforgeeks.org/how-to-install-boost-library-in-cpp-on-linux/)

#Notes by owner project
1) Generate the private key of the root CA:
* openssl genrsa -out rootCAKey.pem 2048

2) Generate the self-signed root CA certificate:
* openssl req -x509 -sha256 -new -nodes -key rootCAKey.pem -days 3650 -out rootCACert.pem

In this example, the validity period is 3650 days. Set the appropriate number of days for your company. Make a reminder to renew the certificate before it expires.

# My notes
## This doesn't functionlly after steps above; I receive a sequence errors that i not resolved...

```cmd
/usr/include/boost/asio/detail/impl/posix_event.ipp:42: undefined reference to `pthread_condattr_setclock'
/usr/bin/ld: ssl_server.o: in function `boost::asio::detail::posix_thread::~posix_thread()':
/usr/include/boost/asio/detail/impl/posix_thread.ipp:35: undefined reference to `pthread_detach'
/usr/bin/ld: ssl_server.o: in function `boost::asio::detail::posix_thread::join()':
...
/usr/include/boost/asio/ssl/detail/impl/engine.ipp:321: undefined reference to `SSL_read'
/usr/bin/ld: ssl_server.o: in function `boost::asio::ssl::detail::engine::do_write(void*, unsigned long)':
/usr/include/boost/asio/ssl/detail/impl/engine.ipp:327: undefined reference to `SSL_write'
collect2: error: ld returned 1 exit status
make: *** [Makefile:15: ssl_server] Error 1
```
If your finded solution to this case, please help me 🙂