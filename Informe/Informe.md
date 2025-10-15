# Informe Laboratorio No. 02 - Análisis y Operación del Manipulador Motoman MH6.

<p align="center">
<img src="Imagenes/logo_3.png" alt="UNAL" width="600"/>
</p>

### Autores:  
Esteban Durán Jiménez  
Ana María Orozco Reyes  

**FACULTAD DE INGENIERÍA**  
**ROBÓTICA**  
**2025-II**



---

## Sección de preguntas


### Describir las diferencias entre el home1 y el home2 del Motoman MH6.

## 1. Movimiento manual del manipulador Motoman

Para mover manualmente el **Motoman** se utiliza el **Teach Pendant (colgante de programación)**.  
El procedimiento general es el siguiente:

1. **Encender el robot y el controlador.**  
2. **Seleccionar el modo "Teach"** desde el interruptor de modo (clave o selector).  
3. **Habilitar el "Servo Power"** presionando el botón “Servo ON READY”.  
4. **Seleccionar el tipo de movimiento:**
   - **Por articulaciones (Joint mode):** se presiona la tecla `COORD` hasta que en la pantalla aparezca `JOINT`.
   - **Por coordenadas cartesianas (Base o Tool):** se presiona nuevamente `COORD` para alternar entre `BASE`, `TOOL`, `USER`, etc.
5. **Mover los ejes o traslaciones:**
   - En modo **Joint**, se usan las teclas de dirección para cada eje (`+J1`, `-J1`, ..., `+J6`, `-J6`).
   - En modo **Cartesiano**, se usan:
     - `+X / -X` para traslaciones en el eje X  
     - `+Y / -Y` para traslaciones en el eje Y  
     - `+Z / -Z` para traslaciones en el eje Z  
     - `+Rx / -Rx`, `+Ry / -Ry`, `+Rz / -Rz` para rotaciones alrededor de esos ejes.

> 🔹 **Nota:** Es necesario mantener presionado el **Deadman Switch** (interruptor de seguridad) en la parte trasera del Teach Pendant para permitir el movimiento.

---

## 2. Niveles de velocidad del Motoman

El **Motoman** dispone de varios **niveles de velocidad** para movimiento manual (jogging):

- Normalmente se establecen niveles como **Low (10%)**, **Medium (50%)**, y **High (100%)**.  
- El ajuste fino puede realizarse en incrementos mediante las teclas de **Speed Override (+/-)**.

### Cambio de velocidad
- Se realiza presionando las teclas:
  - `SHIFT + SPEED +` → aumenta la velocidad.
  - `SHIFT + SPEED -` → disminuye la velocidad.
- También puede configurarse desde el menú del Teach Pendant en la opción **"Setup > Jog speed"**.

### Identificación en pantalla
- El nivel actual de velocidad se muestra en la parte superior de la pantalla LCD del colgante, generalmente en forma de **porcentaje (%)** del máximo permitido.  
  Ejemplo: `SPEED: 50%`.

---

## 3. Aplicaciones principales de RoboDK

**RoboDK** es un software de **simulación y programación offline** para robots industriales.  
Sus principales aplicaciones son:

- **Simulación de trayectorias y procesos** (soldadura, mecanizado, pintura, ensamblaje, pick & place).  
- **Generación automática de programas** para diferentes marcas (Motoman, ABB, KUKA, FANUC, UR, etc.).  
- **Validación de alcances, colisiones y tiempos de ciclo.**  
- **Integración CAD-CAM**, permitiendo importar trayectorias desde software de diseño o mecanizado.

### Comunicación con el manipulador
RoboDK se comunica con el robot mediante el **driver del fabricante** (en este caso Yaskawa Motoman).  
- Envía las **instrucciones de movimiento (puntos, trayectorias y velocidades)** en formato de programa del controlador (ej. lenguaje INFORM para Motoman).  
- Estas instrucciones pueden transmitirse:
  - **Offline:** exportando el programa y cargándolo en el controlador DX100/DX200.  
  - **Online (modo de simulación en vivo):** mediante conexión Ethernet o puerto TCP/IP, enviando los comandos directamente al robot.

---

## 4. Comunicación entre RoboDK y el manipulador

- Se establece una **conexión TCP/IP** entre RoboDK y el controlador del robot (por ejemplo, DX200).  
- RoboDK actúa como un **cliente**, enviando los comandos de posición y lectura de estado al **servidor del controlador**.  
- El protocolo puede variar según el fabricante, pero en Motoman generalmente se utiliza **MotoCOM o el driver Yaskawa RoboDK API**.  
- Una vez conectado, los movimientos simulados en RoboDK se replican en tiempo real en el manipulador físico.

