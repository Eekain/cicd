# Képzési folyamat:

1. Elméleti alapok: CI/CD
2. Groovy és Gradle
3. Build Java projekt esetén: Compile, Unit test, Package
4. Tesztlefedettség
5. Integrációs tesztek inmemory adatbázissal
6. Release (?)
7. Docker alapok
8. Integrációs tesztek valós adatbázissal
9. Csomagolás Docker image-be: 
	* Futtatás Docker image-ben
	* Futtatás Docker image-ben adatbázis& network használatával
	* Konténer futtatása Gradle-bpl
	* Layerelt Docker image
10. Build Docker image-ben
11. E2E tesztelés 
	* E2E tesztelés Docker Compose használatával
12. Jenkins bevezetése 
	* Pipeline 
	* Build number
13. SonarQube
	* Quality Gate és Quality Profile
	* Tesztlefedettség eredménye
14. Deploy artifact to Nexus
15. Deploy Docker image t Nexus
16. Pull and run Docker image from Nexus

## Második nap

Integrációs tesztek valós adatbázisok:

docker run
 -d 
 -e MARIADB_DATABASE=employees
 -e MARIADB_USER=employees
 -e MARIADB_PASSWORD=employees
 -e MARIADB_ALLOW_EMPTY_ROOT_PASSWORD=yes
 -p 3306:3306
 --name employees-mariadb mariadb

docker logs -f employees-mariadb

Futtatás:

docker exec -it employees-mariadb mysql 

Cloudban futtatható alkalmazások alapszabályai:
[The Twelve-Factor App](12factor.net)

Kellett beállítani a springhez dolgokat (liquibase)
* set SPRING_DATASOURCE_URL=jdbc:mariadb://localhost/employees
* set SPRING_DATASOURCE_USER=employees
* set SPRING_DATASOURCE_PASSWORD=employees

ezek után megfelelően elindul a Spring app a java -jar target\employees-1.0-SNAPSHOT.jar paranccsal

Érdemes nem csak a konténtert, de még az alkalmazást is "layerekre bontani"

Dockerben minden egyes copy parancs új "layert" hoz létre 

Dockerfile-on belül lehet meghatározni cache képet, ami a függőségeket letölti, és akkor a build nem minden újrafutásnál szenved vele
