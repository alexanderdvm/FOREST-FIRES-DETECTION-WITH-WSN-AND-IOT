# FOREST-FIRES-DETECTION-WITH-WSN-AND-IOT
# Sistema IoT/WSN para Detección y Alerta de Incendios Forestales

Este proyecto implementa un sistema IoT basado en una red de sensores inalámbricos (WSN) utilizando tecnología LoRa para la detección y alerta temprana de zonas de alto riesgo de incendios forestales. Los sensores monitorean continuamente parámetros ambientales críticos y envían la información a un servidor LoRaWAN en The Things Network (TTN). Posteriormente, los datos son procesados en un backend donde se analiza la información y se genera una alerta en caso de detectar un posible incendio.

## Descripción del Proyecto

### Objetivos
- Monitorear y detectar condiciones que puedan indicar un incendio forestal.
- Alertar de manera temprana a los responsables de la vigilancia del bosque para permitir acciones preventivas.
- Visualizar los datos en tiempo real en una aplicación web y enviar notificaciones por SMS a los encargados.

### Componentes Principales
1. **Sensores de Campo**:
   - **Temperatura y Humedad**: Detecta condiciones ambientales de riesgo (sensor DHT22).
   - **Humo y Gases**: Monitorea la presencia de humo y gases inflamables (sensor MQ2).
   
2. **Módulo LoRa**:
   - Se utiliza el módulo LoRa 32u4 con chipset Semtech SX1276, programado en C++ mediante la librería LMIC de MCCI LoRaWAN.
   - La transmisión de datos se realiza utilizando el protocolo LoRaWAN a través de TTN.

3. **Servidor LoRaWAN (TTN)**:
   - Los datos recolectados por los sensores son transmitidos mediante el módulo LoRa hacia TTN.
   - Una Webhook en TTN se encarga de redirigir los datos al backend de la aplicación.

4. **Backend**:
   - Construido con **Node.js** y **Express**.
   - Recibe los datos a través de la Webhook de TTN y los almacena en una base de datos MySQL.
   - Incluye un algoritmo para la detección de posibles incendios basado en el análisis de los parámetros recibidos.
   - En caso de detectar condiciones de riesgo, genera una alerta que se envía al frontend y, además, se notifica por SMS a los responsables de la vigilancia.

5. **Frontend**:
   - Desarrollado en **React**, permite la visualización de los datos en tiempo real.
   - Muestra una alerta visual en caso de detección de posibles condiciones de incendio.

## Arquitectura del Sistema

1. **Sensores de Campo** -> 2. **Módulo LoRa 32u4** -> 3. **The Things Network (TTN)** -> 4. **Backend (Node.js/Express)** -> 5. **Base de Datos (MySQL)** -> 6. **Frontend (React)** y **Notificación SMS**

## Requisitos

- **Hardware**:
  - Módulo LoRa 32u4
  - Sensores DHT22 y MQ2

- **Software**:
  - Arduino IDE o platform.io para programar el módulo LoRa con C++
  - Node.js y Express para el backend
  - MySQL para la base de datos
  - React para el frontend
  - Cuenta en The Things Network (TTN)

## Configuración del Proyecto

### 1. Configuración de TTN
   - Crear una cuenta en TTN.
   - Configurar la aplicación y los dispositivos LoRa en TTN para recibir los datos.
   - Configurar una Webhook en TTN para redirigir los datos hacia el backend.

### 2. Programación del Módulo LoRa
   - Utilizar Arduino IDE y la librería LMIC de MCCI para programar el módulo LoRa.
   - Configurar los parámetros de red y la autenticación OTAA o ABP para la conexión a TTN y enviar informacion de los sensores.

### 3. Configuración del Backend (Node.js/Express)
   - Recibir la informacion del webhook
   - Configurar la conexión a la base de datos MySQL en el archivo de configuración del backend.
   -Reenviar la informacion al front con HTTP y a los bomberos y policias un sms con una alerta de posible incendio

### 4. Configuración del Frontend (React)
   - Desde la carpeta del proyecto, instalar las dependencias de React
   - Ejecutar la aplicación React y programar la pagina para que muestre la inforacion de los sensores en tiempo real
   - recibir la informacion del back mediante HTTP

### 5. Base de Datos (MySQL)
   - Configurar y crear la base de datos en MySQL.
   - Crear las tablas necesarias para almacenar los datos de los sensores y las alertas generadas.

## Funcionamiento del Sistema

1. Los sensores capturan datos ambientales y los envían a través del módulo LoRa 32u4 hacia TTN.
2. Los datos se envían mediante una Webhook de TTN al backend de la aplicación.
3. El backend procesa y analiza los datos mediante un algoritmo de detección de incendios y envia el front y por SMS a los encargados de para el incendio.
4. Si se detectan condiciones de riesgo, se genera una alerta en el sistema, que es mostrada en el frontend y enviada por SMS a los encargados.

## Tecnologías Utilizadas

- **Hardware**: Módulo LoRa 32u4 con sensores de temperatura, humedad, humo y gases.
- **Protocolos**: LoRaWAN, utilizando TTN.
- **Backend**: Node.js y Express.
- **Base de Datos**: MySQL.
- **Frontend**: React.
- **Programación del Módulo LoRa**: C++ con la librería LMIC de MCCI.

## Contribución

Si deseas contribuir a este proyecto, por favor sigue los siguientes pasos:

1. Haz un fork del repositorio.
2. Crea una nueva rama (`git checkout -b feature/nueva-funcionalidad`).
3. Realiza tus cambios y haz un commit (`git commit -am 'Agrega nueva funcionalidad'`).
4. Haz un push a la rama (`git push origin feature/nueva-funcionalidad`).
5. Abre un Pull Request para revisar los cambios.

## Licencia

Este proyecto está bajo la licencia MIT. Puedes ver el archivo [LICENSE](LICENSE) para más detalles.
