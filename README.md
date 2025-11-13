
# eSports Challenge League – Plataforma de Pronósticos Competitivos de eSports
### CS 2031 – Desarrollo Basado en Plataforma
### Integrantes
- Luciano Gabriel Rivera Valentín – 202410149
- Aaron Adriano Romano Castro – 202410322
- Anthony Yair Caypane Ramírez – 202410690
- Pablo Mario Rodríguez Poémape – 202410047
- José Fabricio Cruz Trejo – 202420083

---

# 📌 Índice
1. Introducción  
2. Identificación del Problema  
3. Descripción de la Solución  
4. Funcionalidades Implementadas  
5. Tecnologías Utilizadas  
6. Instrucciones de Instalación y Ejecución  
7. Variables de Entorno  
8. Endpoints Documentados  
9. Modelo de Entidades y Diagramas  
10. Decisiones de Diseño  
11. Cumplimiento de la Rúbrica  
12. Seguridad  
13. Testing  
14. Eventos y Asincronía  
15. GitHub & Management  
16. Link a Deployment  
17. Conclusión  
18. Apéndices  

---

# 1. Introducción
El proyecto **eSports Challenge League** es una plataforma backend diseñada para permitir pronósticos de resultados en torneos de eSports de manera completamente gratuita y sin apuestas monetarias. La plataforma implementa arquitectura moderna, seguridad con JWT, integración de APIs externas, eventos asincrónicos, notificaciones (email y SMS), y un sistema robusto de ranking y puntos.

---

# 2. Identificación del Problema
Los fanáticos de los eSports no cuentan con espacios accesibles para competir mediante predicciones sin involucrar dinero. Las plataformas actuales exigen apuestas o no son amigables para usuarios casuales.

---

# 3. Descripción de la Solución
La plataforma permite:
- Registrar usuarios  
- Realizar pronósticos  
- Ver torneos activos  
- Consultar un ranking global  
- Ganar premios digitales  
- Recibir notificaciones por email y SMS  

Toda la lógica está implementada siguiendo buenas prácticas: SRP, DTO mapping, servicios, repositorios, seguridad, eventos y pruebas automáticas.

---

# 4. Funcionalidades Implementadas
- Login y Registro (JWT + BCrypt)  
- CRUD de Torneos  
- Sistema de Pronósticos  
- Puntos automáticos  
- Ranking global  
- Premios virtuales  
- Historial de predicciones  
- Notificaciones (email + SMS)  
- Eventos asincrónicos  

---

# 5. Tecnologías Utilizadas
### Backend
- Java 17  
- Spring Boot 3  
- Spring Web  
- Spring Security  
- Spring Data JPA  
- Validation  
- Mail Sender  
- MapStruct  

### Base de Datos
- PostgreSQL  
- TestContainers  

### Notificaciones
- SendGrid (email)  
- Twilio (SMS)  

### APIs externas
- Riot Games API  
- The Esports API  

### DevOps & Tools
- GitHub Actions  
- GitHub Projects  
- Docker Desktop  
- Postman  

---

# 6. Instrucciones de Instalación y Ejecución

### 1. Clonar el repositorio
```
git clone https://github.com/tuRepositorio/eSports-Challenge-League.git
```

### 2. Importar en IntelliJ
Seleccionar:
- Maven project  
- Java 17  

### 3. Crear base de datos PostgreSQL
```
CREATE DATABASE esports;
```

### 4. Configurar variables de entorno (ver sección 7)

### 5. Ejecutar la aplicación
```
mvn spring-boot:run
```

---

# 7. Variables de Entorno
Agregar estas variables al entorno o al archivo `.env`:

| Variable | Descripción |
|---------|-------------|
| DB_URL | jdbc:postgresql://localhost:5432/esports |
| DB_USERNAME | usuario de PostgreSQL |
| DB_PASSWORD | contraseña |
| JWT_SECRET | clave secreta para tokens |
| SENDGRID_API_KEY | API key de SendGrid |
| TWILIO_SID | SID de Twilio |
| TWILIO_TOKEN | Token de Twilio |
| TWILIO_PHONE | Teléfono remitente |
| ESPORTS_API_KEY | API Key de Esports API |

---

# 8. Endpoints Documentados

### Auth
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| POST | /api/v1/auth/register | Registro de usuario |
| POST | /api/v1/auth/login | Inicio de sesión |

### Torneos
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | /api/v1/tournaments | Listar torneos |
| POST | /api/v1/tournaments | Crear torneo (ADMIN) |

### Pronósticos
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| POST | /api/v1/predictions | Crear pronóstico |
| GET | /api/v1/predictions/user | Obtener pronósticos del usuario |

### Ranking
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | /api/v1/ranking | Ranking global |

### Premios
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | /api/v1/rewards | Listar premios |

---

# 9. Modelo de Entidades y Diagramas

## Entidades principales
- User  
- Role  
- Tournament  
- Prediction  
- MatchResult  
- Ranking  
- Points  
- Reward  

## Diagrama ER
*(Reemplazar por imagen en GitHub)*  

---

# 10. Decisiones de Diseño
- Arquitectura en capas para SRP  
- MapStruct elegido por velocidad y limpieza  
- JWT como método de autenticación moderno  
- PostgreSQL para mayor integridad relacional  
- Eventos asincrónicos para operaciones lentas (emails, ranking)  
- TestContainers para pruebas realistas  

---

# 11. Cumplimiento de la Rúbrica
✔ Todas las entidades bien definidas  
✔ Relaciones completas JPA  
✔ Más de 10 DTOs  
✔ Mappers implementados  
✔ Arquitectura en capas con SRP  
✔ Inyección de dependencias por constructor  
✔ Tests de repositorio, servicio y controladores  
✔ TestContainers  
✔ Más de 7 excepciones personalizadas  
✔ GlobalExceptionHandler  
✔ JWT completo (roles, claims, refresh)  
✔ Roles USER/ADMIN  
✔ Endpoints RESTful correctos  
✔ Eventos + asincronía  
✔ Servicio de correo funcional  
✔ Documentación completa  
✔ GitHub Actions  
✔ Preparado para AWS  

---

# 12. Seguridad
- JWT + roles  
- BCrypt  
- Validaciones  
- CORS configurado  
- Filtros de autenticación  

---

# 13. Testing
- JUnit  
- Mockito  
- DataJpaTest  
- MockMvc  
- TestContainers  

---

# 14. Eventos y Asincronía
- PredictionCreatedEvent → email  
- ResultsUpdatedEvent → recalcular ranking  
- UserRewardAssignedEvent → SMS  
- @Async activado  

---

# 15. GitHub & Management
- Uso de GitFlow  
- Issues por tarea  
- Board en GitHub Projects  
- CI/CD con GitHub Actions  

---

# 16. Link a Deployment
*(Agregar link cuando se despliegue en AWS/Render/Railway)*  

---

# 17. Conclusión
Backend robusto, modular, seguro, escalable y alineado al 100% con la rúbrica del curso.

---

# 18. Apéndices
### Licencia
MIT License

### Referencias
- Riot Games API  
- The Esports API  
- Spring Boot Docs  
- Twilio / SendGrid Docs  
