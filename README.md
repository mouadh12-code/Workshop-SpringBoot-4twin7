# Workshop Spring Boot – TP Foyer (4TWIN7)

A Spring Boot workshop completed in class at **ESPRIT** (4TWIN7, academic year 2025–2026), guided by our teacher. It is a REST API for managing a university dormitory ("foyer"): dorms, blocks, rooms, students and room reservations.

> Team project carried out with [Zaineb Messaoudi](https://github.com/Zaineb-Messaoudi/workshop-springboot-4twin7-). Original repository linked for credit.

## Features

- CRUD operations for **Foyer, Bloc, Chambre, Etudiant, Reservation, Universite**
- Business endpoints: assign/unassign a block to a dorm, assign/unassign a room to a reservation, create a room with its reservation, find a room by student CIN
- Custom queries on blocks (not assigned, capacity above 30, name starting with "A")
- Layered architecture: controllers, services (interface + implementation), repositories, entities
- DTOs and **MapStruct** mapping
- **AOP** logging aspects (`LoggingAspect`, `LoggingAspectAround`)
- API documentation with **Swagger / OpenAPI**
- Monitoring endpoints with **Spring Boot Actuator**

## Tech stack

| Tool | Version |
| --- | --- |
| Java | 21 |
| Spring Boot | 3.5.6 |
| Spring Web, Spring Data JPA (Hibernate) | – |
| MySQL | – |
| Lombok | 1.18.34 |
| MapStruct | 1.5.5 |
| springdoc-openapi (Swagger UI) | 2.1.0 |
| Maven (wrapper included) | – |

## Domain model

- A **Universite** has one **Foyer**
- A **Foyer** has many **Blocs**
- A **Bloc** has many **Chambres** (types: `SIMPLE`, `Double`, `TRIPLE`)
- A **Reservation** is linked to many **Etudiants**, and a **Chambre** has many **Reservations**

## Project structure

```
src/main/java/tn/esprit/tpfoyer/
├── config/          # AOP logging aspects
├── controller/      # REST controllers
├── DTO/             # DTOs and MapStruct mapper
├── entities/        # JPA entities and enum TypeChambre
├── repositories/    # Spring Data JPA repositories
├── services/        # Service interfaces and implementations
└── TpFoyerApplication.java
src/main/resources/application.properties
```

## Getting started

**Prerequisites:** JDK 21 and MySQL running on `localhost:3306`. Maven is not required, the wrapper is included.

```bash
# 1. Clone the repository
git clone https://github.com/mouadh12-code/workshop-springboot-4twin7.git

# 2. Go into the project folder
cd workshop-springboot-4twin7

# 3. Check the database settings in src/main/resources/application.properties
#    (default: user "root", empty password, database "tpfoyerdb" created automatically)

# 4. Run the application (Windows)
mvnw.cmd spring-boot:run

# 4. Run the application (Linux / macOS)
./mvnw spring-boot:run
```

The API starts on **http://localhost:8081/tpfoyer**.

- Swagger UI: http://localhost:8081/tpfoyer/swagger-ui.html
- OpenAPI JSON: http://localhost:8081/tpfoyer/v3/api-docs

## Main endpoints

| Resource | Base path |
| --- | --- |
| Foyer | `/tpfoyer/foyercontroller` |
| Bloc | `/tpfoyer/bloccontroller` |
| Chambre | `/tpfoyer/chambrecontroller` |
| Etudiant | `/tpfoyer/etudiantcontroller` |
| Reservation | `/tpfoyer/reservationcontroller` |
| Universite | `/tpfoyer/universitecontroller` |

Open Swagger UI for the full list of routes and request formats.

## Extra documentation

Notes on HTTP status codes, common Spring exceptions, Spring Scheduler and Spring AOP (in French) are in [docs/SPRING_NOTES.md](docs/SPRING_NOTES.md).

## Credits

Workshop carried out at ESPRIT School of Engineering with our teacher. Original repository by [Zaineb Messaoudi](https://github.com/Zaineb-Messaoudi/workshop-springboot-4twin7-), used and republished here with her permission.