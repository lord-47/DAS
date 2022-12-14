# [ADD-0002 Tipo de base de datos a utilizar]

* Status: [acepted]
* Date: [2022-11-07]

## Contexto y problemas a resolver

[Se necesitan guardar en la base de datos tanto órdenes de trabajo como el inventario del material existente]

## Requisitio de decisión

* [RF-004](../requisitos/RF-004.md)

## Opciones consideradas

* [Database-per-service](https://docs.aws.amazon.com/es_es/prescriptive-guidance/latest/modernization-data-persistence/database-per-service.html) : se usará el patrón Database-per-service, en el que cada microservicio tiene una base de datos independiente.
* [Shared-database-per-service](https://docs.aws.amazon.com/es_es/prescriptive-guidance/latest/modernization-data-persistence/shared-database.html): se usará el patrón Shared-database-per-service, en el que los microservicios comparten una base de datos.

## Decisiones tomadas

Opción elegida: "[Shared-database-per-service]", because[queremos garantizar la coherencia de los datos, y utilizar transacciones uniformes, ya que todos los microservicios operan sobre los mismos datos, por lo que nos ahorramos tener bases de datos repetidas.]

### Consecuencias positivas <!-- optional -->

* [Garantizar la coherencia de los datos]
* [Mantener y operar solo una base de datos.]
* [Utilizar transacciones que proporcionan atomicidad, uniformidad, aislamiento y durabilidad (ACID, por sus siglas en inglés).]

### Consecuencias negativas <!-- optional -->

* [Posible dificultad a la hora de crecer.]
* [Patrón difícil debido a las interdependencias entre sus microservicios existentes.]

## Pros y Contras de las Opciones

### [Shared-database-per-service]

* Bueno, porque [Permite mantener una sola base de datos]
* Bueno, porque [Permite garantizar la coherencia de los datos]
* Bueno, porque [Proporciona atomizidad]
* Malo, porque [Es más dificil de implementar]

### [Database-per-service]

* Bueno, porque [Permite descentralizar completamente los microservicios]
* Malo, porque [Debe administrar varias bases de datos relacionales y no relacionales]
