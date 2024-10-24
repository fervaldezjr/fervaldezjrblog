+++
title = "Utilizando RabbitMQ para la comunicación en sistemas distribuidos"
date = "2024-10-24"
tags = ["rabbitmq", "event-driven-architecture"]
+++

Enseñaré uno de los posibles flujos de trabajo básico utilizando [RabbitMQ](https://www.rabbitmq.com/) como [cola de mensajería](https://aws.amazon.com/es/message-queue/#:~:text=Una%20cola%20de%20mensajes%20es,sola%2C%20por%20un%20solo%20consumidor.) para la comunicación entre múltiples microservicios y como ejemplo usaré un sistema de comercio electrónico en el que tenemos un microservicio encargado de **gestionar pedidos** y otro encargado de **notificar a los usuarios**.

<!--more-->

## Primeros pasos

```goat
+-----------+              +-------------+              +-------------+
|  Cliente  |              | OrderService|              |  RabbitMQ   |
+-----------+              +-------------+              +-------------+
     |                             |                             |
     | Realiza un pedido           |                             |
     +---------------------------> |                             |
                                   |                             |
                                   | Publica OrderPlacedEvent    |
                                   +---------------------------> |
                                                                 |
                                                                 | Evento almacenado en
                                                                 | orders.order.placed.queue
                                                                 +--------------------------->
```
