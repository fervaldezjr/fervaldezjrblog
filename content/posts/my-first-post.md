---
title: "Utilizando RabbitMQ para la comunicación entre servicios"
slug: utilizando-rabbitmq-para-la-comunicacion-entre-servicios
description: Ejemplo de como puede utilizarse RabbitMQ para la comunicación entre dos servicios.
date: 2024-10-23T13:25:26+02:00
type: page
draft: false
showmetalinks: false
params:
  author: Fernando Valdez
menu:
  footer:
    name: About
    weight: 999
categories: ["Event-Driven Architecture", "RabbitMQ"]
tags: null
series: null
---

## Introducción

Cuando trabajamos con múltiples microservicios que necesitan comunicarse entre sí, [RabbitMQ](https://www.rabbitmq.com/) es una herramienta excelente para gestionar la mensajería entre ellos.

A continuación, enseñaré uno de los posibles flujos de trabajo básico utilizando esta [cola de mensajería](https://aws.amazon.com/es/message-queue/#:~:text=Una%20cola%20de%20mensajes%20es,sola%2C%20por%20un%20solo%20consumidor.) y como ejemplo usaré un sistema de comercio electrónico en el que tenemos un microservicio encargado de gestionar pedidos y otro encargado de notificar a los usuarios.

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
