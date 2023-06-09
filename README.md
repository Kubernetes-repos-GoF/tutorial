# tutorial Azure - DevOps  

## prueba Tecnica DevOps - Samtel  
link repo prueba:  https://github.com/JefryGG1K91/first-filter


## Contar con las siguientes herramientas instaladas.

Sonarqube  
Organización de azure DevOps.  
Docker.  
Azure Agent Pool SelfHosted   
Kubernetes   
Minikube / Hypervisor / Nube con conexión a Azure DevOps   
Utiliza un repositorio del siguiente link del apartado de framework https://docs.docker.com/samples/   


## Procedimento

1. Descarga los archivos del repositorio elegido.  
2. Instala el framework necesario en caso de no tenerlo.  


# Aplicacion web

##  creacion Proyecto Vue.js

    $ npm install -g @vue/cli
    $ npm install -g npm@9.7.1
    $ vue create app-angel-test
    $ cd app-angel-test/
    $ npm run serve

    App running at:
    - Local:   http://localhost:8080/ 

    Ejecutamos el modo producción de Vue
    $ npm run build


## Correr contenedor SonarQube (local)

3. Compila la aplicación luego de pasar el analisis de sonarqube.  
4. Agregar dos escenarios 1 - analisis fallido | 2 - analisis exitoso  

Se utiliza para evaluar la calidad de codigo (linter) y cobertura de pruebas (CodeCoverage). 

Se levanta el contenedor para no hacer la instalación en el computador.:
    - Teniendo Docker instalado   
    - Crear carpeta local con permisos de lectura y escritura, para los volumenes persistentes de los contenedores   
    - Bajar el docker-compose.yml de SonarQube y guardarlo en la carpeta creada
    - Luego ejecutar (desde la ruta de la carpeta)  

        $ docker-compose up
        $ docker ps

    - la interfaz grafica se despliega en local:   http://localhost:9000  
    - Para vincular con la applicacion web (trabajada), crear el archivo: sonar-project.properties   
    - Install sonar-scanner   
    - Run:   

        $  sonar-scanner


## Crear Dockerfile

5. Genera una imagen de docker y sube la imagen a dockerhub. 

Crear nginx.default.conf  

    $ docker build -t angel-test . 
    $ docker images
    $ docker run -d angel-test 
    $ docker ps
    $ docker exec -it <containerId> sh
    $ docker run -it -p 8080:80 --rm --name angel-test angel-test


6. Dentro del pipeline ejecute lo siguiente en bash o powershell. a. Imprime Hola Mundo 10 veces en pantalla con un job paralelo. b. Script que cree 10 archivos con la fecha y luego lo imprima en consola  

## Azure DevOps   

    - Organization:  AngelCastro-org1  
    - project:   project-angel-test  (Private)  
    - Project description:  Proyecto de Azure DevOps que incluye todo el ciclo de desarrollo para una aplicacion vue.js  
    - link: https://dev.azure.com/AngelCastro-org1/project-angel-test  


7.  Despliega la app a un clúster de kubernetes (minikube o EKS o AKS).  
8. Crea un endpoint externo accesible (ingress) para la aplicación  
9. Sube al repo en una carpeta environment todos los yaml de k8s. 


### Que se espera del ejercicio

Configuración de la infraestructura desde cero.
Documentación para crear solución y demostración de la aplicación funcionando.
Coding Standards.
Enfoque hacia la meta.

### Bonus para tomar en consideración

Construye un clúster de kubernetes usando IaC (terraform o eksctl).
Usa un manejador de templates como Kustomize o Helm.
Despliega en nube publica (AWS o Azure).
Que sea accesible desde internet.
Uso de metodologías DevOps.
####Resultados que debes adjuntar

Codigo
yaml de k8s
Pipelines
Logs
Printscreen
Recording de pantalla (opcional)
Compartir repositorio de github publico para evaluación


### Task Index


0. Crear Script Bash:  
    - Hola mundo x10  
    - Crear 10 archivos con fecha y print en consola (echo )  
1. Azure (Terraform) > az cli  
2. Azure DevOps > Crear Project (PruebaAngel)  
3. Infra:  
    - Remote State (backend)  
    - Networking? 
    - ACR (imagen)  
    - AKS (pods, svc, ingress)  
    - Application Gateway (loadBalancer)  
    - Agent  
    - SonarQube  
4.  Azure DevOps:  
    - ServicePrincipal  
    - Agent  
    - Library: env  
    - Pipeline (master, qa, dev):   
        - Script Bash (paralelo)  
        - StaticCodeAnalysis (UnitTesting, Linter, CodeCoverage)  
        - Artifact: files  
    - Release: env (dev, qa, prd) > Policies (Approvers)  
        - Build (.js, .html)  
        - Dockerfile > Imagen Push (ACR)  
        - K8S: helmChart > Image2Pod, rollout  


    helmChart (var env): deployment, svc, ingress, configMap, secret, hpa  
    Dockerfile  
    Code Dev....  
    SonarLocal (>= 85) ... run UnitTesting, Linter, SonarScanner  
    Git: git checkout -b feature/angel && git push origin/feature/angel  
    GitHub: Pull Request: master < feature/angel === Approved  