# UIDE-PROYECTO
JUEGO DE LA SERPIENTE.                                        
                                                          Fecha: 14 de Diciembre del 2024
#DIAGRAMA primera parte
https://lucid.app/lucidchart/c624f0f3-69e1-4b96-8097-506f4105c6cb/edit?page=0_0#

#DIAGRAMA segunda parte
https://lucid.app/lucidchart/73ba3369-3d43-4481-8107-efa520f47188/edit?page=0_0#

#DIAGRAMA tercera parte (final)
https://lucid.app/lucidchart/b068ec4f-76e6-47db-adba-136563d2694a/edit?page=0_0#

A continúan voy a detallar que funciones cumplen los códigos que eh utilizado para programar el Popular Juego de la Serpiente.

# Importación y Configuración Inicial 
importación de módulos:
•	pygame: Biblioteca para desarrollo de videojuegos.
•	time: Control del tiempo.
•	random: Generación de valores aleatorios.

# Inicialización de Pygame y Configuración de la Ventana
pygame.init() 
ancho = 600 
alto = 400
 pantalla = pygame.display.set_mode((ancho, alto)) pygame.display.set_caption("Popular Juego de la Serpiente")
Inicialización: Activa todas las funciones de pygame.
Configuración de la Ventana:
•	Tamaño de la ventana (600x400 píxeles).
•	Título de la ventana.

# Definición de Colores y Parámetros
blanco = (255, 255, 255) 
negro = (0, 0, 0) 
rojo = (213, 50, 80)
 verde = (0, 255, 0) 
azul = (50, 153, 213)
Colores: Definidos usando el formato RGB.

# Tamaño de la Serpiente y Velocidad
tamano_bloque = 20
 velocidad = 10
Tamaño del Bloque: Cada segmento de la serpiente mide 20x20 píxeles.
Velocidad: Control de la velocidad de movimiento.

# Fuentes de Texto y Reloj del Juego
fuente = pygame.font.SysFont("bahnschrift", 25)
 fuente_puntaje = pygame.font.SysFont("comicsansms", 30)
 reloj = pygame.time.Clock()
Fuentes: Configuración para mostrar mensajes y puntuaciones.
Reloj: Control del FPS del juego.

# Funciones Auxiliares
•	Mostrar puntaje: 
def puntaje(score):
    valor = fuente_puntaje.render(f"PUNTAJE: {score}", True, azul)
    pantalla.blit(valor, [0, 0])
Muestra la Puntuación: Dibuja la puntuación actual en la parte superior izquierda.
•	Dibujar la Serpiente:
def nuestra_serpiente(tamano_bloque, lista_serpiente):
    for bloque in lista_serpiente:
        pygame.draw.rect(pantalla, verde, [bloque[0], bloque[1], tamano_bloque, tamano_bloque])
Dibuja la Serpiente: Itera sobre lista_serpiente y dibuja cada segmento.
•	Mostrar Mensaje de Game Over:
def mensaje(msg, color):
    texto = fuente.render(msg, True, color)
    pantalla.blit(texto, [ancho / 6, alto / 3])
Muestra un Mensaje: Presenta un texto de "Perdiste" cuando termina el juego.

# Función Principal juego()
•	Inicialización de Variables:
x1 = ancho / 2
y1 = alto / 2
x1_cambio = 0
y1_cambio = 0
lista_serpiente = []
largo_serpiente = 1
 Posición Inicial: Centro de la pantalla.
Cambios de Dirección: Sin movimiento inicial.
Lista de la Serpiente: Contendrá sus segmentos.
Tamaño Inicial: Un solo segmento.

•	Generación de la Comida:
comida_x = round(random.randrange(0, ancho - tamano_bloque) / 20.0) * 20.0
comida_y = round(random.randrange(0, alto - tamano_bloque) / 20.0) * 20.0
Posición Aleatoria: La comida aparece en posiciones múltiples de 20 píxeles.

•	Bucle Principal del Juego:
while not game_over:
Bucle Principal: Se ejecuta hasta que el jugador pierda o cierre la ventana.

•	Pantalla de "Game Over":
while game_close:
    pantalla.fill(negro)
    mensaje("Perdiste! Presiona Q-Salir o C-Continuar", rojo)
    puntaje(largo_serpiente - 1)
    pygame.display.update()
Pantalla Final: Opción de salir (Q) o reiniciar (C).

•	Detección de Eventos del Teclado:
if event.key == pygame.K_LEFT:
    x1_cambio = -tamano_bloque
    y1_cambio = 0
Eventos de Movimiento: Cambios en la dirección según las teclas de flecha.

•	Colisiones con los Bordes:
if x1 >= ancho or x1 < 0 or y1 >= alto or y1 < 0:
    game_close = True
Colisiones con los Bordes: El juego termina si la serpiente toca los límites de la ventana.

•	Movimiento y Actualización:
x1 += x1_cambio
y1 += y1_cambio
pantalla.fill(negro)
Actualización de la Posición: Mueve la serpiente y actualiza la pantalla.

•	Colisiones con la Comida:
if x1 == comida_x and y1 == comida_y:
    comida_x = round(random.randrange(0, ancho - tamano_bloque) / 20.0) * 20.0
    comida_y = round(random.randrange(0, alto - tamano_bloque) / 20.0) * 20.0
    largo_serpiente += 1
Si Come la Comida: La serpiente crece y la comida se reposiciona.

•	Dibujo Final:
nuestra_serpiente(tamano_bloque, lista_serpiente)
puntaje(largo_serpiente - 1)
pygame.display.update()
Dibuja Todo: Actualiza la pantalla con la nueva posición.

•	Finalización del Juego:
pygame.quit()
quit()
Cerrar el Juego: Finaliza la ejecución correctamente.

Conclusió.
El código implementa el clásico Juego de la Serpiente usando Pygame, gestionando eventos de teclado, colisiones y detección de comida. Todo está estructurado con funciones bien organizadas para mostrar puntajes, mensajes y dibujar elementos en pantalla. El diseño es modular y permite fácil expansión y personalización.
