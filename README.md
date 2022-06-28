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

