# eSports Challenge League – Plataforma de Pronósticos Competitivos de eSports
### CS 2031 – Desarrollo Basado en Plataforma
### Integrantes
- Luciano Gabriel Rivera Valentín – 202410149
- Aaron Adriano Romano Castro – 202410322
- Anthony Yair Caypane Ramírez – 202410690
- Pablo Mario Rodríguez Poémape – 202410047
- José Fabricio Cruz Trejo – 202420083

## 📌 Índice
1. Introducción
2. Identificación del Problema
3. Descripción de la Solución
4. Funcionalidades Implementadas
5. Tecnologías Utilizadas
6. Modelo de Entidades
7. Testing y Manejo de Errores
8. Medidas de Seguridad Implementadas
9. Eventos y Asincronía
10. GitHub & Management
11. Conclusión
12. Apéndices

## 1. Introducción
### Contexto
El crecimiento del ecosistema de eSports ha generado una audiencia global de millones de fanáticos. Sin embargo, pocas plataformas permiten realizar pronósticos sin dinero y de forma amigable. Nuestra solución busca cubrir ese vacío.

### Objetivos del Proyecto
- Permitir pronósticos sobre torneos.
- Otorgar puntos por predicciones correctas.
- Gestionar rankings y recompensas.
- Integrar APIs oficiales de eSports.
- Implementar un backend seguro y escalable.

## 2. Identificación del Problema
### Descripción del Problema
No existen plataformas accesibles para pronosticar resultados de eSports sin apuestas monetarias.

### Justificación
El proyecto promueve una competencia sana, gamificada y sin riesgos financieros.

## 3. Descripción de la Solución
Creamos **eSports Challenge League**, una plataforma donde los usuarios predicen resultados, obtienen puntos, revisan rankings y desbloquean premios digitales.

## 4. Funcionalidades Implementadas
- Registro/Login con JWT.
- Listado de torneos.
- Realización de pronósticos.
- Cálculo automático de puntos.
- Ranking global.
- Premios digitales.
- Historial de predicciones.
- Email/SMS notificando eventos importantes.

## 5. Tecnologías Utilizadas
- Java 17, Spring Boot 3, Maven
- Spring Web, Security, JPA, Validation
- PostgreSQL, TestContainers
- SendGrid, Twilio
- Riot Games API, Esports API
- GitHub Projects + Actions, Docker

## 6. Modelo de Entidades
### Entidades
- **User**
- **Role**
- **Tournament**
- **Prediction**
- **MatchResult**
- **Points**
- **Ranking**
- **Reward**
- **UserRewards**
- **UserTournament**

### Relaciones
- User 1:N Predictions
- Tournament 1:N Predictions
- User 1:1 Ranking
- User M:N Rewards
- User M:N Tournaments

## 7. Testing y Manejo de Errores
### Testing
- Unit tests (servicios)
- Repository tests (DataJpaTest)
- Integration tests (MockMvc)
- TestContainers con PostgreSQL real

### Manejo de Errores
GlobalExceptionHandler maneja:
- NotFound
- InvalidPrediction
- Conflict
- Unauthorized
- Validaciones

## 8. Medidas de Seguridad Implementadas
- JWT completo
- Roles (USER, ADMIN)
- BCrypt
- Validaciones de entrada
- Prevención de SQLi y XSS
- CORS configurado

## 9. Eventos y Asincronía
### Eventos
- PredictionCreatedEvent → email
- ResultsUpdatedEvent → recálculo de puntos
- UserRewardAssignedEvent → SMS

### Asincronía
- @Async + @EnableAsync
- Procesamiento paralelo de cálculos

## 10. GitHub & Management
- GitHub Projects con Kanban
- Issues por tarea
- Ramas feature/*
- GitHub Actions: build + test

## 11. Conclusión
El backend cumple todos los requisitos del curso: seguridad, arquitectura limpia, eventos asincrónicos, integración con APIs y pruebas completas.

## 12. Apéndices
### Licencia
MIT License

### Referencias
- Riot Games API
- The Esports API
- Spring Boot Docs
- Twilio / SendGrid Docs
