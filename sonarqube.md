# Sonarqube

Instalar con Docker

## Uso

- Acceso por url http://localhost:9000
- Credenciales:
  - admin : admin
- Tokens:
  - secure: token-secure: 8cdc2b5ee937edf391e9e873c76d9a12a8e2bc10

- Descargar scanner para OS
  - [Docs de config](https://docs.sonarqube.org/latest/analyzing-source-code/scanners/sonarscanner/)
  
- Añadir en gitignore:
  - sonar-project.properties
  - .scannerwork/
  
- Crear archivo sonar-project.properties en root:
    ```
    # must be unique in a given SonarQube instance
    # sonar.projectKey=my:project
    sonar.projectKey=secure.in99
    sonar.host.url=http://localhost:9000   
    sonar.login=8cdc2b5ee937edf391e9e873c76d9a12a8e2bc10

    # --- optional properties ---

    # defaults to project key
    #sonar.projectName=My project
    # defaults to 'not provided'
    #sonar.projectVersion=1.0
 
    # Path is relative to the sonar-project.properties file. Defaults to .
    #sonar.sources=.
    #sonar.exclusions=tests/**/*, public/js/plugins/**/*, public/in99panel/vendors/**/*, public/js/@babel/**/*,app/Repositories/**/*,app/Services/**/*,app/CrmModels/**/*
    #sonar.exclusions=tests/**/*, public/js/plugins/**/*, public/in99panel/vendors/**/*, public/js/@babel/**/*
    # sonar.exclusions=tests/coverage/**/*, public/js/plugins/**/*, public/in99panel/js/extensions/**/*, public/in99panel/vendors/**/*, public/js/@babel/**/*, public/dist/**/*, public/fonts/**/*, public//**/*
    sonar.exclusions=tests/**/*, app/CrmModels/**/*, public/js/plugins/**/*, public/in99panel/js/extensions/**/*, public/in99panel/vendors/**/*, public/js/@babel/**/*, public/dist/**/*, public/fonts/**/*
    # sonar.exclusions=tests/**/*, public/js/plugins/**/*, public/in99panel/vendors/**/*, public/js/@babel/**/*,app/CrmModels/**/*

    
    # Encoding of the source code. Default is default system encoding
    #sonar.sourceEncoding=UTF-8

    #sonar.php.coverage.reportPaths=tests/coverage.xml
    sonar.test=tests/**/*
    sonar.test.exclusions=tests/coverage/**/*

    # Ignorar issue PHP line comment
    # sonar.issue.ignore.multicriteria=php:S125
    sonar.issue.ignore.multicriteria=e1
    sonar.issue.ignore.multicriteria.e1.ruleKey=php:S125
    sonar.issue.ignore.multicriteria.e1.resourceKey=**/*
    # common.sonar.issue.ignore.multicriteria=e1
    # common.sonar.issue.ignore.multicriteria.e1.ruleKey=php:S125
    # common.sonar.issue.ignore.multicriteria.e1.resourceKey=**/*
    ```

- Ejecutar desde root con parametros en sonar-project:`sonar-scanner`


- Ejecutar desde root con parametros por consola:
    ```
    sonar-scanner \
    -Dsonar.projectKey=secure.in99 \
    -Dsonar.sources=. \
    -Dsonar.host.url=http://localhost:9000 \
    -Dsonar.login=8cdc2b5ee937edf391e9e873c76d9a12a8e2bc10
    ```

Informes - cnes-report
[Docs y source](https://github.com/cnescatlab/sonar-cnes-reporthttps://github.com/cnescatlab/sonar-cnes-report)

- Descargar
- Ejecutar `mvn clean install` para crear el .jar ejecutable
- Entrar en `/target` y ejecutar `java -jar sonar-cnes-report-4.1.3.jar -h`