---

## 5. Diferencias entre RoboDK y RobotStudio

| Característica | **RoboDK** | **RobotStudio (ABB)** |
|----------------|-------------|------------------------|
| Fabricante | Independiente (multimarca) | ABB |
| Propósito | Simulación y programación offline de múltiples robots industriales | Simulación, programación y depuración específica de robots ABB |
| Lenguaje de programación | Genera código en el lenguaje de cada fabricante (ej. INFORM, RAPID, KRL, TP, etc.) | Usa **RAPID**, lenguaje nativo de ABB |
| Conexión con robot real | Mediante drivers genéricos o API de cada marca | Conexión directa con controladores ABB reales o virtuales (Virtual Controller) |
| Interfaz | Más abierta y compatible con software CAD/CAM | Más integrada al ecosistema ABB |
| Ideal para | Laboratorios, universidades, integración de robots mixtos | Empresas que usan exclusivamente robots ABB |

### Interpretación personal
- **RoboDK** representa una **plataforma versátil y universal**, útil para **aprender, integrar y comparar distintos robots** sin necesidad de hardware específico.  
- **RobotStudio**, en cambio, es una **herramienta especializada**, que permite **programar con precisión un robot ABB** tal como se comportaría en el entorno real, ideal para **automatización industrial profesional**.

---


---
## Cuadro comparativo de características técnicas del Motoman MH6 y el IRB140

| Característica             | Motoman MH6                          | ABB IRB 140                             |
|----------------------------|--------------------------------------|-----------------------------------------|
| Ejes                       | 6 :contentReference[oaicite:0]{index=0} | 6 :contentReference[oaicite:1]{index=1} |
| Carga útil (payload)       | 6 kg :contentReference[oaicite:2]{index=2} | 6 kg :contentReference[oaicite:3]{index=3} |
| Alcance horizontal (reach) | 1,422 mm :contentReference[oaicite:4]{index=4} | 810 mm (hasta el eje 5) :contentReference[oaicite:5]{index=5} |
| Repetibilidad               | ±0.08 mm :contentReference[oaicite:6]{index=6} | ±0.03 mm :contentReference[oaicite:7]{index=7} |
| Peso del robot              | 130 kg :contentReference[oaicite:8]{index=8} | 98 kg :contentReference[oaicite:9]{index=9} |
| Velocidad de ejes (máx.)    | J1: 220 °/s · J2: 200 °/s · J3: 220 °/s · J4: 410 °/s · J5: 410 °/s · J6: 610 °/s :contentReference[oaicite:10]{index=10} | J1: 200 °/s · J2: 200 °/s · J3: 260 °/s · J4: 360 °/s · J5: 360 °/s · J6: 450 °/s :contentReference[oaicite:11]{index=11} |
| Rango de movimiento de ejes | J1: ±170°; J2: +155° / –90°; J3: +250° / –175°; J4: ±180°; J5: +225° / –45°; J6: ±360° :contentReference[oaicite:12]{index=12} | J1: ±360°; J2: ±200°; J3: ±280°; J4: ±400°; J5: ±240°; J6: ±800° :contentReference[oaicite:13]{index=13} |
| Montaje permitido            | Piso, invertido, en ángulo :contentReference[oaicite:14]{index=14} | Piso, invertido, pared (ángulo cualquier) :contentReference[oaicite:15]{index=15} |
| Protección / ambiente        | Opción de IP67 en muñeca (para MH6) :contentReference[oaicite:16]{index=16} | IP67 estándar en brazos; versiones “Wash”, “Foundry” y “Clean Room” disponibles :contentReference[oaicite:17]{index=17} |
| Aplicaciones típicas         | Soldadura, ensamblaje, dispensado, manejo de materiales :contentReference[oaicite:18]{index=18} | Soldadura, limpieza/aspersión, manejo, empaquetado, etc. :contentReference[oaicite:19]{index=19} |




---
## Descripción de las configuraciones home1 y home2 del Motoman MH6

---
## Procedimiento detallado para realizar movimientos manuales

---
## Explicación sobre los niveles de velocidad para movimientos manuales

---
## Descripción de las principales funcionalidades de RoboDK

---
## Análisis comparativo entre RoboDK y RobotStudio

---
## Diagrama de flujo de acciones del robot

---
## Plano de planta

---
## Código RoboDK 

---
## Video de simulación e implementación

