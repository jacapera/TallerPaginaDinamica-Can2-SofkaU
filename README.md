# TallerPaginaDinamica-Can2-SofkaU

## Ejercicio caso práctico de una página dinámica

Juego de dados para múltiples jugadores.

Proyecto demo en donde se implementamos una separación de responsabilidades usando los conceptos de :
- Plantilla (vista)
- Lógica (controlador)
- Datos (Modelo)

Se debe tener un sistema orientado a Rest, para esto se debe tener en cuenta lo siguiente:

## 1. Request de creación de juego, con su respectivo formulario:
POST http://localhost:8080/createGame

BODY:
{
  "id": "fffff-ggg-jjjjj",
  "type": "",
  "gamers": [
    "Raul Andres",
    "Pedro",
    "Juan"
  ]
}

## 2. Query para consultar el juego y su estado (listado de jugadores y estados como tal del juego)
GET http://localhost:8080/game/fffff-ggg-jjjjj

RESULT:
{
  "id": "fffff-ggg-jjjj",
  "gamers": {
    "5257b4d6-5c87-4871-93c3-b2b9ce04d706": {
      "id": "5257b4d6-5c87-4871-93c3-b2b9ce04d706",
      "name": "Raul Andres"
    },
    "8dda6205-f54c-4643-a017-71b6f0353319": {
      "id": "8dda6205-f54c-4643-a017-71b6f0353319",
      "name": "Juan"
    },
    "e5834d8e-5195-41fc-993e-c731dbce4fab": {
      "id": "e5834d8e-5195-41fc-993e-c731dbce4fab",
      "name": "Pedro"
    }
  },
  "inProgress": false,
  "winner": {
    "id": "e5834d8e-5195-41fc-993e-c731dbce4fab",
    "name": "Pedro"
  }
}

## 3. Query para determinar el ganador del juego(una vista con el ganador)
GET http://localhost:8080/game/fffff-ggg-jjjjj/winner

RESULT:
{
  "id": "e5834d8e-5195-41fc-993e-c731dbce4fab",
  "name": "Pedro"
}

## 4. Request para iniciar el juego con la apuesta por cada jugador (acción que permita iniciar el juego)
POST http://localhost:8080/startGame

BODY:
{
  "id": "fffff-ggg-jjjjj",
  "type": "",
  "gamerBet": {
      "5257b4d6-5c87-4871-93c3-b2b9ce04d706": 3,
      "8dda6205-f54c-4643-a017-71b6f0353319": 6,
      "e5834d8e-5195-41fc-993e-c731dbce4fab": 5
    }
}