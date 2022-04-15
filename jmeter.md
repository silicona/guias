# Jmeter

[docs Apache](https://jmeter.apache.org/usermanual/get-started.html)

Medidor de webs y aplicaciones

## Properties

Editar archivo bin/jmeter.properties para modificar valores de config:
  - `resultcollector.action_if_file_exists=DELETE`: Sobreescribe el archivo de resultados
  - `CookieManager.save.cookies=true`: Guarda las cookies del test
  - `CookieManager.name.prefix=wedont_cookie`: Establece el nombre de la cookie

## Primer test

[Primer test](https://programmerclick.com/article/49181282828/)

## Certificado JMeter

Modificar en bin/jmeter.properties:
  - Detener JMeter
  - Aumentar validez del certificado a 365 dias
  - Borrar ApacheJMeter....CA.crt de bin/
  - Reiniciar JMeter

## Cookies

Pasos:
  - Habilitar variables de CookieManager
  - Añadir

### Recording

[tutorial](https://octoperf.com/blog/2018/04/26/jmeter-recording/#firefox-setup)

Pasos:
  - File - Templates - Recording
  - Script Recorder:
    - Port: 8181
    - Transaction Name: cambiar por cada pagina visitada
  - Navegador:
    - Firefox:
      - Ajustes - General - Configuración de red:
        - Configuración manual del proxy:
          - http y https: localhost, puerto 8181
      - Ajustes - Privacidad y Seguridad - Certificados:
        - Importar certificado \_JMeter Root CA... (en JMeter root)

Con el ScriptRecorder apagado, el navegador no funciona con los parametros del proxy.