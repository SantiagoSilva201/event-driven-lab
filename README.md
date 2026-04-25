# Laboratorio: Microservicios con Spring Boot y RabbitMQ

## Descripción

Este laboratorio implementa una arquitectura basada en eventos utilizando dos microservicios desarrollados con Spring Boot que se comunican mediante RabbitMQ.

El objetivo es demostrar cómo desacoplar servicios usando mensajería asíncrona y Docker para su despliegue.


## Arquitectura

El flujo del sistema es el siguiente:

Cliente → Producer → RabbitMQ → Consumer
1. El cliente envía una petición HTTP al productor
2. El productor publica un mensaje en RabbitMQ
3. RabbitMQ enruta el mensaje a una cola
4. El consumidor recibe y procesa el mensaje

## Tecnologías usadas

- Spring Boot 3.5.0
- Java 17
- RabbitMQ
- Docker
- Docker Compose
- Maven

## Estructura del proyecto

event-driven-lab/
├── producer-service/
├── consumer-service/
├── docker-compose.yml
└── .devcontainer/


## Cómo ejecutar

### 1. Clonar el repositorio

```
git clone https://github.com/SantiagoSilva201/event-driven-lab.git
cd event-driven-lab

```
### 2. Levantar los servicios

```
docker-compose up -d

```
### 3. Esperar 30 segundos

```
sleep 30

```

### 4. Probar enviando un mensaje

```
curl -X POST "http://localhost:8080/api/messages/send?message=HolaMundo"

```

### 5. Verificar que el consumidor recibió el mensaje

```
docker-compose logs consumer

```

## Endpoints

Método:POST            
URL:/api/messages/send?message=texto
Descripción: Enviar mensaje

## Comandos útiles

1. docker-compose up -d: Iniciar servicios
2. docker-compose down: Detener servicios
3. docker-compose ps: Ver estado
4. docker-compose logs -f: Ver logs
5. docker-compose logs consumer: Logs del consumidor

## Estado del proyecto

Productor funcionando

Consumidor funcionando

RabbitMQ funcionando

Comunicación exitosa

## Conclusión

Este laboratorio demuestra cómo implementar comunicación asíncrona entre microservicios utilizando RabbitMQ, permitiendo una arquitectura desacoplada y escalable.