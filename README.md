# tutorial Azure - DevOps

## prueba Tecnica DevOps - Samtel

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