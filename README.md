# 🤖 Informe Laboratorio No. 02 – Análisis y Operación del Manipulador Motoman MH6


---

## 📘 Descripción general

Este repositorio contiene el **informe técnico y material complementario** del **Laboratorio No. 02 – Análisis y Operación del Manipulador Motoman MH6**, desarrollado en el marco del curso de **Robótica – Facultad de Ingeniería, Universidad Nacional de Colombia (UNAL)** durante el semestre **2025-II**.

El propósito del laboratorio es comprender el **funcionamiento, modos de operación y comunicación** del robot industrial **Motoman MH6** mediante el **controlador Yaskawa DX100** y la **simulación en RoboDK**.  
Además, se comparan las capacidades del MH6 frente al **ABB IRB 140**, y se analiza el uso de herramientas de simulación **RoboDK vs. RobotStudio**.

---

## 👥 Autores

- **Esteban Durán Jiménez**  
- **Ana María Orozco Reyes**

**Facultad de Ingeniería – Universidad Nacional de Colombia**  
**Curso: Robótica | 2025-II**

---

## 🧩 Contenido del repositorio

| Carpeta / Archivo | Descripción |
|-------------------|-------------|
| `Informe_Lab2_Motoman_MH6.md` | Informe principal con respuestas, análisis y comparaciones técnicas. |
| `Imagenes/` | Imágenes de apoyo incluidas en el informe (diagramas, logos, capturas del Teach Pendant, etc.). |
| `planos/` | Planos de planta y disposición de la celda robótica. |
| `videos/` o enlace externo | Registro audiovisual de la simulación y prueba práctica del robot. |
| `README.md` | Este archivo: descripción general del proyecto y guía de navegación. |

---

## 🧠 Temas principales abordados

1. **Diferencias entre HOME1 y HOME2 del Motoman MH6.**  
2. **Movimiento manual del manipulador** mediante el *Teach Pendant* (DX100).  
3. **Niveles de velocidad** y su configuración desde el controlador.  
4. **Aplicaciones y comunicación de RoboDK** con el robot.  
5. **Comparativa entre RoboDK y RobotStudio.**  
6. **Análisis técnico** entre **Motoman MH6** y **ABB IRB 140.**  
7. **Diagrama de flujo** y **planos de planta** de la celda experimental.  
8. **Video de simulación e implementación.**

---

## ⚙️ Herramientas y software utilizados

| Herramienta | Función |
|--------------|---------|
| **Yaskawa DX100 Controller** | Control del robot Motoman MH6. |
| **Teach Pendant Motoman** | Operación manual y programación básica. |
| **RoboDK** | Simulación y programación offline multimarca. |
| **RobotStudio** | Simulación avanzada de robots ABB. |
| **SolidWorks / Fusion 360** | Modelado CAD y trayectorias CAM. |

---

## 📊 Comparaciones clave

| Aspecto | Motoman MH6 | ABB IRB 140 |
|----------|--------------|-------------|
| Carga útil | 6 kg | 6 kg |
| Alcance | 1422 mm | 810 mm |
| Repetibilidad | ±0.08 mm | ±0.03 mm |
| Peso | 130 kg | 98 kg |
| Aplicaciones típicas | Soldadura, ensamblaje, manejo de materiales | Ensamblaje, empaquetado, soldadura |

---

## 🧰 Procedimientos destacados

- Encendido y habilitación de servos (`Servo ON Ready`).  
- Selección de modos de coordenadas (`JOINT`, `BASE`, `TOOL`, `USER`).  
- Uso del *Deadman Switch* para seguridad.  
- Ajuste de velocidades de jogging (`SHIFT + SPEED ±`).  
- Registro y retorno a posiciones HOME1 y HOME2.  
- Comunicación RoboDK ↔ DX100 via TCP/IP.

---

## 📺 Video de simulación e implementación

🎥 [Ver simulación en Google Drive](https://drive.google.com/file/d/1pG5Jd7inoIBH1-W4YGltWOecrmIMRyJh/view?usp=sharing)

---

## 🧾 Licencia y uso académico

Este proyecto fue desarrollado con fines **académicos y de aprendizaje** dentro del curso de **Robótica – UNAL 2025-II**.  
El contenido puede ser reutilizado con fines educativos, citando a los autores y la institución.

---

## 💬 Contacto

Si deseas más información o referencias adicionales:

- 📧 **Esteban Durán Jiménez** – [correo institucional o GitHub Profile]  
- 📧 **Ana María Orozco Reyes** – [correo institucional o GitHub Profile]  

---
