# Setting Up the Node.js App with Docker

## Introduction  
This guide will help you set up and run a Node.js Express server using Docker, including a MySQL database for a seamless development environment.

---

## Cloning the Repository  
Clone the project repository and switch to the `dockerized` branch containing the Docker setup:  
```sh
git clone https://github.com/dasunwickr/dockerize-node-app.git
cd dockerize-node-app
git checkout dockerized
```

---

## Installing Docker and Docker Compose  
Ensure Docker and Docker Compose are installed:  
- **Windows/macOS**: Install [Docker Desktop](https://www.docker.com/products/docker-desktop).  
- **Linux (Debian/Ubuntu)**:  
  ```sh
  sudo apt update
  sudo apt install docker.io docker-compose -y
  sudo systemctl enable --now docker
  ```

Verify installation:  
```sh
docker --version
docker-compose --version
```

---

## Docker Compose Configuration  
The `docker-compose.yml` automates the setup with:  
- **Node.js App**: Built from the `Dockerfile`, mapped to host port 8080.  
- **MySQL Database**: Preconfigured with credentials and a database.  

```yaml
version: '3.8'
services:
  app:
    container_name: my_custom_app
    build: .
    ports:
      - "8080:3000"
    depends_on:
      - db
  db:
    container_name: my_custom_db
    image: mysql:latest
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: testdb
```

---

## Running the Application  
Start the containers in detached mode:  
```sh
docker-compose up --build -d
```

**Output**:  
```
Creating network "dockerize-node-app_default" with the default driver
Building app
...
Status: Downloaded newer image for mysql:latest
Creating my_custom_db ... done
Creating my_custom_app ... done
```

---

## Testing the Application  
Access the Node.js app at:  
```
http://localhost:8080
```  
**Expected Response**:  
```
Hello, Docker!
```

---

## Managing Containers  
- **Stop Containers**:  
  ```sh
  docker-compose down
  ```  
- **View Running Containers**:  
  ```sh
  docker ps
  ```  
- **Inspect Logs**:  
  ```sh
  docker-compose logs app
  ```

---

## Database Access  
Connect to the MySQL database using:  
- **Host**: `my_custom_db` (container name)  
- **Port**: `3306`  
- **Username**: `root`  
- **Password**: `root`  
- **Database**: `testdb`  

Example connection via CLI:  
```sh
docker exec -it my_custom_db mysql -uroot -proot
```

---

## Troubleshooting  
- **Rebuild After Changes**:  
  ```sh
  docker-compose up --build
  ```  
- **Clean Volumes**:  
  ```sh
  docker-compose down -v
  ```  

---

## Next Steps  
Explore advanced configurations like environment variables, persistent storage, or integrating with other services.  

**Happy containerizing!** 🐳
