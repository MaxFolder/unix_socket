# Unix Sockets

Unix socket server with multiple clients

# Install

- composer require maxfolder/unix_socket

- set path to your local socket file in socket.ini
example: /var/www/server.socket

# Getting Started

create server.php

```
 if (file_exists($settings['SOCK_FILE_PATH'])) {
      unlink($settings['SOCK_FILE_PATH']);
  }
  
  $server = (new ServerSocketDataBuilder())
      ->setDomainServerSocketFilePath($settings['SOCK_FILE_PATH'])
      ->setProtocolFamilyForSocket(AF_UNIX)
      ->setTypeOfDataExchange(SOCK_STREAM)
      ->setProtocol(0)
      ->setMaxByteForRead(65536)
      ->built();
  
  
  $server->run();
```

create client.php
```

$client = (new ClientSocketDataBuilder())
    ->setDomainServerSocketFilePath($settings['SOCK_FILE_PATH'])
    ->setProtocolFamilyForSocket(AF_UNIX)
    ->setTypeOfDataExchange(SOCK_STREAM)
    ->setProtocol(0)
    ->setMaxByteForRead(65536)
    ->built();

$client->run();
```

run server.php in console then client.php in another console

<h1>License</h1>
<p>This project is licensed under the MIT License - see the LICENSE.md file for details</p>
