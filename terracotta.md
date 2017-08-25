# Terrocatta OSS Cheat Sheet

## Resources
* https://terracotta.org/generated/4.3.0/html/bmg-all/index.html#page/BigMemory_Go_Documentation_Set%2Fco-oper_examples_of_uris_3.html%23


## API
### Configuration Details
```
http://localhost:9510/config
```

### Agent Details
```
http://localhost:9540/tc-management-api/agents
http://localhost:9540/tc-management-api/agents/info

http://localhost:9540/tc-management-api/v2/agents
http://localhost:9540/tc-management-api/v2/agents/info
```

### Caching
```
http://localhost:9540/tc-management-api/agents/cacheManagers
http://localhost:9540/tc-management-api/v2/agents/cacheManagers/caches?show=CacheHitRatio&show=CacheHitRate&show=CacheMissRate&show=Size&show=LocalHeapSize&show=LocalHeapSize&show=AverageGetTime
```