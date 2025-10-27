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

## Sección de preguntas:


### Describir las diferencias entre el home1 y el home2 del Motoman MH6.

### 1. Movimiento manual del manipulador Motoman

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

### 2. Niveles de velocidad del Motoman

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

### 3. Aplicaciones principales de RoboDK

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

### 4. Comunicación entre RoboDK y el manipulador

- Se establece una **conexión TCP/IP** entre RoboDK y el controlador del robot (por ejemplo, DX200).  
- RoboDK actúa como un **cliente**, enviando los comandos de posición y lectura de estado al **servidor del controlador**.  
- El protocolo puede variar según el fabricante, pero en Motoman generalmente se utiliza **MotoCOM o el driver Yaskawa RoboDK API**.  
- Una vez conectado, los movimientos simulados en RoboDK se replican en tiempo real en el manipulador físico.

---

### 5. Diferencias entre RoboDK y RobotStudio

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
### Cuadro comparativo de características técnicas del Motoman MH6 y el IRB140

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

### Descripción de las configuraciones HOME1 y HOME2 del Motoman MH6

El robot **Motoman MH6**, controlado mediante el sistema **Yaskawa DX100**, cuenta con dos configuraciones principales de posición de referencia: **HOME1** y **HOME2**. Ambas posiciones están definidas en el controlador y pueden configurarse o ajustarse desde el **Teach Pendant**, sirviendo como puntos seguros para inicio, paro o transporte del manipulador.

---

### 🔹 HOME1 – Posición base o de referencia principal
- **Definición:** corresponde a la posición estándar de referencia del robot.  
- **Configuración típica:** todos los ejes alineados en sus ángulos de cero grados (`J1=0°, J2=0°, J3=0°, J4=0°, J5=0°, J6=0°`).
- **Propósito:**
  - Punto de **inicio** y **finalización** de los programas de trabajo.
  - Facilita la **calibración** y verificación de límites articulares.
  - Asegura una **posición estable y libre de colisiones**.
- **Acceso:** puede moverse a HOME1 mediante una instrucción de tipo `MOVJ` en el programa o manualmente seleccionando la posición registrada.

> 📘 Según el manual del DX100, las posiciones de referencia (puntos base o REFP) pueden registrarse directamente con la tecla `[REFP]` o desde el menú de *job programming*, asegurando que el manipulador retorne al punto seguro antes de ejecutar o finalizar un ciclo:contentReference[oaicite:0]{index=0}.

---

### 🔹 HOME2 – Posición compacta o de transporte
- **Definición:** segunda configuración de referencia, **definida por el usuario**, orientada a fines logísticos o de mantenimiento.
- **Propósito y ventajas:**
  - Ubica al robot en una **postura más compacta**, reduciendo el espacio ocupado y facilitando su **transporte o almacenamiento**.
  - Permite que el robot quede **soportado sobre sí mismo**, minimizando la carga sobre los actuadores y **evitando el uso innecesario de los frenos**.
  - Se emplea también para **movimientos intermedios o de estacionamiento seguro** dentro del área de trabajo.
- **Programación:** puede registrarse manualmente moviendo el robot a la posición deseada y guardándola como `HOME2` desde el Teach Pendant (`RECORD POS → HOME2`).
- **Ejemplo práctico:** en la imagen adjunta, el MH6 se encuentra en su **HOME2**, con el brazo plegado y el efector final hacia adentro, ocupando un volumen mínimo y protegido contra desplazamientos accidentales.

---

### 🔧 Observación general
Ambas configuraciones son esenciales para el trabajo seguro y eficiente del robot:
- **HOME1** se utiliza para **referencia y calibración.**
- **HOME2** se utiliza para **transporte y reposo prolongado.**

> En la práctica industrial, se recomienda **verificar las posiciones HOME** antes de ejecutar cualquier programa, especialmente después de reiniciar el controlador o mover el robot manualmente.


---
### Procedimiento detallado para realizar movimientos manuales en el Motoman MH6 (Controlador DX100)

