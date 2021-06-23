# BTH011 FinalReview

## L00 IP Basics + Routing

### OSI Reference Model

- Application
- Presentation
- Session
- Transport
- Network
- Data Link
- Physic

### Host - Device with one or more L3 endpoint

### Router - Device with two or more L3 endpoints within two or more different subnets

### IP (Internet Protocol)

- IPv4 32-bit
- IPv6 128-bit
- Unreliable and connectionless datagram delivery service
- IP datagram header

### Subnet mask

### ARP (Address Resolution Protocol)

- IP --> MAC

## L02 Introduction to Sockets

### ICMP (Internet Control Message Protocol) - Error Handling

### UDP (User Datagram Protocol)

- Message Oriented Transport Protocol
- Unreliable datagram delivery
- Can provide Integrity Verification (Checksum)
- Simple
- Statless

### TCP (Transmission Control Protocol)

- Reliable, ordered and error-checked delivery of a stream of bytes
- End-to-end
- Full-duplex

### ntohs, ntohl, htons, htonl

### POSIX (Portable Operating System Interface) - System API Standard

### API - socket(int family, int type, int protocol)

Return: A non-negative integer, a socket descriptor

### API - bind(int socked, struct sockaddr*, int socklen_t)

![Screen Shot 2021-06-14 at 10.31.12 PM](/Users/salvation/Library/Application Support/typora-user-images/Screen Shot 2021-06-14 at 10.31.12 PM.png)

![Screen Shot 2021-06-14 at 10.31.20 PM](/Users/salvation/Library/Application Support/typora-user-images/Screen Shot 2021-06-14 at 10.31.20 PM.png)

#include <string.h>
/* ANSI C */ 
void *memset(void *dest, int c, size_t len);
void *memcpy(void *dest, const void *src, size_t nbytes);
int memcmp(const void *ptr1, const void *ptr2, size_t nbytes);

#include <arpa/inet.h>


### /* Convert ’A.B.C.D’ to 32-bit */

int inet_aton(const char *strptr, struct in_addr *addptr);  


### /* Convert ’A.B.C.D’ to 32-bit */

in_addr_t inet_addr(const char *strptr);


### /* Convert 32-bit to ’A.B.C.D’ */

char *inet_ntoa(struct in_addr inaddr);



### /* Convert ’A.B.C.D’ || ’A::D’ to 32/128-bit */

int inet_pton(int family, const char *strptr, void *addptr);  


### /* Convert 32/128-bit to ’A.B.C.D’ ||’A::D’ */

Const char *inet_ntop(int family, const struct *addrptr, char *strptr, size_t len);

## L02 UDP Sockets

### ![Screen Shot 2021-06-14 at 10.37.21 PM](/Users/salvation/Library/Application Support/typora-user-images/Screen Shot 2021-06-14 at 10.37.21 PM.png)

![Screen Shot 2021-06-14 at 10.38.17 PM](/Users/salvation/Library/Application Support/typora-user-images/Screen Shot 2021-06-14 at 10.38.17 PM.png)

### Send a Message with UDP

ssize_t send(int sockfd, const void *buf, size_t len, int flags);

ssize_t sendto(int sockfd, const void *buf, size_t len, int flags,
               const struct sockaddr *dest_addr, socklen_t addrlen);

ssize_t sendmsg(int sockfd, const struct msghdr *msg, int flags);



ssize_t write(int fd, const void *buf, size_t count);

### Receive a Message with UDP

ssize_t recv(int sockfd, void *buf, size_t len, int flags);

ssize_t recvfrom(int sockfd, void *buf, size_t len, int flags,
                 struct sockaddr *src_addr, socklen_t *addrlen);

ssize_t recvmsg(int sockfd, struct msghdr *msg, int flags);



ssize_t read(int fd, void *buf, size_t count);

### API - getaddrinfo(const char *hostname, const char *service, const struct addrinfo *hints, struct addrinfo **result)

### Connect on UDP

- Kernel checks for errors, records IP and port of the peer (from sockaddr). 
- Cannot use sendto -> send or write
- Cannot use recvfrom -> recv or read
- Asyncronous errors are returned to the process 

## L03 TCP Sockets

![Screen Shot 2021-06-14 at 11.01.39 PM](/Users/salvation/Library/Application Support/typora-user-images/Screen Shot 2021-06-14 at 11.01.39 PM.png)

