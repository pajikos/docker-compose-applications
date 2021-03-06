# Docker logging via graylog

## Start graylog
```
docker-compose up -d graylog
```

## Start input in graylog
```
 System ->
  Inputs ->
    Select Input ->
      Gelf UDP
```      
![input](https://github.com/marcelmaatkamp/docker-compose-applications/blob/master/graylog/contrib/Screen%20Shot%202016-10-18%20at%2015.21.37.png)
![active](https://github.com/marcelmaatkamp/docker-compose-applications/blob/master/graylog/contrib/Screen%20Shot%202016-10-18%20at%2015.21.43.png)

## Start example app
```
docker-compose -f docker-compose-hello.yml up hello-via-gelf
```

A docker application can now log to localhost:12201 where graylog will insert each stdout line into elasticsearch, an example would be via docker-compose
```
 hello-via-gelf:
  image: hello-world
  logging:
   driver: "gelf"
   options:
    gelf-address: "udp://localhost:12201"
```

## Admire output in graylog
![succes!](https://github.com/marcelmaatkamp/docker-compose-applications/blob/master/graylog/contrib/Screen%20Shot%202016-10-18%20at%2016.23.17.png)
