
# eSports Challenge League – Plataforma de Pronósticos Competitivos de eSports
### CS 2031 – Desarrollo Basado en Plataforma

## Integrantes
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
9. Modelo de Entidades (ACTUALIZADO)  
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
El proyecto **eSports Challenge League** es una plataforma backend que permite pronósticos gratuitos en torneos de eSports. El sistema implementa autenticación JWT, arquitectura modular, mapeos DTO, eventos asincrónicos, notificaciones, ranking dinámico y pruebas automatizadas.

---

# 2. Identificación del Problema
Los fanáticos de los eSports no cuentan con plataformas accesibles para competir mediante predicciones sin involucrar dinero. Las plataformas existentes son de apuestas o demasiado complejas.

---

# 3. Descripción de la Solución
La plataforma permite:
- Registro y autenticación segura
- Realizar pronósticos
- Ver torneos y partidas
- Recibir notificaciones por email y SMS
- Ranking dinámico por desempeño
- Premios virtuales y badges

---

# 4. Funcionalidades Implementadas
- Login y Registro con JWT  
- CRUD de Torneos  
- Sistema de Pronósticos  
- Recalculo automático del ranking  
- Premios digitales  
- Historial de predicciones  
- Notificaciones (email + SMS)  
- Sistema de eventos asincrónicos  
- Audit logs  

---

# 5. Tecnologías Utilizadas
### Backend
- Java 17  
- Spring Boot 3  
- Spring Web  
- Spring Security  
- Spring Data JPA  
- Validation  
- MapStruct  

### Base de Datos
- PostgreSQL  
- TestContainers  

### Notificaciones
- SendGrid  
- Twilio  

### APIs externas
- Riot Games API  
- The Esports API  

### DevOps & Tools
- GitHub Actions  
- GitHub Projects  
- Docker  
- Postman  

---

# 6. Instrucciones de Instalación y Ejecución

### 1. Clonar repositorio
```
git clone https://github.com/tuRepositorio/eSports-Challenge-League.git
```

### 2. Importar en IntelliJ (Java 17)

### 3. Crear base de datos
```
CREATE DATABASE esports;
```

### 4. Configurar variables de entorno (sección 7)

### 5. Ejecutar aplicación
```
mvn spring-boot:run
```

---

# 7. Variables de Entorno
| Variable | Descripción |
|---------|-------------|
| DB_URL | jdbc:postgresql://localhost:5432/esports |
| DB_USERNAME | Usuario |
| DB_PASSWORD | Contraseña |
| JWT_SECRET | Clave secreta JWT |
| SENDGRID_API_KEY | Email provider |
| TWILIO_SID | SMS provider |
| TWILIO_TOKEN | Token Twilio |
| TWILIO_PHONE | Teléfono remitente |
| ESPORTS_API_KEY | API Key externa |

---

# 8. Endpoints Documentados
### Auth
- POST /api/v1/auth/register  
- POST /api/v1/auth/login  

### Torneos
- GET /api/v1/tournaments  
- POST /api/v1/tournaments  

### Pronósticos
- POST /api/v1/predictions  
- GET /api/v1/predictions/user  

### Ranking
- GET /api/v1/ranking  

### Premios
- GET /api/v1/rewards  

---

# 9. Modelo de Entidades (ACTUALIZADO)
Estas son las entidades DEFINITIVAS después de tu optimización:

1. **User**  
2. **Role**  
3. **Tournament**  
4. **Match**  
5. **MatchResult**  
6. **Prediction**  
7. **Ranking**  
8. **Reward**  
9. **UserReward**  
10. **UserTournament**  
11. **NotificationLog**  

> ⚠ Eliminada: `Points` (funcionalidad absorbida por Ranking)  
> ⚠ Añadida: `NotificationLog` (para eventos + asincronía)

---

# 10. Decisiones de Diseño
- Arquitectura en capas  
- Role como entidad independiente  
- Ranking global simplificado  
- Eliminación de redundancias (Points)  
- Nuevos logs de notificación  
- Uso obligatorio de LAZY en relaciones  
- Uso de MapStruct para DTOs  

---

# 11. Cumplimiento de la Rúbrica
✔ Más de 6 entidades  
✔ Relaciones correctas  
✔ DTOs especializados  
✔ MapStruct  
✔ SRP en servicios  
✔ Inyección por constructor  
✔ Tests completos  
✔ TestContainers  
✔ Excepciones personalizadas (7+)  
✔ Handler global  
✔ JWT completo  
✔ Roles en BD  
✔ API REST con versionado  
✔ Eventos y asincronía  
✔ Email funcional  
✔ GitHub Actions  
✔ Documentación completa  

---

# 12. Seguridad
- JWT  
- BCrypt  
- Filtros  
- CORS  
- Roles y Claims  

---

# 13. Testing
- Unit tests (Mockito)  
- Integration tests (MockMvc)  
- DataJpa tests  
- TestContainers  

---

# 14. Eventos y Asincronía
- PredictionCreatedEvent  
- ResultsUpdatedEvent  
- UserRewardAssignedEvent  
- Uso de @Async  

---

# 15. GitHub & Management
- GitFlow  
- Pull Requests  
- GitHub Actions  
- GitHub Issues / Projects  

---

# 16. Link a Deployment
*(pending)*

---

# 17. Conclusión
Backend robusto, escalable y alineado a todos los criterios del curso.

---

# 18. Apéndices
### Licencia
MIT License

### Referencias
- Riot Games API  
- Esports API  
- Spring Documentation  