El movimiento manual del robot **Motoman MH6**, controlado mediante el sistema **Yaskawa DX100**, se realiza a través del **Teach Pendant**, siguiendo una secuencia de pasos segura que garantiza el control total de los ejes y la correcta selección del modo de operación.  
A continuación se detalla el procedimiento completo:

---

### 🔹 1. Preparación del sistema
1. **Encender el controlador DX100** y verificar que no existan alarmas activas.  
2. **Seleccionar el modo “TEACH”** mediante el interruptor de modo (llave de seguridad o selector físico).  
   - Este modo permite el control directo de los ejes desde el colgante.  
3. **Activar el servo power:** presionar el botón `[SERVO ON READY]` o equivalente en el panel del Teach Pendant.  
4. Confirmar que el **“Deadman switch”** (interruptor de seguridad en la parte trasera del colgante) funcione correctamente.  
   - El robot solo se moverá cuando este interruptor esté presionado parcialmente.

---

### 🔹 2. Selección del tipo de movimiento
En el Teach Pendant, usar la tecla `[COORD]` para alternar entre los diferentes sistemas de coordenadas:
- **JOINT:** movimientos por articulaciones (J1 a J6).  
- **BASE / WORLD:** movimientos cartesianos respecto al sistema global.  
- **TOOL:** movimientos relativos a la herramienta (TCP).  
- **USER:** sistema definido por el usuario según la celda o aplicación.

La selección actual se muestra en la parte superior de la pantalla del colgante.

---

### 🔹 3. Ejecución de movimientos manuales

#### 🔸 a) Movimiento por articulaciones
1. Verificar que el modo de coordenadas sea `JOINT`.  
2. Utilizar las teclas direccionales de eje (`+J1 / -J1`, ..., `+J6 / -J6`) para mover individualmente cada articulación.  
3. Mantener presionado el **Deadman switch** mientras se pulsa la dirección deseada.  
4. Observar en la pantalla la variación angular de cada eje en tiempo real.

#### 🔸 b) Movimiento cartesiano (traslación y rotación)
1. Cambiar a modo `BASE` o `TOOL` presionando `[COORD]`.  
2. Usar las siguientes teclas para traslaciones:
   - `+X / -X` → avance o retroceso en eje X.  
   - `+Y / -Y` → desplazamiento lateral.  
   - `+Z / -Z` → elevación o descenso.
3. Para rotaciones:
   - `+Rx / -Rx`, `+Ry / -Ry`, `+Rz / -Rz` → rotaciones alrededor de los ejes cartesianos.  
4. Mantener el **Deadman switch** activado durante el movimiento.

---

### 🔹 4. Control de velocidad manual
- La velocidad se puede ajustar mediante las teclas:  
  - `[SHIFT] + [+SPEED]` → aumenta velocidad.  
  - `[SHIFT] + [-SPEED]` → reduce velocidad.  
- El nivel actual (porcentaje de velocidad) aparece en la parte superior de la pantalla del Teach Pendant.  
- En el manual DX100 se indica que la velocidad de jogging puede limitarse entre **1% y 100%** para mayor seguridad:contentReference[oaicite:0]{index=0}.

---

### 🔹 5. Finalización del movimiento
1. Llevar el robot a una posición segura o HOME (preferiblemente **HOME1 o HOME2**).  
2. Soltar el Deadman switch.  
3. Apagar el servo con `[SERVO OFF]` si no se realizarán más movimientos.  
4. Registrar posiciones si se desea guardar puntos de trabajo (`RECORD POS`).

---

### ⚙️ Recomendaciones de seguridad
- No ejecutar movimientos sin mantener presionado el **Deadman switch**.  
- Mantener despejada el área de trabajo.  
- No exceder la velocidad manual recomendada durante pruebas o calibración.  
- Verificar el sentido de los ejes antes de moverlos, especialmente en modo TOOL.

---

