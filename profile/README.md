
# πΏFavieList
μΉ΄μΉ΄μ€ ν΄λΌμ°λ μ€μΏ¨μμ μ§νν λμ»€ κΈ°λ°μ 3-Tire νλ‘μ νΈ
* λͺ©ν : Front, Back, DBμ λ©ν° μ»¨νμ΄λλ‘ λμ»€ νκ²½μμ μλΉμ€λ₯Ό μ΄μ
* μλΉμ€ μ£Όμ  : κ΄μ¬μν λ¦¬λ·° μ¬μ΄νΈ
* μλΉμ€ κΈ°λ₯ : μν κ²μ, κ΄μ¬ λ±λ‘, λ¦¬λ·° CRUD

<br>

## π‘FavieList νμ΄μ§ μ μ
1. `192.168.56.103:3000` λ‘ μ μν©λλ€.
2. νμ κ°μμ μν΄ `Signup`μ ν΄λ¦­νμ¬ μ΄λν©λλ€.
3. `ID : test`, `Password : 1234`λ₯Ό μλ ₯νμ¬ νμ κ°μ & λ‘κ·ΈμΈμ μ§νν©λλ€.
<br>

![image](https://user-images.githubusercontent.com/73453283/204574236-36dff68b-06ee-4b26-a374-3d2a912e7791.png)

<br>
<br>

4. μΌκ° μν μμκ° 1μλΆν° 10μκΉμ§ λνλ©λλ€.
(μνμ§ν₯μμνμ openAPIλ₯Ό μ¬μ©ν¨μΌλ‘ ν΄λΉ μ¬μ΄νΈμ λ¬Έμ μ λ°λΌ μνμμκ° λ³΄μ΄μ§ μμ μ μμ΅λλ€)
<br>

![image](https://user-images.githubusercontent.com/73453283/204575486-6ee082d7-7c35-4971-9f79-f14aeab758c8.png)
<br>
<br>

5. κ²μμ°½μ ν΅ν΄ μνλ μνλ₯Ό κ²μν  μλ μμ΅λλ€.
<br>

![image](https://user-images.githubusercontent.com/73453283/204574357-570ccfcb-195f-48d8-8223-982a51178a13.png)
<br>
<br>

6. Add λ²νΌμ λλ₯΄λ©΄ [κ΄μ¬ μν λͺ©λ‘]μ μΆκ°ν  μ μμ΅λλ€.
* μ΄λ―Έ [κ΄μ¬ μν λͺ©λ‘]μ λ±λ‘λμ΄ μλ μνμ λν΄ Add λ²νΌμ λλ₯Ό μ μλμ κ°μ κ²½κ³ μ°½μ΄ μΆλ ₯λ©λλ€.<br>

![image](https://user-images.githubusercontent.com/73453283/204576365-08d5d462-c485-45c5-a370-336fe02c9841.png)
![image](https://user-images.githubusercontent.com/73453283/204576395-e21c094f-9dd4-4e09-8c76-92124e9c19c4.png)

<br>
<br>

7. λ©μΈ νμ΄μ§μ μ°μλ¨μ μμΉν ννΈ λ²νΌμ ν΄λ¦­νλ©΄ [κ΄μ¬ μν λͺ©λ‘]νμ΄μ§λ‘ μ΄λν  μ μμ΅λλ€.
* [κ΄μ¬ μν λͺ©λ‘]μΌλ‘ λ±λ‘λ μνλ€μ΄ λνλ©λλ€.

![image](https://user-images.githubusercontent.com/73453283/204574465-41267044-eaf7-407f-a7bc-3d7326f030ca.png)

<br>
<br>

8. μμ μ νμ κ³Ό μ½λ©νΈλ₯Ό μμ±νκ³  Reply λ²νΌμ ν΄λ¦­νλ©΄ ν΄λΉ μ λ³΄λ₯Ό μ μ₯ν  μ μμ΅λλ€.
* νμ κ³Ό μ½λ©νΈλ₯Ό μλ‘ μλ ₯νμ Reply λ²νΌμ ν΄λ¦­νλ©΄ μμ ν  μ μμ΅λλ€.
<br>

![image](https://user-images.githubusercontent.com/73453283/204574553-23de887c-4a86-45bc-9d90-7b245d279ccd.png)
![image](https://user-images.githubusercontent.com/73453283/204577963-9f94258e-b084-4d1d-a43c-633ee44d4f08.png)

<br>
<br>

9. [κ΄μ¬ μν]μ μ°μλ¨μ μμΉν ννΈ λ²νΌμ ν΄λ¦­νλ©΄ κ΄μ¬ λͺ©λ‘μμ μ κ±°ν  μ μμ΅λλ€.
<br>

![image](https://user-images.githubusercontent.com/73453283/204578117-b57020dc-1678-41ab-901d-19ddb710b80f.png)

<br>
<br>
<br>

## π‘Docker Compose
* compose νμΌ μμ±
```
mkdir compose
```
* docker compose νμΌ μ€ν 
  * front-end, back-end, databaseμ νμν νκ²½λ³μ μ€μ 
  * front-end, back-end, databaseκ° μν  custom bridge μ€μ 
```
version: "3.8"
services:
  mydb:
    image: mariadb:10.2
    environment:
      - MARIADB_ROOT_PASSWORD=1234
      - MARIADB_DATABASE=movie
    ports:
      - "3306:3306"
    command:
      - --character-set-server=utf8
      - --collation-server=utf8_general_ci
    networks:
      back-net:
  myapp:
    build:
      context: ./backend
      dockerfile: Dockerfile
    environment:
      SPRING_DATASOURCE_URL: jdbc:mariadb://mydb:3306/movie?useSSL=false
      SPRING_DATASOURCE_USERNAME: root
      SPRING_DATASOURCE_PASSWORD: 1234
      SERVER_PORT: 8080
      expose: 8080
    depends_on:
      - mydb
    restart: always
    networks:
      - back-net
      - front-net
  myweb:
    build:
      context: ./frontend
      dockerfile: Dockerfile
    environment:
      API_IP: myapp:8080
    ports:
      - "3000:3000"
    depends_on:
      - myapp
    restart: always
    networks:
      - front-net
networks:
  back-net: {}
  front-net: {}
```

## π‘Docker Image & Docker Network 
### Backend Docker file
```
FROM openjdk:20-ea-11-slim-buster
COPY BoxOffice-0.0.1-SNAPSHOT.jar BoxOffice.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "BoxOffice.jar"]
```

### Front Docker file
```
FROM node:18-alpine3.15
COPY . .
RUN npm -y install
CMD ["npm", "run", "start"]
```
<br>

![image](https://user-images.githubusercontent.com/73453283/204580370-21504754-5d95-4eda-a439-c4afd211190f.png)
![image](https://user-images.githubusercontent.com/73453283/204569943-aae5d6f6-c272-4df4-8a21-a81b81ecf082.png)
![image](https://user-images.githubusercontent.com/73453283/204570069-796b672f-8923-4a39-b34e-f7a3ed2b850f.png)

