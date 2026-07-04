# Cronógrafo Inteligente (Smart Chronograph)

Este proyecto consiste en un **Cronógrafo Inteligente** completo para medir la velocidad y la energía cinética de proyectiles (como perdigones de carabinas de aire comprimido, balines de airsoft, etc.). El sistema está compuesto por el hardware/firmware de medición y aplicaciones móviles/de escritorio para visualizar, analizar y escuchar los resultados en tiempo real a través de Bluetooth LE.

## 🚀 Características principales
- **Medición de precisión**: Firmware para Arduino (C++) en el ESP32 Dev Module que calcula la velocidad detectando el paso del proyectil por barreras de sensores ópticos (infrarrojos).
- **Conectividad inalámbrica**: Transmisión de datos en tiempo real mediante Bluetooth Low Energy (BLE).
- **Anuncios por Voz (TTS)**: La aplicación móvil anuncia por voz la velocidad de cada disparo de forma automática para no tener que mirar la pantalla mientras se dispara.
- **Cálculo de Energía Cinética**: Cálculo automático de la energía en Julios (J) a partir de la velocidad medida y el peso configurable del proyectil (g).
- **Estadísticas Completas**: Seguimiento de velocidad/energía mínima, máxima, media y lista histórica de la sesión de disparos.
- **Soporte Multilingüe**: Disponible en Catalán, Español e Inglés.

---

## 📁 Estructura del Proyecto

El repositorio está organizado en las siguientes carpetas:

```
├── cronografo_android/       # Aplicación móvil nativa para Android (Kotlin + Jetpack Compose)
├── cronografo/               # Aplicación multiplataforma en .NET MAUI
├── imported_cronografo/      # Código y firmware para dispositivos de hardware (versión actual Arduino y scripts heredados)
│   ├── arduino/              # Código C++ (.ino) para Arduino (versión actual)
│   └── (archivos .py)        # Scripts heredados de versiones anteriores (MicroPython)
├── Analisis_Precision_Cronografo.pdf / .html  # Documento técnico con el análisis de precisión del sistema
└── README.md                 # Este archivo
```

---

## 🛠️ Componentes y Configuración

### 1. Hardware y Firmware (`imported_cronografo/`)
El hardware requiere dos barreras de sensores infrarrojos situadas a una distancia conocida. Cuando un proyectil interrumpe la primera y luego la segunda barrera, el microcontrolador calcula el tiempo transcurrido y la velocidad.

- **ESP32 Dev Module (Firmware principal)**: Código fuente en C++ para Arduino (`imported_cronografo/arduino/cronoABC ultima version/cronoABC/cronoABC.ino`). Este firmware se encarga de realizar la medición mediante interrupciones y transmitir los datos por Bluetooth LE (BLE).

### 2. Aplicación Android (`cronografo_android/`)
Desarrollada en Kotlin con la interfaz moderna de **Jetpack Compose**.
- Permite escanear y conectarse al cronógrafo mediante BLE.
- Configurar el peso del balín en gramos.
- Escuchar las lecturas a través de Text-To-Speech (TTS).
- Ver un resumen analítico con la velocidad mínima, máxima y media de la tanda de disparos.

### 3. Aplicación .NET MAUI (`cronografo/`)
Una alternativa multiplataforma desarrollada en C# y XAML con soporte para Windows, Android e iOS.

---

## ⚙️ Requisitos y Licencia

- **Dispositivos móviles**: Android 8.0 (API 26) o superior para la aplicación nativa. Permisos de Bluetooth y ubicación (para el escaneo BLE) requeridos.
- **Desarrollo Android**: Android Studio Koala o superior, con Gradle actualizados.
- **Desarrollo MAUI**: Visual Studio 2022 con la carga de trabajo de .NET MAUI.