> ✅ **Resumen:**  
> El procedimiento de movimiento manual en el Motoman MH6 con controlador DX100 consiste en **habilitar el modo Teach**, **activar los servos**, **seleccionar el sistema de coordenadas adecuado**, y **mover el robot manualmente por ejes o en coordenadas cartesianas**, controlando la velocidad y seguridad mediante el Teach Pendant y el Deadman switch.


---
### Explicación sobre los niveles de velocidad para movimientos manuales

El controlador **Yaskawa DX100** del robot **Motoman MH6** permite ajustar la **velocidad de movimiento manual (jogging)** mediante distintos niveles y porcentajes, ofreciendo precisión y seguridad durante la manipulación del robot.

---

### 🔹 1. Concepto general
Los **niveles de velocidad** determinan la rapidez con la que el robot se mueve cuando es operado manualmente desde el **Teach Pendant**.  
Estas velocidades no afectan los programas automáticos, sino únicamente los desplazamientos realizados en modo **TEACH**.

El rango de ajuste está comprendido entre **1 % y 100 %** de la velocidad máxima de jogging, y se puede modificar fácilmente en tiempo real durante la operación:contentReference[oaicite:0]{index=0}.

---

### 🔹 2. Tipos de velocidad en el movimiento manual
Existen tres niveles habituales:

| Nivel | Descripción | Uso recomendado |
|-------|--------------|-----------------|
| **Baja (10 %)** | Movimiento lento y preciso. | Calibración, acercamiento a piezas o herramientas, enseñanza de puntos finos. |
| **Media (50 %)** | Velocidad intermedia. | Ajustes o comprobaciones rápidas con control visual. |
| **Alta (100 %)** | Velocidad máxima permitida en modo manual. | Movimientos amplios o desplazamientos entre zonas seguras. |

El operador puede limitar la velocidad por seguridad, especialmente cuando hay riesgo de colisión o durante pruebas iniciales.

---

### 🔹 3. Configuración y cambio de velocidad
- El cambio de nivel de velocidad se realiza mediante las combinaciones de teclas:
  - `[SHIFT] + [+SPEED]` → Aumenta la velocidad.
  - `[SHIFT] + [-SPEED]` → Disminuye la velocidad.
- También puede modificarse desde el menú **Setup > Jog Speed** o dentro de la ventana **Speed Modification**, donde se elige el **tipo de velocidad (SPEED KIND)** y se introduce un valor numérico manualmente:contentReference[oaicite:1]{index=1}.

---

### 🔹 4. Identificación del nivel en pantalla
El nivel de velocidad activo se muestra en la parte superior del **Teach Pendant**, expresado como un **porcentaje (%)** o como una **etiqueta** (`LOW`, `MID`, `HIGH`).  
Durante el movimiento manual, esta referencia se actualiza en tiempo real para indicar la velocidad efectiva de los ejes.

---

### 🔹 5. Recomendaciones de seguridad
- Utilizar velocidades bajas al acercarse a objetos o personas.  
- No superar el 50 % durante operaciones de calibración o aprendizaje.  
- Confirmar siempre la dirección del eje antes de aplicar alta velocidad.  
- Mantener presionado el **Deadman Switch** mientras se efectúa cualquier movimiento.

---

> ✅ **En resumen:**  
> Los niveles de velocidad en el modo manual del Motoman MH6 permiten controlar la rapidez y seguridad de los movimientos de enseñanza. Se ajustan desde el **Teach Pendant**, se visualizan en pantalla y garantizan una operación segura y precisa durante la programación o calibración del robot.

---
##### Descripción de las principales funcionalidades de RoboDK

**RoboDK** es una plataforma de **simulación y programación offline** para robots industriales de múltiples marcas.  
Permite crear, verificar y ejecutar programas robóticos sin necesidad de tener el robot físico encendido, facilitando el desarrollo, la enseñanza y la integración de celdas automatizadas.

---

### 🔹 1. Simulación de robots industriales
RoboDK ofrece un entorno 3D donde se pueden **simular trayectorias, movimientos y procesos industriales** de diferentes robots (ABB, Yaskawa, KUKA, FANUC, UR, entre otros).  
Esto permite:
- Visualizar el comportamiento del robot antes de ejecutarlo físicamente.  
- Detectar **colisiones** entre el robot, herramientas, piezas o estructuras.  
- Validar **alcances**, zonas de trabajo y configuraciones articulares.

