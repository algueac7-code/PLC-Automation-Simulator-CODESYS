# ⚙️ PLC Automation Simulator – CODESYS

## 📌 Descripción

Proyecto de automatización industrial desarrollado en **CODESYS**, basado en una arquitectura modular con **Function Blocks (FB)**.

Simula el control de un proceso de mezcla con motor, incluyendo:

* Máquina de estados (FSM)
* Modos Automático y Manual
* Manejo de fallas
* Interlocks de seguridad
* Sistema de recetas
* Historial de producción con timestamp
* Interfaz HMI interactiva

Este proyecto está orientado a demostrar **buenas prácticas utilizadas en entornos industriales reales**.

---

## 🏗️ Arquitectura del sistema

El sistema está estructurado en bloques funcionales independientes:

* `FB_Inputs` → Lectura de entradas (Start, Stop, Reset, sensores)
* `FB_Events` → Detección de flancos (R_TRIG / F_TRIG)
* `FB_Control` → Máquina de estados (FSM)
* `FB_Process` → Lógica de proceso y fallas
* `FB_Interlocks` → Permisivos y condiciones de seguridad
* `FB_Recipes` → Gestión de recetas de proceso
* `FB_LotHistory` → Registro de lotes (buffer circular)
* `FB_PlantSim` → Simulación de planta
* `FB_Outputs` → Control de salidas

---

## 🔄 Máquina de estados (FSM)

Estados implementados:

| Estado | Descripción |
| ------ | ----------- |
| 0      | IDLE        |
| 5      | MANUAL      |
| 10     | STARTING    |
| 20     | PROCESSING  |
| 40     | COMPLETE    |
| 90     | FAULT       |

### Comportamiento

* En **Automático** → el sistema sigue la secuencia FSM
* En **Manual** → control directo del motor
* En **Falla** → el sistema se detiene y requiere Reset

---

## 🔁 Modos de operación

### 🔹 Automático

* Secuencia controlada por FSM
* Validación de interlocks
* Supervisión de proceso y fallas

### 🔹 Manual

* Control directo desde HMI
* Interlocks de seguridad activos
* Permite pruebas y mantenimiento controlado

---

## ⚠️ Manejo de fallas

Fallas implementadas:

* **Motor No Start**
* **Nivel inválido de tolva**

Características:

* Fallas latcheadas (RS)
* Reset controlado
* Diagnóstico en HMI
* Estado global de fallo

---

## 🧪 Simulación de planta

Incluye simulación completa de:

* Motor (retardo de contactor)
* Sensores de nivel (Low / Mid / High)
* Consumo de material en tolva
* Animación visual del proceso

---

## 🧠 Sistema de recetas

Permite seleccionar diferentes configuraciones de proceso:

* Receta Normal
* Receta Rápida
* Modo Simulación

Parámetros controlados:

* Tiempo de proceso
* Velocidad del motor

Incluye **bloqueo de cambio de receta durante ejecución** (interlock).

---

## 📊 Historial de lotes

El sistema registra automáticamente los lotes procesados mediante un **buffer circular de 20 posiciones**.

Cada lote incluye:

* Número de lote
* Receta utilizada
* Tiempo de proceso
* Velocidad del motor
* Fecha y hora de finalización

Características:

* Registro por evento (flanco)
* Sin duplicados
* Reescritura automática al llenarse el buffer
* Contador dinámico de registros válidos (sin filas vacías en HMI)

---

## 🖥️ Interfaz HMI

La visualización incluye:

### Controles

* Start / Stop / Reset
* Selector Manual / Automático
* Selección de receta

### Indicadores

* Estado del sistema
* Estado del motor
* Nivel de tolva
* Alarmas

### Historial en tiempo real

* Tabla dinámica de lotes procesados
* Datos actualizados en vivo

---

## 🎮 Modo de prueba

Permite:

* Forzar condiciones desde HMI
* Simular fallas
* Validar lógica sin hardware físico

---

## 🚀 Cómo ejecutar

1. Abrir el proyecto en **CODESYS**
2. Compilar (Build)
3. Ejecutar (Login + Run)
4. Abrir la visualización (HMI)

### Probar:

* Modo Automático
* Modo Manual
* Generación de fallas
* Cambio de recetas
* Registro de lotes

---

## ⚠️ Consideraciones

* Proyecto basado en simulación (sin hardware real)
* Puede requerir librerías instaladas en CODESYS
* Configurar correctamente el dispositivo de simulación

---

## 📷 Capturas

* Control de Estados
<img width="626" height="329" alt="image" src="https://github.com/user-attachments/assets/42ca05b4-fe6d-4173-9525-cca16bbd50fc" />

* Incluye Fallas de Carga y de motor.
<img width="618" height="320" alt="image" src="https://github.com/user-attachments/assets/e7ff67a7-7008-48bf-801f-33d16053e3c2" />

*


---

## 👨‍💻 Autor

**Alonso Guevara Acosta**
Costa Rica

Experiencia en:

* Automatización industrial
* Manufactura avanzada
* Sistemas PLC
* Control de procesos

---

## 🎯 Objetivo del proyecto

Demostrar habilidades en:

* Diseño modular de sistemas PLC
* Implementación de FSM industriales
* Manejo de fallas e interlocks
* Desarrollo de HMI funcional
* Simulación de procesos
* Trazabilidad de producción

---

## 🔮 Próximas mejoras

* Historial de fallas con timestamp
* Exportación de datos (SQL / Workstation)
* Mejora visual de HMI
* Integración con sistemas externos

---

