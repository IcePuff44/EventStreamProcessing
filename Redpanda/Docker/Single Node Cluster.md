We shall use the rpk container to run Redpanda in containers without interactions with Docker. RPK stands for RedPanda Keeper.

#Running on Docker#
docker run -d --pull=always --name=redpanda-1 --rm -p 9092:9092 -p 9644:9644 docker.vectorized.io/vectorized/redpanda:latest redpanda start --overprovisioned --smp 1  --memory 1G --reserve-memory 0M --node-id 0 --check=false

```
Streaming
Creating a topic:
docker exec -it redpanda-1 rpk topic create intern_chat --brokers=localhost:9092

Write messages to the topic:
docker exec -it redpanda-1 rpk topic produce intern_chat --brokers=localhost:9092
Each message can be separated by pressing “enter”

Consume messages in the topic:
docker exec -it redpanda-1 rpk topic consume intern_chat --brokers=localhost:9092