---

### 🔹 2. Programación offline (OLP)
RoboDK permite crear programas completos sin usar el controlador real del robot.  
Una vez verificada la simulación, el programa se **exporta en el lenguaje nativo del fabricante**:
- ABB → RAPID  
- Yaskawa Motoman → INFORM  
- KUKA → KRL  
- FANUC → TP  
- Universal Robots → URScript  

De esta forma, se reducen los tiempos de parada del robot y se facilita el desarrollo desde el computador.

---

### 🔹 3. Integración con CAD/CAM
El software permite importar trayectorias desde programas de diseño y mecanizado (como SolidWorks, Fusion 360 o CATIA) y **convertirlas automáticamente en movimientos robóticos**.  
Esto es muy útil para aplicaciones de:
- Corte y mecanizado CNC con robots.  
- Pulido, pintura, dispensado y soldadura.

---

### 🔹 4. Generación y gestión de trayectorias
RoboDK permite:
- Definir **puntos de referencia (targets)** y trayectorias interpoladas (lineales o por articulaciones).  
- Editar manualmente posiciones, velocidades y orientaciones.  
- Sincronizar movimientos del robot con **herramientas externas** (bandas, mesas giratorias, ejes adicionales).

---

### 🔹 5. Comunicación y control en tiempo real
RoboDK puede comunicarse directamente con un manipulador físico mediante una **conexión Ethernet o TCP/IP**, utilizando el **driver del fabricante**.  
Esto permite:
- Controlar el robot en tiempo real desde la computadora.  
- Verificar la ejecución de trayectorias simuladas.  
- Enviar programas directamente al controlador (por ejemplo, DX100 o DX200 en el caso de Motoman).

---

### 🔹 6. Compatibilidad multimarca
Una de sus mayores ventajas es su **carácter universal**:  
RoboDK incluye bibliotecas con más de 500 modelos de robots industriales de diferentes fabricantes, permitiendo trabajar con varios tipos de robots dentro de una misma celda o proyecto.

---

### 🔹 7. Aplicaciones principales
RoboDK se utiliza ampliamente en:
- **Soldadura y pintura robótica.**  
- **Paletizado y manipulación de materiales.**  
- **Inspección y medición automatizada.**  
- **Educación y entrenamiento en robótica industrial.**  
- **Simulación de procesos de manufactura flexible.**

---

> ✅ **En resumen:**  
> RoboDK es una herramienta integral que permite **simular, programar, optimizar y comunicar robots industriales** sin necesidad de programarlos directamente en su controlador.  
> Su entorno visual, compatibilidad con múltiples marcas y facilidad para generar trayectorias lo convierten en una solución potente tanto para **entornos industriales como educativos.**


---
## Análisis comparativo entre RoboDK y RobotStudio

Tanto **RoboDK** como **RobotStudio** son herramientas de simulación y programación de robots industriales, pero difieren en su enfoque, compatibilidad y nivel de especialización.  
A continuación se presenta un análisis comparativo entre ambas plataformas.

---

### 🔹 1. Propósito y alcance

| Característica | **RoboDK** | **RobotStudio** |
|----------------|-------------|-----------------|
| **Fabricante** | Independiente (multimarca) | ABB Robotics |
| **Enfoque principal** | Simulación y programación **offline** de robots de distintas marcas. | Simulación, programación y control específico de **robots ABB**. |
| **Uso típico** | Educación, integración de celdas mixtas y proyectos de investigación. | Industria automatizada con robots ABB y controladores IRC5 u OmniCore. |

---

### 🔹 2. Compatibilidad y soporte

