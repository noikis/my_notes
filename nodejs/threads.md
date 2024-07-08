
Event main Loop  single thread, that really just loops for callbacks
Threading in Node jS (libuv) used for IO/intensive and  CPU intensive :
  - DNS queries
  - file system reads
  - CPU intensive
  - crypto
  - compression (ZLIB)

You can increase the number of threads by modifying the env variable:
```javascript
process.env.UV_THREADPOOL_SIZE=7 // default=4
```

## Resources
[When is NodeJS Single-Threaded and when is it Multi-Threaded?](https://www.youtube.com/watch?v=gMtchRodC2I)
