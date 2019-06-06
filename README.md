
gateway.yml
```
spring: 
  cloud:
    gateway:
      default-filters:
      - AddResponseHeader=X-Response-Default-Foo, Default-Bar

      routes:
      - id: default_path_to_google
        uri: ${test.uri}
        filters:
        - name: RequestRateLimiter
          args:
            redis-rate-limiter.replenishRate: 2
            redis-rate-limiter.burstCapacity: 2
        order: 10000
        predicates:
        - Path=/**

```
