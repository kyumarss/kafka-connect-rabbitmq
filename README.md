# Configuration

## RabbitMQSourceConnector

Connector is used to read from a RabbitMQ Queue or Topic.

```properties
name=connector1
tasks.max=1
connector.class=com.github.jcustenborder.kafka.connect.rabbitmq.RabbitMQSourceConnector

# Set these required values
```

| Name                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Type    | Default   | Valid Values | Importance |
|--------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|-----------|--------------|------------|
| rabbitmq.automatic.recovery.enabled  | Enables or disables automatic connection recovery. See [ConnectionFactory.setAutomaticRecoveryEnabled(boolean)](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/ConnectionFactory.html#setAutomaticRecoveryEnabled-boolean-)                                                                                                                                                                                                                                                                                                                                                    | boolean | false     |              | high       |
| rabbitmq.connection.timeout.ms       | Connection TCP establishment timeout in milliseconds. zero for infinite. See [ConnectionFactory.setConnectionTimeout(int)](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/ConnectionFactory.html#setConnectionTimeout-int-)                                                                                                                                                                                                                                                                                                                                                    | int     | 60000     |              | high       |
| rabbitmq.handshake.timeout.ms        | The AMQP0-9-1 protocol handshake timeout, in milliseconds. See [ConnectionFactory.setHandshakeTimeout(int)](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/ConnectionFactory.html#setHandshakeTimeout-int-)                                                                                                                                                                                                                                                                                                                                                                    | int     | 10000     |              | high       |
| rabbitmq.host                        | The RabbitMQ host to connect to. See [ConnectionFactory.setHost(java.lang.String)](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/ConnectionFactory.html#setHost-java.lang.String-)                                                                                                                                                                                                                                                                                                                                                                                            | string  | localhost |              | high       |
| rabbitmq.network.recovery.interval   | See [ConnectionFactory.setNetworkRecoveryInterval(long)](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/ConnectionFactory.html#setNetworkRecoveryInterval-long-)                                                                                                                                                                                                                                                                                                                                                                                                               | int     | 0         |              | high       |
| rabbitmq.password                    | The password to authenticate to RabbitMQ with. See [ConnectionFactory.setPassword(java.lang.String)](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/ConnectionFactory.html#setPassword-java.lang.String-)                                                                                                                                                                                                                                                                                                                                                                      | string  | guest     |              | high       |
| rabbitmq.port                        | The RabbitMQ port to connect to. See [ConnectionFactory.setPort(int)](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/ConnectionFactory.html#setPort-int-)                                                                                                                                                                                                                                                                                                                                                                                                                      | int     | 5672      |              | high       |
| rabbitmq.requested.channel.max       | Initially requested maximum channel number. Zero for unlimited. See [ConnectionFactory.setRequestedChannelMax(int)](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/ConnectionFactory.html#setRequestedChannelMax-int-)                                                                                                                                                                                                                                                                                                                                                         | int     | 0         |              | high       |
| rabbitmq.requested.frame.max         | Initially requested maximum frame size, in octets. Zero for unlimited. See [ConnectionFactory.setRequestedFrameMax(int)](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/ConnectionFactory.html#setRequestedFrameMax-int-)                                                                                                                                                                                                                                                                                                                                                      | int     | 0         |              | high       |
| rabbitmq.requested.heartbeat.seconds | Set the requested heartbeat timeout. Heartbeat frames will be sent at about 1/2 the timeout interval. If server heartbeat timeout is configured to a non-zero value, this method can only be used to lower the value; otherwise any value provided by the client will be used. See [ConnectionFactory.setRequestedHeartbeat(int)](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/ConnectionFactory.html#setRequestedHeartbeat-int-)                                                                                                                                            | int     | 60        |              | high       |
| rabbitmq.shutdown.timeout.ms         | Set the shutdown timeout. This is the amount of time that Consumer implementations have to continue working through deliveries (and other Consumer callbacks) after the connection has closed but before the ConsumerWorkService is torn down. If consumers exceed this timeout then any remaining queued deliveries (and other Consumer callbacks, *including* the Consumer's handleShutdownSignal() invocation) will be lost. See [ConnectionFactory.setShutdownTimeout(int)](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/ConnectionFactory.html#setShutdownTimeout-int-) | int     | 10000     |              | high       |
| rabbitmq.topology.recovery.enabled   | Enables or disables topology recovery. See [ConnectionFactory.setTopologyRecoveryEnabled(boolean)](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/ConnectionFactory.html#setTopologyRecoveryEnabled-boolean-)                                                                                                                                                                                                                                                                                                                                                                  | boolean | false     |              | high       |
| rabbitmq.username                    | The username to authenticate to RabbitMQ with. See [ConnectionFactory.setUsername(java.lang.String)](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/ConnectionFactory.html#setUsername-java.lang.String-)                                                                                                                                                                                                                                                                                                                                                                      | string  | guest     |              | high       |
| rabbitmq.virtual.host                | The virtual host to use when connecting to the broker. See [ConnectionFactory.setVirtualHost(java.lang.String)](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/ConnectionFactory.html#setVirtualHost-java.lang.String-)                                                                                                                                                                                                                                                                                                                                                        | string  | /         |              | high       |


# Schemas

## com.github.jcustenborder.kafka.connect.rabbitmq.BasicProperties.HeaderValue

Used to store the value of a header value. The `type` field stores the type of the data and the corresponding field to read the data from.

| Name    | Optional | Schema                                                                                                  | Default Value | Documentation                                                                                                                             |
|---------|----------|---------------------------------------------------------------------------------------------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| type    | false    | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING)   |               | Used to define the type for the HeaderValue. This will define the corresponding field which will contain the value in it's original type. |
| INT8    | true     | [Int8](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#INT8)       |               | Storage for when the `type` field is set to `INT8`. Null otherwise.                                                                       |
| INT16   | true     | [Int16](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#INT16)     |               | Storage for when the `type` field is set to `INT16`. Null otherwise.                                                                      |
| INT32   | true     | [Int32](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#INT32)     |               | Storage for when the `type` field is set to `INT32`. Null otherwise.                                                                      |
| INT64   | true     | [Int64](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#INT64)     |               | Storage for when the `type` field is set to `INT64`. Null otherwise.                                                                      |
| FLOAT32 | true     | [Float32](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#FLOAT32) |               | Storage for when the `type` field is set to `FLOAT32`. Null otherwise.                                                                    |
| FLOAT64 | true     | [Float64](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#FLOAT64) |               | Storage for when the `type` field is set to `FLOAT64`. Null otherwise.                                                                    |
| BOOLEAN | true     | [Boolean](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#BOOLEAN) |               | Storage for when the `type` field is set to `BOOLEAN`. Null otherwise.                                                                    |
| STRING  | true     | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING)   |               | Storage for when the `type` field is set to `STRING`. Null otherwise.                                                                     |
| BYTES   | true     | [Bytes](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#BYTES)     |               | Storage for when the `type` field is set to `BYTES`. Null otherwise.                                                                      |

## com.github.jcustenborder.kafka.connect.rabbitmq.Envelope

Encapsulates a group of parameters used for AMQP's Basic methods. See [Envelope](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/Envelope.html)

| Name        | Optional | Schema                                                                                                  | Default Value | Documentation                                                                                                                                                                                                      |
|-------------|----------|---------------------------------------------------------------------------------------------------------|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| deliveryTag | false    | [Int64](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#INT64)     |               | The delivery tag included in this parameter envelope. See [Envelope.getDeliveryTag()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/Envelope.html#getDeliveryTag--)   |
| isRedeliver | false    | [Boolean](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#BOOLEAN) |               | The redelivery flag included in this parameter envelope. See [Envelope.isRedeliver()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/Envelope.html#isRedeliver--)      |
| exchange    | true     | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING)   |               | The name of the exchange included in this parameter envelope. See [Envelope.getExchange()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/Envelope.html#getExchange--) |
| routingKey  | true     | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING)   |               | The routing key included in this parameter envelope. See [Envelope.getRoutingKey()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/Envelope.html#getRoutingKey--)      |

## com.github.jcustenborder.kafka.connect.rabbitmq.BasicProperties

Corresponds to the [BasicProperties](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/BasicProperties.html)

| Name            | Optional | Schema                                                                                                                                                                                                                                                                      | Default Value | Documentation                                                                                                                                                                                                            |
|-----------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| contentType     | true     | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING)                                                                                                                                                                       |               | The value in the contentType field. See [BasicProperties.getContentType()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/BasicProperties.html#getContentType--)             |
| contentEncoding | true     | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING)                                                                                                                                                                       |               | The value in the contentEncoding field. See [BasicProperties.getContentEncoding()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/BasicProperties.html#getContentEncoding--) |
| headers         | false    | Map of <[String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING), [com.github.jcustenborder.kafka.connect.rabbitmq.BasicProperties.HeaderValue](#com.github.jcustenborder.kafka.connect.rabbitmq.BasicProperties.HeaderValue)> |               |                                                                                                                                                                                                                          |
| deliveryMode    | true     | [Int32](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#INT32)                                                                                                                                                                         |               | The value in the deliveryMode field. [BasicProperties.html.getDeliveryMode()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/BasicProperties.html#getDeliveryMode--)         |
| priority        | true     | [Int32](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#INT32)                                                                                                                                                                         |               | The value in the priority field. [BasicProperties.getPriority()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/BasicProperties.html#getPriority--)                          |
| correlationId   | true     | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING)                                                                                                                                                                       |               | The value in the correlationId field. See [BasicProperties.getCorrelationId()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/BasicProperties.html#getCorrelationId--)       |
| replyTo         | true     | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING)                                                                                                                                                                       |               | The value in the replyTo field. [BasicProperties.getReplyTo()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/BasicProperties.html#getReplyTo--)                             |
| expiration      | true     | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING)                                                                                                                                                                       |               | The value in the expiration field. See [BasicProperties.getExpiration()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/BasicProperties.html#getExpiration--)                |
| messageId       | true     | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING)                                                                                                                                                                       |               | The value in the messageId field. [BasicProperties.getMessageId()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/BasicProperties.html#getMessageId--)                       |
| timestamp       | true     | [Timestamp](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Timestamp.html)                                                                                                                                                                             |               | The value in the timestamp field. [BasicProperties.getTimestamp()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/BasicProperties.html#getTimestamp--)                       |
| type            | true     | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING)                                                                                                                                                                       |               | The value in the type field. [BasicProperties.getType()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/BasicProperties.html#getType--)                                      |
| userId          | true     | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING)                                                                                                                                                                       |               | The value in the userId field. [BasicProperties.getUserId()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/BasicProperties.html#getUserId--)                                |
| appId           | true     | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING)                                                                                                                                                                       |               | The value in the appId field. [BasicProperties.getAppId()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/BasicProperties.html#getAppId--)                                   |
| clusterId       | true     | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING)                                                                                                                                                                       |               | [AMQP.BasicProperties.getClusterId()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/AMQP.BasicProperties.html#getClusterId--)                                               |

## com.github.jcustenborder.kafka.connect.rabbitmq.Message

Message as it is delivered to the [RabbitMQ Consumer](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/Consumer.html#handleDelivery-java.lang.String-com.rabbitmq.client.Envelope-com.rabbitmq.client.AMQP.BasicProperties-byte:A-) 

| Name            | Optional | Schema                                                                                                                              | Default Value | Documentation                                                                                                                                                                              |
|-----------------|----------|-------------------------------------------------------------------------------------------------------------------------------------|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| consumerTag     | false    | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING)                               |               | The consumer tag associated with the consumer                                                                                                                                              |
| envelope        | false    | [com.github.jcustenborder.kafka.connect.rabbitmq.Envelope](#com.github.jcustenborder.kafka.connect.rabbitmq.Envelope)               |               | Encapsulates a group of parameters used for AMQP's Basic methods. See [Envelope](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/Envelope.html) |
| basicProperties | false    | [com.github.jcustenborder.kafka.connect.rabbitmq.BasicProperties](#com.github.jcustenborder.kafka.connect.rabbitmq.BasicProperties) |               | Corresponds to the [BasicProperties](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/BasicProperties.html)                                      |
| body            | false    | [Bytes](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#BYTES)                                 |               | The message body (opaque, client-specific byte array)                                                                                                                                      |

## com.github.jcustenborder.kafka.connect.rabbitmq.MessageKey

Key used for partition assignment in Kafka.

| Name      | Optional | Schema                                                                                                | Default Value | Documentation                                                                                                                                                                                      |
|-----------|----------|-------------------------------------------------------------------------------------------------------|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| messageId | true     | [String](https://kafka.apache.org/0102/javadoc/org/apache/kafka/connect/data/Schema.Type.html#STRING) |               | The value in the messageId field. [BasicProperties.getMessageId()](https://www.rabbitmq.com/releases/rabbitmq-java-client/current-javadoc/com/rabbitmq/client/BasicProperties.html#getMessageId--) |


