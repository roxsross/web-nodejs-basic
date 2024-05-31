### Prerrequisitos:

#### Java (JDK)

Ejecute los siguientes comandos para instalar Java y Jenkins.

##### Instalar Java

```sh
sudo apt update
sudo apt install openjdk-17-jre
```

##### Verificar que Java está instalado

```sh
java -version
```

Ahora, puede proceder con la instalación de Jenkins.

##### Instalar Jenkins

```sh
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

**Nota:** use el puerto 8080 para acceder.

##### Validar status Jenkins
```sh
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```

### Instalación de Docker:

Si planea utilizar Docker en su pipeline de CI/CD, puede instalarlo los siguientes comandos:

```sh
sudo apt update
sudo apt install docker.io
sudo usermod -aG docker jenkins
```

Reinicie Jenkins para que los cambios surtan efecto.

Para reiniciar Jenkins, puede utilizar el siguiente script:

```sh
sudo systemctl restart jenkins
```

### Instalación de Plugins:

Puede instalar plugins de Jenkins a través de la interfaz web de Jenkins o utilizando la CLI de Jenkins.

- **NodeJS**
- **Docker**
- **Docker Pipeline**
- **Docker Build Step**
