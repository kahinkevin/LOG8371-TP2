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

## Deployment de Weka Rest sur Docker

1. Cloner le projet
```shell
git clone https://github.com/kahinkevin/LOG8371-TP2.git
```

2. Naviguer dans le dossier du projet
```shell
cd LOG8371-TP2
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

## Exécution de JProfiler

1. Télécharger et installer JProfiler GUI sur le site :
```shell
https://www.ej-technologies.com/download/jprofiler/files
```

2. Lancer l'application JProfiler GUI
```shell
./jprofiler_linux_11_0.sh
```

Si l'application ne veut pas se lancer, donner d'abord permission pour l'exécution
```shell
chmod +x <path absolu au fichier>/jprofiler_linux_11_0.sh
```

3. Lors de l'installation, choisir l'activation de la version essai (trial)

4. Pour commencer une nouvelle session de JProfiler, effectuer les étapes suivantes :
```shell
1. Menu -> Session -> New Session
2. Session Type -> Attach -> Attach to remote JVM
3. Choisir l'adresse IP du docker container de WekaRest (127.0.0.1)
4. Choisir le port du docker container de WekaRest (8849)
5. Cliquer sur OK
6. Choisir Evaluate
```

## Configuration de JMeter
1. Telecharger et extraire JMeter
```shell
wget http://muug.ca/mirror/apache-dist//jmeter/binaries/apache-jmeter-5.1.1.zip
unzip apache-jmeter-5.1.1.zip
```

2. (Optionnel) Utiliser le GUI de Jmeter creer un plan de test
```shell
cd apache-jmeter-5.1.1/bin/
./jmeter
```

3. Rouler les tests existants pour le TP
```shell
cd apache-jmeter-5.1.1/bin/
./jmeter -n -t [CHEMIN_VERS_LE_FOLDER_DU_REPO]/jmeter_loadtests/{linearregression | simplekmeans | zeror}_{low | medium | high | veryhigh}.jmx
```

4. Enjoy the show!

5. Note importante #1: Les tests existants de JMeter assument que le conteneur Docker de WEKA REST est roule localement avec les parametres par defaut.
Ainsi, on peut y acceder a travers :
```shell
http://localhost:8081/
```

6. Note importante #2: Les tests (scenarios) sont decrits de la maniere suivante :
```shell
- Low : 1 thread (user) avec 10 loops
- Medium : 10 threads (users) avec 100 loops
- High : 100 threads (users) avec 1000 loops
- VeryHigh : 1000 threads (users) avec 1000 loops
```
