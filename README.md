# Demo Spring Boot Application (Java 25, Maven, PostgreSQL)

This is a minimal Spring Boot sample application configured for Java 25, Maven, and PostgreSQL.

Files:
- `pom.xml` - Maven configuration
- `src/main/java/com/example/demo` - application sources
- `src/main/resources/application.properties` - DB configuration

Quick start

1. Ensure Java 25 JDK and Maven are installed and on PATH. If Java 25 causes compatibility issues, use Java 21 LTS and update `pom.xml`.

2. Start PostgreSQL locally or via Docker:

```powershell
# Run a PostgreSQL container (local testing)
docker run --rm -e POSTGRES_USER=demo_user -e POSTGRES_PASSWORD=demo_pass -e POSTGRES_DB=demo_db -p 5432:5432 postgres:15
```

3. Build the project:

```powershell
mvn -DskipTests package
```

4. Run the app:

```powershell
mvn spring-boot:run
# or
java -jar target/demo-0.0.1-SNAPSHOT.jar
```

5. Smoke test endpoint:

```powershell
Invoke-RestMethod http://localhost:8080/api/hello
```

Notes

- `spring.jpa.hibernate.ddl-auto=update` is for development only; switch to proper migrations (Flyway/Liquibase) for production.
- If the build fails due to Java 25 incompatibility with some plugins, change `<java.version>` in `pom.xml` to `21` and the `maven-compiler-plugin` `<release>` accordingly.
