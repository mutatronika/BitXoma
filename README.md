# BitXoma - Sistema de Rehabilitación con Prótesis Inteligente

![Estado del Proyecto](https://img.shields.io/badge/Estado-En%20Desarrollo-yellow)
![Licencia](https://img.shields.io/badge/Licencia-MIT-green)
![Versión](https://img.shields.io/badge/Versión-1.0.0-blue)

---

## 🎯 Visión del Proyecto

**BitXoma** es un sistema open-source de prótesis de extremidades de bajo costo con control mioeléctrico (EMG) avanzado, fabricación mediante impresión 3D y capacidades de inteligencia artificial adaptativa. El objetivo es democratizar el acceso a tecnología protésica de calidad para pacientes amputados en contextos de recursos limitados.

---

## ✨ Características Principales

- 🦾 **Prótesis de mano 3D impresa** con 5 grados de libertad
- 🧠 **Control mioeléctrico multi-canal** (EMG) con clasificación ML
- 🧤 **Guante sensor** con flex sensors para teleoperation
- 📡 **Transmisión inalámbrica** vía Bluetooth Low Energy (BLE)
- 💾 **Data logging** en tarjeta SD para análisis offline
- 🤖 **Machine Learning embebido** con TensorFlow Lite Micro
- 🔧 **Hardware accesible**: ESP32, Arduino, componentes <$200 USD
- 📖 **Documentación completa** y protocolos de rehabilitación

---

## 🚀 Estado Actual

**Fase 1: Prótesis Mioeléctrica Funcional** ✅

Actualmente implementado:
- Mano robótica con servomotores MG996R
- Adquisición EMG de 3 canales (Grove EMG Detector)
- Filtrado digital (Notch 50/60Hz, RMS)
- Guante con 5 flex sensors
- Transmisión BLE y logging CSV
- Código base ESP32 funcional

**Próximo objetivo:** Fase 2 - Consolidación y Validación Experta

---

## 📁 Estructura del Repositorio

```
bitxoma/
├── hardware/
│   ├── cad_files/              # Archivos STL/STEP para impresión 3D
│   ├── schematics/             # Esquemáticos electrónicos (Fritzing, KiCAD)
│   └── bom.md                  # Bill of Materials con proveedores
├── firmware/
│   ├── esp32_emg_acquisition/  # Código ESP32 para adquisición EMG
│   ├── arduino_servo_control/  # Control de servomotores
│   └── libraries/              # Librerías custom (filtros, BLE)
├── software/
│   ├── ml_models/              # Modelos TensorFlow/TFLite entrenados
│   ├── data_processing/        # Scripts Python para procesamiento
│   ├── mobile_app/             # App Android/iOS (opcional)
│   └── dashboard/              # Interfaz web para monitoreo
├── datasets/
│   ├── emg_recordings/         # Datasets propios de EMG
│   └── ninapro_preprocessed/   # Datos NinaPro procesados
├── docs/
│   ├── assembly_guide.md       # Guía de ensamblaje paso a paso
│   ├── user_manual.md          # Manual de usuario
│   ├── research_protocol.md    # Protocolo de investigación
│   └── publications/           # Papers y presentaciones
├── tests/
│   ├── unit_tests/             # Tests unitarios de código
│   └── validation_results/     # Resultados de validaciones clínicas
├── bitacora/                   # Bitácoras de sesiones de desarrollo
├── ROADMAP.md                  # Roadmap del proyecto
├── CONTRIBUTING.md             # Guía para colaboradores
├── LICENSE                     # Licencia MIT
└── README.md                   # Este archivo
```

---

## 🛠️ Hardware Requerido

### Componentes Básicos (Fase 1)

| Componente | Modelo | Cantidad | Precio Aprox |
|-----------|---------|----------|--------------|
| Microcontrolador | ESP32 DevKit | 1 | $10 |
| Sensores EMG | Grove EMG Detector | 3 | $75 |
| Flex Sensors | Spectra Symbol | 5 | $40 |
| Servomotores | MG996R | 5 | $25 |
| Batería | LiPo 3.7V 1500mAh | 1 | $15 |
| Módulo SD | MicroSD Module | 1 | $5 |
| Filamento 3D | Tough PLA | 500g | $15 |
| **TOTAL** | | | **~$185** |

### Hardware Adicional (Fases Avanzadas)

- **Fase 3:** IMU (MPU6050/9250), FSR sensors, módulo WiFi
- **Fase 5:** Headset EEG (OpenBCI, Mindflex hack), sensores adicionales

---

## 💻 Software y Dependencias

### Para Firmware (ESP32/Arduino)
```
Arduino IDE 2.x o PlatformIO
├── ESP32 Board Package (Espressif)
├── BLE Library (incluida en ESP32)
├── SD Library (Arduino standard)
└── TensorFlow Lite Micro (para ML)
```

### Para Procesamiento y ML (Python)
```bash
pip install tensorflow
pip install scikit-learn
pip install pandas numpy
pip install matplotlib seaborn
pip install scipy  # Para filtros digitales
```

### Para Análisis de Señales (Opcional)
```bash
pip install mne  # Para EEG en fases avanzadas
```

---

## 🚀 Inicio Rápido

### 1. Clonar el Repositorio
```bash
git clone https://github.com/tu-usuario/bitxoma.git
cd bitxoma
```

### 2. Cargar Firmware en ESP32
```bash
cd firmware/esp32_emg_acquisition
# Abrir bitxoma_emg_esp32.ino en Arduino IDE
# Seleccionar board: ESP32 Dev Module
# Cargar código (Ctrl+U)
```

### 3. Conectar Hardware
- Conectar sensores EMG a pines GPIO32, GPIO33, GPIO34
- Conectar servomotores a pines PWM
- Alimentar con batería LiPo o USB

### 4. Verificar Funcionamiento
```bash
# Abrir Serial Monitor (115200 baud)
# Deberías ver:
# "PROYECTO BITXOMA - Sistema EMG v1.0"
# "BLE inicializado. Esperando conexión..."
```

### 5. Conectar vía BLE
- Descargar app **nRF Connect** (Android/iOS)
- Escanear dispositivos BLE
- Conectar a "Bitxoma_EMG"
- Habilitar notificaciones
- Ver stream de datos RMS en tiempo real

---

## 📊 Datasets de Referencia

BitXoma utiliza y contribuye a los siguientes datasets:

- **NinaPro DB2**: Base de datos de EMG con 40 sujetos, 50 movimientos ([ninapro.hevs.ch](https://ninapro.hevs.ch))
- **Dryad Dataset**: doi:10.5061/dryad.1k84r
- **BitXoma Dataset** (en construcción): Datos propios con sensores de bajo costo

---

## 🧪 Protocolos de Validación

### Evaluaciones Funcionales Implementadas
- **SHAP** (Southampton Hand Assessment Procedure): 26 tareas cronometradas
- **BBT** (Box and Blocks Test): Destreza manual en 60 segundos
- **ACMC** (Assessment of Capacity for Myoelectric Control): 22 ítems

### Métricas de Desempeño
- Accuracy de clasificación de gestos: **Target >90%**
- Latencia de control: **Target <100ms**
- Completion time (SHAP): **Target <60 segundos**

---

## 📚 Publicaciones y Presentaciones

### Papers (En Preparación)
1. "BitXoma: Low-Cost Myoelectric Prosthetic Hand with TinyML for Resource-Limited Settings"
2. "Federated Learning for Personalized Prosthetic Control: A Multi-User Study"

### Conferencias Target
- IEEE EMBC (Engineering in Medicine and Biology Conference)
- ICORR (International Conference on Rehabilitation Robotics)
- Congreso Colombiano de Bioingeniería

---

## 🤝 Cómo Contribuir

¡BitXoma es un proyecto colaborativo! Puedes contribuir de varias formas:

### Desarrollo de Hardware
- Mejoras en diseño mecánico (CAD)
- Optimización de circuitos electrónicos
- Reducción de costos en BOM

### Desarrollo de Software
- Mejoras en algoritmos de filtrado
- Implementación de nuevos clasificadores ML
- Desarrollo de interfaz de usuario

### Investigación y Validación
- Recolección de datos EMG
- Pruebas con usuarios
- Protocolos de rehabilitación

### Documentación
- Tutoriales y guías
- Traducción a otros idiomas
- Videos explicativos

**Ver [CONTRIBUTING.md](CONTRIBUTING.md) para detalles**

---

## 📝 Licencia

Este proyecto está licenciado bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para detalles.

La licencia MIT permite uso comercial, modificación, distribución y uso privado, con la única condición de mantener el aviso de copyright.

---

## 👥 Equipo y Colaboradores

### Desarrollador Principal
- **[Tu Nombre]** - Instituto Tecnológico Metropolitano (ITM), Medellín, Colombia

### Colaboradores
- [Añadir colaboradores conforme se unan]

### Agradecimientos
- Comunidad e-NABLE
- OpenBionics Project
- NinaPro Database Team
- Upside Down Labs (BioAmp)

---

## 📧 Contacto

- **Email**: [tu-email@itm.edu.co]
- **GitHub Issues**: Para reportar bugs o sugerencias
- **Discord/Slack**: [Enlace a comunidad] (opcional)

---

## 🌟 Roadmap del Proyecto

Ver [ROADMAP.md](ROADMAP.md) para la visión completa de desarrollo a 3 años.

### Hitos Inmediatos (Q4 2025)
- ✅ Sistema base funcional con 3 canales EMG
- ⏳ Expandir a 8 canales EMG
- ⏳ Implementar TinyML con TFLite
- ⏳ Primera validación con 5 usuarios

### Próximos 6 Meses (Q1-Q2 2026)
- Integración de IMU y FSR
- Dashboard web de monitoreo
- Dataset propio con 1000+ muestras
- Publicación de primer paper

---

## 📈 Estadísticas del Proyecto

![GitHub Stars](https://img.shields.io/github/stars/tu-usuario/bitxoma?style=social)
![GitHub Forks](https://img.shields.io/github/forks/tu-usuario/bitxoma?style=social)
![GitHub Issues](https://img.shields.io/github/issues/tu-usuario/bitxoma)

---

## 🔗 Enlaces Útiles

- **Documentación completa**: [docs.bitxoma.org](https://docs.bitxoma.org) (cuando esté disponible)
- **Wiki del proyecto**: [GitHub Wiki](https://github.com/tu-usuario/bitxoma/wiki)
- **Canal de YouTube**: Tutoriales y demos
- **Instagram/Twitter**: @bitxoma_project

---

## ⚠️ Disclaimer

BitXoma es un proyecto de investigación y desarrollo educativo. **No está certificado como dispositivo médico** y no debe usarse como sustituto de prótesis clínicamente aprobadas sin supervisión médica apropiada. Siempre consulta con profesionales de la salud antes de usar cualquier dispositivo protésico.

---

## 🙏 Apoyo al Proyecto

Si BitXoma te resulta útil, considera:

- ⭐ Dar una estrella al repositorio
- 🐛 Reportar bugs o sugerir mejoras
- 📢 Compartir el proyecto en redes sociales
- 💰 Donar para materiales de investigación (opcional)

---

**Última actualización**: Noviembre 2025  
**Versión README**: 1.0  
**Estado**: Activamente desarrollado 🚀

---

**¡Construyamos juntos el futuro de la tecnología protésica accesible!** 🦾✨
