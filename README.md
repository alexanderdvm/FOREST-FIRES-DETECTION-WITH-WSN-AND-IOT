# FOREST-FIRES-DETECTION-WITH-WSN-AND-IOT
# Sistema IoT/WSN para Detección y Alerta de Incendios Forestales

Este proyecto tiene como objetivo implementar un sistema de monitoreo y alerta temprana de incendios forestales, basado en una red de sensores IoT que utilizan tecnología LoRaWAN para enviar datos de temperatura, humedad, humo y gases a un servidor de LoRaWAN en The Things Network (TTN). Estos datos son analizados por un backend que aplica un algoritmo de detección de incendios para generar alertas preventivas en una aplicación web.

## Tabla de Contenidos

1. [Descripción del Proyecto](#descripción-del-proyecto)
2. [Arquitectura del Sistema](#arquitectura-del-sistema)
3. [Tecnologías y Herramientas](#tecnologías-y-herramientas)
4. [Configuración del Proyecto](#configuración-del-proyecto)
5. [Estructura del Código](#estructura-del-código)
6. [Contribuciones](#contribuciones)
7. [Licencia](#licencia)

---

## Descripción del Proyecto

Este sistema IoT permite la detección y alerta temprana de áreas de alto riesgo de incendios forestales mediante una red de sensores (Wireless Sensor Network - WSN) que monitorean en tiempo real la temperatura, humedad, y la concentración de humo y gases en el ambiente. Los datos recogidos son enviados de manera eficiente a través de LoRa a un servidor LoRaWAN (TTN), donde son procesados por un backend que ejecuta un algoritmo de detección de posibles incendios. La información y las alertas generadas se muestran en una aplicación web para facilitar el monitoreo y permitir acciones preventivas.

## Arquitectura del Sistema

La arquitectura general del sistema es la siguiente:

1. **Red de Sensores (WSN)**: Incluye sensores de temperatura, humedad, humo y gases conectados al módulo LoRa 32u4.
2. **Transmisión de Datos**: Los datos se envían a TTN utilizando LoRaWAN (Over-The-Air Activation - OTAA).
3. **Servidor LoRaWAN (TTN)**: Gestiona la red LoRaWAN y permite la recolección de datos.
4. **Backend y Procesamiento de Datos**: Un servidor Node.js con Express que recibe los datos mediante una API Webhook de TTN y aplica un algoritmo de detección de incendios.
5. **Frontend**: Una aplicación React que muestra los datos y alertas en tiempo real, con una interfaz intuitiva para visualizar el estado de riesgo de incendios forestales.

## Tecnologías y Herramientas

- **Hardware**: Módulo LoRa 32u4, sensores de temperatura, humedad, humo y gases.
- **Lenguajes y Librerías**:
  - **C++**: Programación de los módulos LoRa con la librería LMIC MCCI LoRaWAN.
  - **Node.js y Express**: Backend para recibir y procesar datos.
  - **React**: Frontend para visualizar las alertas y datos de riesgo.
- **Servidor de LoRaWAN**: The Things Network (TTN)
- **Comunicación**: Webhook para recibir datos desde TTN en el backend.

## Configuración del Proyecto

### Requisitos Previos

- [Node.js](https://nodejs.org) instalado en el servidor.
- [React](https://reactjs.org) para la aplicación web.
- Configuración de los módulos LoRa 32u4 con la librería LMIC MCCI para la conexión a TTN.

### Configuración de TTN

1. Crear una aplicación en [The Things Network (TTN)](https://www.thethingsnetwork.org/) y registrar el dispositivo LoRa 32u4 utilizando OTAA.
2. Configurar los sensores y programar el módulo LoRa en C++ para enviar datos de temperatura, humedad, humo y gases.
3. Configurar un Webhook en TTN para enviar los datos al backend mediante una URL definida.

