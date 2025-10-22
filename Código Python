from robodk.robolink import *    # API para comunicarte con RoboDK
from robodk.robomath import *    # Funciones matemáticas
import math

#------------------------------------------------
# 1) Conexión a RoboDK e inicialización
#------------------------------------------------
RDK = Robolink()

# Elegir un robot (si hay varios, aparece un popup)
robot = RDK.ItemUserPick("Selecciona un robot", ITEM_TYPE_ROBOT)
if not robot.Valid():
    raise Exception("No se ha seleccionado un robot válido.")

# Conectar al robot físico
#if not robot.Connect():
    #raise Exception("No se pudo conectar al robot. Verifica que esté en modo remoto y que la configuración sea correcta.")

# Confirmar conexión
#if not robot.ConnectedState():
    #raise Exception("El robot no está conectado correctamente. Revisa la conexión.")

print("Robot conectado correctamente.")

#------------------------------------------------
# 2) Cargar el Frame (ya existente) donde quieres dibujar
#    Ajusta el nombre si tu Frame se llama diferente
#------------------------------------------------
frame_name = "Frame_from_Target1"
frame = RDK.Item(frame_name, ITEM_TYPE_FRAME)
if not frame.Valid():
    raise Exception(f'No se encontró el Frame "{frame_name}" en la estación.')

# Asignamos este frame al robot
robot.setPoseFrame(frame)
# Usamos la herramienta activa
robot.setPoseTool(robot.PoseTool())

# Ajustes de velocidad y blending
robot.setSpeed(300)   # mm/s - Ajusta según necesites
robot.setRounding(5)  # blending (radio de curvatura)

#------------------------------------------------
# 3) Parámetros de la figura (rosa polar)
#------------------------------------------------
num_points = 720       # Cuántos puntos muestreamos (mayor = más suave)
A = 150               # Amplitud (300 mm = radio máximo)
k = 5                  # Parámetro de la rosa (pétalos). Si es impar, habrá k pétalos; si es par, 2k
z_surface = 0          # Z=0 en el plano del frame
z_safe = 50            # Altura segura para aproximarse y salir

#------------------------------------------------
# NUEVO BLOQUE: función para escribir texto antes de dibujar la rosa
#------------------------------------------------
letter_scale = 15      # Tamaño de las letras
spacing = 60           # Distancia entre líneas

def escribir_texto(texto, x0, y0, z0):
    """Escribe texto básico usando trayectorias lineales simples."""
    letras = {
        'A': [(0,0),(0,2),(1,3),(2,2),(2,0),(2,1),(0,1),(2,1)],
        'N': [(0,0),(0,3),(2,0),(2,3)],
        'E': [(2,0),(0,0),(0,3),(2,3),(0,3),(0,1.5),(1.5,1.5)],
        'S': [(0,0),(2,0),(2,1.5),(0,1.5),(0,3),(2,3)],
        'T': [(0,3),(2,3),(1,3),(1,0)],
        'B': [(0,0),(0,3),(1.5,3),(2,2.5),(1.5,2),(0,2),(1.5,2),(2,0.75),(1.5,0),(0,0)],
    }

    # Ángulo de rotación +90° (radianes)
    ang = math.radians(90)
    cos_a = math.cos(ang)
    sin_a = math.sin(ang)

    x_cursor = x0
    for letra in texto.upper():
        if letra == " ":
            x_cursor += 3 * letter_scale
            continue
        if letra not in letras:
            x_cursor += 2 * letter_scale
            continue

        puntos = letras[letra]

        # Mover al inicio de la letra
        x, y = puntos[0]
        y = -y  # <-- corregimos espejo
        # Rotamos +90° alrededor del eje Z del TCP
        x_rot =  cos_a*x - sin_a*y
        y_rot =  sin_a*x + cos_a*y

        robot.MoveL(transl(x_cursor + x_rot*letter_scale, y0 + y_rot*letter_scale, z0 - z_safe))
        robot.MoveL(transl(x_cursor + x_rot*letter_scale, y0 + y_rot*letter_scale, z0))

        # Trazo
        for (x, y) in puntos[1:]:
            y = -y
            x_rot =  cos_a*x - sin_a*y
            y_rot =  sin_a*x + cos_a*y
            robot.MoveL(transl(x_cursor + x_rot*letter_scale, y0 + y_rot*letter_scale, z0))

        # Subir antes de ir a la siguiente letra
        robot.MoveL(transl(x_cursor + x_rot*letter_scale, y0 + y_rot*letter_scale, z0 - z_safe))
        x_cursor += 4 * letter_scale  # Avance horizontal, permite modificar espacio entre letras

#------------------------------------------------
# NUEVO BLOQUE: escribir "Ana" y "Esteban" arriba de la rosa
#------------------------------------------------
# Posición base del texto: encima del centro de la rosa
x_start = -100
y_center_rosa = 0  # Centro de la rosa en Y
y_start = y_center_rosa + 3*spacing + 40  # Ajuste para colocar los nombres arriba

# Escribir "Ana"
escribir_texto("Ana", x_start, y_start, z_surface)

# Escribir "Esteban" debajo de "Ana"
escribir_texto("Esteban", x_start, y_start - spacing, z_surface)

#------------------------------------------------
# 4) Movimiento al centro en altura segura
#------------------------------------------------
# El centro de la rosa (r=0) corresponde a x=0, y=0
# (Se ajusta posición para colocar la rosa debajo del texto)
robot.MoveJ(transl(0, y_center_rosa, z_surface - z_safe))

# Bajamos a la "superficie" (Z=0)
robot.MoveL(transl(0, y_center_rosa, z_surface))

#------------------------------------------------
# 5) Dibujar la rosa polar
#    r = A * sin(k*theta)
#    x = r*cos(theta), y = r*sin(theta)
#------------------------------------------------
# Recorremos theta de 0 a 2*pi (una vuelta completa)
full_turn = 2*math.pi

for i in range(num_points+1):
    # Fracción entre 0 y 1
    t = i / num_points
    # Ángulo actual
    theta = full_turn * t

    # Calculamos r
    r = A * math.sin(k * theta)

    # Convertimos a coordenadas Cartesianas X, Y
    x = r * math.cos(theta)
    y = r * math.sin(theta) + y_center_rosa  # desplazamiento vertical al centro de la rosa

    # Movemos linealmente (MoveL) en el plano del Frame
    robot.MoveL(transl(x, y, z_surface))

# Al terminar, subimos de nuevo para no chocar
robot.MoveL(transl(x, y, z_surface - z_safe))

print(f"¡Texto (rotado 90° y arriba) y figura (rosa polar) completados en el frame '{frame_name}'!")