| Aspecto | **RoboDK** | **RobotStudio** |
|----------|-------------|-----------------|
| **Compatibilidad** | Compatible con más de **500 modelos de robots** de diferentes fabricantes (Yaskawa, KUKA, FANUC, UR, etc.). | Solo compatible con **robots ABB**. |
| **Lenguaje de programación** | Genera código en el lenguaje nativo de cada fabricante (INFORM, RAPID, KRL, TP, URScript, etc.). | Usa **RAPID**, lenguaje nativo de ABB. |
| **Exportación de programas** | Permite exportar y ejecutar programas directamente en diferentes controladores. | Exporta y sincroniza programas RAPID con controladores ABB reales o virtuales. |

---

### 🔹 3. Simulación y entorno gráfico

| Aspecto | **RoboDK** | **RobotStudio** |
|----------|-------------|-----------------|
| **Simulación 3D** | Realista, intuitiva y rápida; permite verificar colisiones, trayectorias y sincronización con ejes externos. | Simulación de alta precisión con entorno gráfico más detallado y física realista. |
| **Interfaz** | Interfaz simple y ligera, fácil de aprender para estudiantes. | Interfaz avanzada e integrada con herramientas profesionales de ingeniería ABB. |
| **Bibliotecas** | Amplia base de datos de robots, herramientas y accesorios. | Biblioteca completa de componentes ABB, modelos de celdas y periféricos. |

---

### 🔹 4. Conectividad y control

| Aspecto | **RoboDK** | **RobotStudio** |
|----------|-------------|-----------------|
| **Conexión con robot real** | A través de drivers o conexión **TCP/IP** según el fabricante. | Conexión directa mediante **Virtual Controller**, idéntico al controlador real ABB. |
| **Modo de operación** | Puede trabajar **offline** o **online**, con control remoto del robot. | Simula exactamente el comportamiento del robot físico en un entorno virtual ABB. |
| **Intercambio de datos** | Soporte para intercambio CAD/CAM y comunicación con software externo (Python API, Fusion 360, SolidWorks). | Integración con sistemas ABB, PLCs y herramientas de diagnóstico industrial. |

---

### 🔹 5. Aplicaciones y usuarios

| Aspecto | **RoboDK** | **RobotStudio** |
|----------|-------------|-----------------|
| **Usuarios principales** | Universidades, integradores de sistemas, desarrolladores y centros de formación. | Ingenieros de automatización, fabricantes y técnicos ABB. |
| **Aplicaciones comunes** | Soldadura, mecanizado, paletizado, ensamblaje, inspección. | Soldadura, pintura, pulido, ensamblaje automatizado ABB. |
| **Licenciamiento** | Más flexible y económico. | Licencia profesional con módulos especializados ABB. |

---

### 🔹 6. Interpretación general

- **RoboDK** representa una herramienta **versátil, accesible y educativa**, ideal para **aprender y simular diferentes marcas de robots**.  
  Permite experimentar con programación y optimización sin depender de un fabricante específico.

- **RobotStudio** es una plataforma **especializada y profesional**, diseñada para **entornos industriales ABB**, donde se requiere precisión, control de procesos y validación exacta de los programas RAPID.

---

> ✅ **Conclusión:**  
> - **RoboDK** es ideal para entornos **académicos, de investigación y proyectos multirobot** por su flexibilidad y compatibilidad.  
> - **RobotStudio** es la mejor opción para **automatización profesional con robots ABB**, ofreciendo una simulación idéntica al comportamiento real del equipo.  
>  
> En conjunto, ambas herramientas se complementan: **RoboDK** fomenta la formación y el prototipado, mientras que **RobotStudio** garantiza la **implementación industrial precisa**.

---
## Diagrama de flujo de acciones del robot
<p align="center">
<img src="Imagenes/Diagrama flujo lab 2.png" alt="UNAL" width="300"/>
</p>

---
## Plano de planta

<p align="center">
<img src="planos/Plano 1.png" alt="UNAL" width="600"/>
</p>

<p align="center">
<img src="planos/Plano 2.png" alt="UNAL" width="600"/>
</p>

---

## Video de simulación e implementación
https://drive.google.com/file/d/1pG5Jd7inoIBH1-W4YGltWOecrmIMRyJh/view?usp=sharing

