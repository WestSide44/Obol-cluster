## Меняем версию geth и lighthouse

 ```
  cd charon-distributed-validator-node
  ```
 ```
  nano docker-compose.yml
 ```
 # заменить версию **geth** и **lighthouse**
   
- **geth: v1.11.3**
- **lighthouse : v3.5.1**

Должно получиться так: 

https://i.imgur.com/5UKGub9.png

https://i.imgur.com/WIPKtiv.png


```
  docker-compose down 
```
```
  docker-compose up -d  
```

# проверить логи : 

```
docker-compose logs -f
```
```
docker logs charon-distributed-validator-node-teku-1
```
```
docker-compose logs geth 
```
```
docker-compose logs lighthouse
```
```
docker-compose logs charon
```

если у вас в логах есть ошибка:  ```error:Error: load priv key: decode private key hex: encoding/hex: invalid byte```

то делаем следующие действия :

```
cd charon-distributed-validator-node
```

```
nano docker-compose.yml
```

меняем версию **Сharon**

- **charon: v0.14.1**

и делаем ресинхрон:

```
docker-compose stop lighthouse
```

```
sudo rm -rf data/lighthouse/beacon
```

```
docker-compose up -d lighthouse
```

проверяем логи: 

```
docker-compose logs geth 
```

```
docker-compose logs lighthouse
```

```
docker-compose logs -f
```



   
