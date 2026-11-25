# Message queues and Kafka

Queues decouple producers from consumers: absorb spikes, retry failures, let services evolve separately.

**Kafka concepts**
- **Topic** split into **partitions**: ordered, append-only logs.
- **Key** decides the partition, so all events for `order_42` stay in order.
- **Consumer group**: each partition is read by one consumer in the group. Max useful consumers = number of partitions.
- **Offset**: a consumer's position; committed after processing.
- Messages are kept for a retention period, so they can be replayed.

**Delivery:** usually *at-least-once*, so consumers must be **idempotent** (dedupe by event ID).

| Use Kafka for | Use RabbitMQ/SQS for |
|---|---|
| event streams, replay, high throughput | task queues, per-message routing and acks |
