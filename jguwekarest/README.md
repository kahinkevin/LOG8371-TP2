# TP2 - Weka REST

## Installation des requis du projet

1. Mettre à jour le package manager
```shell
sudo apt-get update
```

2. Installer Docker
```shell
sudo apt-get install docker-ce docker-ce-cli
```

Si vous avez des problèmes pour installer Docker, suivez les étapes de ce site :
```shell
https://docs.docker.com/install/linux/docker-ce/ubuntu/
```

3. Installer Docker-compose
```shell
sudo apt install docker-compose
```

4. Installer Git
```shell
sudo apt install git
```

5. Installer Maven
```shell
sudo apt install maven
```

6. Télécharger et installer JProfiler sur le site :
```shell
https://www.ej-technologies.com/download/jprofiler/files
```

## Deployment de Weka Rest sur Docker

1. Cloner le projet
```shell
git clone https://github.com/kahinkevin/LOG8371-TP2.git
```

2. Naviguer dans le dossier du projet
```shell
cd LOG8371-TP2/jguwekarest
```

3. Compiler le projet Weka REST
```shell
mvn clean package
```

4. Build le Docker container
```shell
sudo docker build -t jguweka/jguweka:OAS3 .
```

5. Exécuter docker-compose
```shell
sudo docker-compose up
```

## Configuration de JProfiler


## Configuration de JMeter

