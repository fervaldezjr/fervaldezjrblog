+++
date = '2024-11-12T18:15:00+01:00'
draft = false
title = 'Definiciones Técnicas del día a día'
tags = ['career', 'definitions']
+++

Algunas notas sueltas que fuí encontrando en viejas libretas sobre pequeñas dudas, conceptos, definiciones y comentarios que me ayudaron mucho en mi camino como desarrollador.

Como el aprendizaje es continuo espero que este artículo siga creciendo, también es bienvenido cualquier comentario para complementar dichas notas o crear un documento especifico.

<!--more-->

[Versión 0.0.1]

## Tabla de Contenido

1. [Gradle Wrapper](#gradle-wrapper)
1. [Architecture Decision Records](#architecture-decision-records)
1. [Liquibase](#liquibase)
1. [Atajos Útiles de Bash](#atajos-utiles-de-bash)

---

# Gradle Wrapper

[Gradlew Wrapper](https://docs.gradle.org/current/userguide/gradle_wrapper.html) se usa para ejecutar [Gradle](https://docs.gradle.org/current/userguide/userguide.html) sin tener que instalarlo en tu computadora.
De esta manera todos los integrantes del equipo no van a tener problemas de compatibilidad ya que tendrán la misma versión porque esta **wrappeada** en el proyecto.

_Referencias y artículos relacionados_

- [Gradle Wikipedia](https://es.wikipedia.org/wiki/Gradle)

---

# Architecture Decision Records

También conocido como **ADR** es un registro de decisiones arquitectonicas junto con su contexto y consecuencias.

_Ejemplo:_

## ADR 001 - Elección del framework frontend: React vs Vue.js

| Estado   | Autor           | Fecha      |
| -------- | --------------- | ---------- |
| Aprobado | Fernando Valdez | 12/11/2024 |

## Contexto

Estamos construyendo una aplicación web interactiva y necesitamos seleccionar un framework JavaScript para el frontend.

## Decisión tomada

Utilizaremos **React** para desarrollar el frontend de la aplicación.

## Justificación

- **Comunidad y soporte:** React tiene una comunidad más grande y recursos de soporte, lo que facilita resolver problemas y encontrar soluciones.
- **Integración con el ecosistema:** Ya usamos otras librerías que funcionan bien con React, como react-hook-form y NativeWind.
- **Facilidad de contratación:** Es más fácil encontrar desarrolladores con experiencia en React.

## Alternativas consideradas

- **Vue.js:** Menor curva de aprendizaje, pero menos usado en nuestra empresa.
- **Angular:** Complejo y no se ajusta bien a la arquitectura de nuestro proyecto.

## Consecuencias

- Tendremos más facilidad para integrar componentes existentes y bibliotecas de terceros.
- La curva de aprendizaje puede ser un poco mayor para los nuevos desarrolladores que no conocen React.

_Referencias y artículos relacionados_

- [ADR en GitHub y Plantillas](https://github.com/joelparkerhenderson/architecture-decision-record)

---

# Liquibase

[Liquibase](http://www.liquibase.org/) funciona como una especie de control de versiones para administrar y aplicar cambios en el modelo de base de datos desde línea de comandos. Es una librería hecha con Java y de código abierto.

En mi experiencia he utilizado archivos basados en texto (cuyo formato puede ser SQL, XML, JSON y YAML) llamados [changelogs](https://docs.liquibase.com/concepts/changelogs/home.html) para enumerar los cambios de la base de datos en orden secuencial.

_Ejemplo_

Archivo llamado: `db.changelog_001.1.yml`

```yaml
databaseChangeLog:
  - changeSet:
      id: 1_create-user-table
      author: fervaldezjr11@gmail.com
      changes:
        - createTable:
            tableName: user
            columns:
              - column:
                  name: id
                  type: int
                  autoIncrement: true
                  constraints:
                    primaryKey: true
              - column:
                  name: username
                  type: varchar(50)
                  constraints:
                    nullable: false
```

_Referencias y artículos relacionados_

- [¿Cómo funciona liquibase?](https://www.liquibase.com/how-liquibase-works)
- [Introducción a Liquibase](https://docs.liquibase.com/concepts/introduction-to-liquibase.html)

---

# Atajos Utiles de Bash

| Atajos              | Descripcción                                |
| ------------------- | ------------------------------------------- |
| `ctrl` + `A`        | Ir al inicio de la línea.                   |
| `ctrl` + `E`        | Ir al final de la línea.                    |
| `alt` + `<-` o `->` | Moverse por cada palabra.                   |
| `ctrl` + `U`        | Borrar todo antes del cursor.               |
| `ctrl` + `K`        | Borrar todo después del cursor.             |
| `tab`               | Autocompletado.                             |
| `!` + ./            | Buscar en el historial comandos utilizados. |
