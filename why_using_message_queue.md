##  왜 메시지 큐를 쓰는 것인지?  
그냥 바로 각 celery 의 worker에게 task를 할당시키면 되는것 아닌지?  
```   
Message queues enable asynchronous communication, which means that the endpoints that are   
producing and consuming messages interact with the queue, not each other.   
Producers can add requests to the queue without waiting for them to be processed.   
Consumers process messages only when they are available.
```   
매시지 큐는 비동기 작업을 가능하게 해준다. 어떤 task를 전달하는 producer(내경우 dajango app) 이 기다리지 않고 작업을 전달할 매개가 되는것. consummers(내경우 celery worker)는 이것을 순서대로 가져와서 처리한다. 만약 이런 저장 공간? 큐가 없다면 produser는 consumer가 앞서서 할당한 작업을 끝내기 전까지 마냥 기다려야 할것. 
