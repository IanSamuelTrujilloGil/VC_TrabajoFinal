# Interfaz natural de usuario para videojuegos FPS
Control híbrido basado en Visión por Computador

Proyecto académico para la asignatura Visión por Computador (ULPGC). El sistema implementa un controlador híbrido para videojuegos FPS utilizando una única cámara, combinando:
- Seguimiento visual de un objeto físico para el apuntado y el disparo.
- Estimación de pose humana para el movimiento del personaje.

El prototipo se ha validado experimentalmente con Counter-Strike 2 como caso de uso. 

## Funcionalidades
- Apuntado del ratón mediante tracking visual de un objeto físico (pistola de juguete).
- Disparo detectando incrementos bruscos de brillo en la ROI del objeto seguido.
- Movimiento del personaje (W/A/D) mediante gestos corporales.
- Salto detectado por elevación y velocidad de cadera.
- Calibración guiada para pose y objeto.
- Filtros de estabilidad: EMA, antirrebote (debouncer), histéresis y cooldowns.
- Recuperación del tracking: CSRT + filtro de Kalman + template matching multiescala con veto HSV. 

## Tecnologías
- Python 3.10.19
- MediaPipe Pose Landmarker (modelo lite, modo VIDEO)
- OpenCV (opencv-contrib-python)
- NumPy
- pynput / xdotool (Linux) / pydirectinput y pygetwindow (Windows)
- Jupyter Notebook 

## Requisitos
- Webcam (probado con 720p)
- Linux o Windows
- En Linux: xdotool instalado

## Instalación
1) Clonar el repositorio:

    git clone URL_DEL_REPOSITORIO
    
2) Crear entorno e instalar dependencias.

Opción A (Conda, recomendada):

    conda env create -f environment.yml
    conda activate <nombre_entorno>

Opción B (pip):

    pip install -r requirements.txt

Solo Linux (dependencia del sistema):

Ejemplos de instalación de xdotool según la distribución:
- Ubuntu / Debian:
    - sudo apt install xdotool
- Arch Linux / Manjaro:
    - sudo pacman -S xdotool
- Fedora / Redhat:
    - sudo dnf install xdotool
- openSUSE:
    - sudo zypper install xdotool

## Ejecución
1) Abrir y ejecutar el notebook principal del proyecto.
2) Calibrar el objeto apuntador: 9 clics en 3 fases.
3) Calibrar la pose: postura neutral y postura forward.
4) Activar/desactivar modos de control desde los atajos de teclado.
5) Manteniendo el script en ejecución, cambiar el foco a la ventana del juego (Alt+Tab) para comenzar la interacción.

## Controles (teclado)
- Q / Esc: salir
- C: activar/desactivar control de ratón por cámara
- M: activar/desactivar control de movimiento por pose
- R: reiniciar calibración del objeto apuntador (tracker)
- P: reiniciar calibración del módulo de pose
- \+ / -: ajustar sensibilidad del ratón 

## Mapeo por defecto
- W: avanzar
- A / D: desplazamiento lateral
- Espacio: saltar
- Click izquierdo: disparar 

## Limitaciones
- En condiciones de alta dinámica, movimientos rápidos del objeto pueden generar desenfoque y provocar pérdida del objetivo por el tracker CSRT o reasignaciones erróneas hacia el fondo.
- La interacción asociada al disparo es sensible a la iluminación del entorno y a la distancia a la cámara; cambios de luz y escala pueden causar activaciones inconsistentes o que el disparo no se detecte de forma fiable. 
## Aviso
Proyecto experimental y académico. Se recomienda su uso en entornos controlados (p. ej., entrenamiento/servidores privados) y respetar los términos de servicio del software donde se utilice. 

## Autores
- Guillermo Raposo Iglesias
- Tycho Santana Quintana
- Ian Samuel Trujillo Gil

## Vídeo comercial
[![Ver Video Comercial](https://img.youtube.com/vi/MTQH-I_IvvM/0.jpg)](https://www.youtube.com/watch?v=MTQH-I_IvvM)

## Licencia
MIT. Ver el archivo [LICENSE](LICENSE).
