<div align="center">

# ❤️ Monitor de Pulso Cardíaco con ESP32

### Sensor de pulso analógico · Pantalla TFT ST7789 · Visualización de BPM

**Proyecto académico – UNISANGIL, sede Yopal**

![ESP32](https://img.shields.io/badge/Plataforma-ESP32-blue)
![Arduino](https://img.shields.io/badge/IDE-Arduino-00979D)
![Pantalla](https://img.shields.io/badge/Pantalla-ST7789-purple)
![Tipo](https://img.shields.io/badge/Proyecto-Educativo-success)

</div>

---

## 📌 Descripción

Este proyecto implementa un monitor educativo de pulso cardíaco utilizando un ESP32, un sensor óptico de pulso analógico y una pantalla TFT ST7789 de 240 × 280 píxeles. El sistema adquiere la señal del sensor, la procesa para detectar los latidos, estima la frecuencia cardíaca en pulsaciones por minuto (BPM) y presenta el resultado junto con una gráfica de la onda de pulso.

En este repositorio se reúnen el código fuente, el informe académico, fotografías del montaje y videos de demostración del prototipo.

> **Aviso importante:** este es un prototipo académico, no un dispositivo médico. No debe utilizarse para diagnóstico ni para tomar decisiones clínicas. Esta versión utiliza un sensor analógico de un solo canal y **no mide SpO₂**.

## ✨ Características

- Lectura analógica del sensor mediante el ADC de 12 bits del ESP32.
- Muestreo configurado a 100 Hz.
- Suavizado de la señal y eliminación de la línea base.
- Detección de latidos mediante un umbral adaptativo.
- Estimación de BPM a partir de los intervalos entre latidos.
- Visualización de BPM y onda de pulso en pantalla TFT.
- En la versión documentada con buzzer: aviso sonoro por latido.
- Envío de datos al Monitor Serie o al Serial Plotter de Arduino IDE.

## 🧰 Componentes

| Componente | Función |
|---|---|
| ESP32 DevKit (ESP32 clásico) | Adquisición y procesamiento |
| Sensor óptico de pulso analógico de 3 pines | Captura de la señal de pulso |
| Pantalla TFT ST7789 240 × 280 | Interfaz gráfica |
| Buzzer activo | Aviso sonoro (versión con buzzer) |
| Placa de expansión y cables Dupont | Conexiones |
| Cable USB | Alimentación y programación |

## 🔌 Conexiones

### Pantalla TFT ST7789

| Pin de la pantalla | ESP32 |
|---|---|
| SCL / SCK | GPIO 18 |
| SDA / MOSI | GPIO 23 |
| RES | GPIO 4 |
| DC | GPIO 2 |
| CS | GPIO 5 |
| VCC | 3.3 V |
| BLK | 3.3 V |
| GND | GND |

### Sensor de pulso analógico

| Pin del sensor | ESP32 |
|---|---|
| VCC / + | 3.3 V |
| GND / − | GND |
| S / señal | GPIO 34 |

### Buzzer activo (cuando se utiliza la versión con sonido)

| Pin del buzzer | ESP32 |
|---|---|
| Positivo (+) | GPIO 25 |
| Negativo (−) | GND |

**Notas:** la pantalla utiliza SPI; sus etiquetas SDA y SCL corresponden a MOSI y SCK. El sensor analógico se conecta al ADC mediante GPIO34 y no utiliza I²C. Comprueba el pinout impreso en tus módulos antes de energizar el circuito.

## 💻 Software y bibliotecas

1. Instala [Arduino IDE](https://www.arduino.cc/en/software).
2. Selecciona una placa ESP32 compatible, por ejemplo **ESP32 Dev Module**.
3. Instala desde el Gestor de bibliotecas:
   - **Adafruit GFX Library**
   - **Adafruit ST7735 and ST7789 Library**
   - **Adafruit BusIO**, si el gestor la solicita como dependencia.
4. Abre el archivo `.ino` de la carpeta `src`.
5. Selecciona el puerto COM correspondiente y carga el programa.

La comunicación serial está configurada a **115200 baudios**.

## 🚀 Código fuente

El sketch disponible en `src/Monitor_Pulso_ESP32_ST7789_v2.ino` corresponde al código recibido para la versión con buzzer activo y corazón animado. Se conserva el código original suministrado, cambiando únicamente la extensión del archivo a `.ino` para facilitar su apertura en Arduino IDE.

En el código, `MODO_PLOTTER=true` habilita la salida para el Serial Plotter. Con `MODO_PLOTTER=false` se envía información textual al Monitor Serie. Si no hay una señal válida, el BPM puede aparecer como `--` en pantalla o `0` en la salida serial.

## 📈 Uso del monitor

1. Alimenta el ESP32 mediante USB.
2. Espera a que aparezca la interfaz en la pantalla.
3. Apoya suavemente la yema del dedo sobre el sensor, sin presionar demasiado.
4. Mantén el dedo quieto mientras el sistema estabiliza la lectura.
5. Observa el valor de BPM y la onda en la pantalla.
6. Para revisar los datos, abre el **Serial Plotter** del Arduino IDE a 115200 baudios.

## 🎥 Videos de demostración

- [▶ Demostración 1](videos/Demostracion_01.mp4)
- [▶ Demostración 2](videos/Demostracion_02.mp4)

## 📷 Fotografías del prototipo

<p align="center">
  <img src="imagenes/Monitor_pulso_vista_01.png" width="42%" alt="Monitor de pulso con pantalla TFT"/>
  <img src="imagenes/Monitor_pulso_vista_02.png" width="42%" alt="Monitor de pulso en funcionamiento"/>
</p>

## 📄 Informe académico

El informe en formato Word está disponible aquí:

[📘 Informe del Monitor de Pulso – formato IEEE](docs/Informe_Monitor_de_Pulso_IEEE.docx)

## 📁 Estructura del repositorio

```text
Monitor-de-Pulso-ESP32/
├── README.md
├── GUIA_PARA_SUBIR_A_GITHUB.txt
├── src/
│   └── Monitor_Pulso_ESP32_ST7789_v2.ino
├── docs/
│   └── Informe_Monitor_de_Pulso_IEEE.docx
├── videos/
│   ├── Demostracion_01.mp4
│   └── Demostracion_02.mp4
└── imagenes/
    ├── Monitor_pulso_vista_01.png
    └── Monitor_pulso_vista_02.png
```

## 👨‍💻 Autores

- Cristian Enrique Cruz Fernández
- Samuel Felipe Díaz Galindo
- Santiago Reina Socha

**Fundación Universitaria de San Gil – UNISANGIL, sede Yopal**  
Yopal, Casanare, Colombia.

---

<div align="center">

**Proyecto académico de electrónica y sistemas embebidos**

</div>