### API - connect(int sockfd, const struct sockaddr *addr, socklen_t addrlen)

- Return: int
- Initialize a TCP connection towards the destination in addr

### API - bind(int sockfd, const struct sockaddr *addr, socklen_t addrlen)

- Assigns a local address and port to a socket

### API - listen(int sockfd, int backlog)

- Converts an active socket into a passive one
- Backlog specifies max number of connections to queue
  - Completed connection queue (ESTABLISHED)
  - Incomplete connection queue (SYN_RCVD)

### API - accept(int sockfd, const struct sockaddr *addr, socklen_t addrlen)

### API - close(int sockfd)

int getsockname(int sockfd, struct sockaddr *localaddr, socklen_t *localaddrlen); 
int getpeername(int sockfd, struct sockaddr *peeraddr, socklen_t *peerlen); 

## L04 IO Models

### IO Multiplexing

### IO Models

- Blocking I/O 阻塞recvfrom
- Nonblocking I/O 不阻塞recvfrom 若数据没有准备好则返回EWOULDBLOCK
- I/O multiplexing (select and poll) 用一个select线程集中处理轮询
- Signal driven (SIGIO) 数据准备完成后以信号通知用户进程
- Asynchronous I/O (POSIX aio_ functions) 异步处理

![Screen Shot 2021-06-15 at 6.35.43 PM](/Users/salvation/Library/Application Support/typora-user-images/Screen Shot 2021-06-15 at 6.35.43 PM.png)

### What does 'Ready' mean?

- Socket is ready for READING if:
  - Number of bytes in socket receive buffer is larger than low-water mark
  - The read half is closed (a socket receive FIN)
  - It's a listening socket, at least ONE completed connections (accept() would not block)
  - A socket error is pending
- Socket is ready for WRITING if:
  - Number of bytes available space in socket send buffer is larger than low-water mark for both connected TCP or UDP.
  - The write half is closed (a socket send FIN)
  - A socket using non-blocking connect has completed the connection, or the connect has failed. i.e. after connect()
  - A socket error is pending

![Screen Shot 2021-06-15 at 6.49.22 PM](/Users/salvation/Library/Application Support/typora-user-images/Screen Shot 2021-06-15 at 6.49.22 PM.png)

### Socket timeout

1. Alarm (SIGALRM)  + Signal handler 
2. Select
3. SO_RCVTIMEO, SO_SNDTIMEO - setsockopt()

![Screen Shot 2021-06-15 at 7.14.30 PM](/Users/salvation/Library/Application Support/typora-user-images/Screen Shot 2021-06-15 at 7.14.30 PM.png)

## L06 Multicast

### Multicast address

- IPv4
  - Class D; 224.0.0.0 - 239.255.255.255
- IPv6
  - ff:[*]
- Special
  - 224.0.0.1 all-hosts
  - 224.0.0.2 all-routers
  - ff01::1, ff02::1 all-nodes
  - ff01::2, ff02::2, ff05::2 all-routers

## HTTP

### HyperText Transfer Protocol

- HTTP is an asymmetric request-response client-server protocol
- Stateless
- Permits negotiation of data type and representation

### URL (Uniform Resource Locator)

protocol://hostname:port/path-and-file-name

## Basic Network Cryptography

### Security Attacks

- Passive Attacks
  - Learn or make use of information from target system but does not affect system resources.
- Active Attacks
  - Attempts to alter system resources or affect their operations.

### Terminology

- Plaintext - The original message or data that is fed into the algorithm as input
- Encrption algorithm - The encryption algorithm performs various operations on the plaintext
- Secret key - Input to the encryption algorithm that governs the operations.
- Ciphertext - The scrambled message.
- Decryption Algorithm - The decryption algorithm deciphers the ciphertext, using the secret key, and produces the original data.

### Symmetric Encryption

- Security - Depends on the secrecy of the key
- Algorithms
  - Data Encryption Standard (DES), 3DES
  - Blowfish
  - Twofish
  - Advanced Encryption Standard (AES)

# Client-Server Design Alternatives

### Server Strategies

- Iterative server
- Concurrent server, one fork per client request
- Prefork, each child calls accept
- Prefork, file locking to protect accept
- Prefork, thread mutex to protect accept
- Prefork, with parent passing socket to child
- Concurrent server, one thread per client.
- Prethreaded with mutex to protect accept
- Prethreaded with main thread calling accept