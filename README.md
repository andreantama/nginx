# Install Nginx di systemd
systemd only availble Ubuntu and centos

mencari port nginx berjalan
```bash
ps aux | grep nginx
```

signal command to quit, stop nginx
```bash
nginx -s stop
```

test nginx conf
```bash
nginx -t
```

configuration systemd nginx
https://www.nginx.com/resources/wiki/start/topics/examples/systemd/


# Configuration terms nginx
2 terms configuration nginx

1. Directive
```bash
server_name mydomain
```

2. Context
```bash
server { #context start
  index index.html index.htm index.php; #directive

  include mime.types; #directive

  server { #context start
    listen 80; #directive
    server_name mydomain.com #directive
  } #context end
} # context end

```

# Creating Virtual Host

```bash
events {}

http {
  # START DOCUMMENTATION
  # to register nginx mime types of contens is served

  # types {
  #   text/html html;
  #   text/css css;
  # }

  # or

  include mime.types

  # END DOCUMMENTATION

  server {
    
    # listen import 80
    listen 80;
    # name domain subdomain ip address
    server_name 127.0.0.1
    # route path which serving request from
    root /var/www/html

    # START DOCUMMENTATION
    # LOCATION BLOCKS
    # Location block is use for define and conigure the behavior spesific URI Request

    # prefix match : everythinf url start with greet , greetings/
    # location /greet {
    #   return 200 'Hello Greet World';
    # }

    # exact match : url with semae greet
    # location = /greet {
    #   return 200 'Hello Greet World';
    # }

    # REGEX match : url with case sensitive
    # location ~ /greet[0-9] {
    #   return 200 'Hello Greet World';
    # }

    # REGEX match : url with incasesensitive
    # location ~* /greet[0-9] {
    #   return 200 'Hello Greet World';
    # }

    # 

    # END DOCUMMENTATION


  }
}
```

# Varibles
```bash
$http, $url, $args
$host\n$uri\n$args
$arg_name

if($arg_apikey != 1234) {
  return 401 "Incorrect Api Key";
}

set $weekend "No";

# Check if weekend

if($date_local ~ 'Saturday|Sunday') {
  set $weekend "Yes";
}
```





