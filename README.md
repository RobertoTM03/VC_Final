# Neon Caster - Juego de Visión por Computador

**Proyecto Final de Visión por Computador Grupo 19**

**Autores:**
- Jesús Santacruz Martín-Delgado
- Roberto Tejero Martín

---

## Descripción

Neon Caster es un juego interactivo que utiliza **MediaPipe Pose** para detectar movimientos del cuerpo en tiempo real y controlar mecánicas de defensa y ataque. El jugador controla el personaje mediante gestos corporales capturados por la cámara web, sin necesidad de usar teclado o ratón.

El juego presenta un sistema progresivo de rondas con enemigos que aparecen desde los bordes de la pantalla, power-ups que caen desde arriba, y un sistema de combate basado en poses corporales específicas.

---

## Mecánicas del Juego

### Controles con el Cuerpo

- **Escudo (Brazos Cruzados):** Cruza los brazos sobre tu pecho para activar el escudo y bloquear enemigos. Consume un punto de escudo por uso.

- **Ataque de Área (Carga y Disparo):**
  1. Junta las manos al frente de tu cuerpo con los brazos extendidos para cargar energía
  2. Cuando la carga llegue al 100%, separa bruscamente las manos
  3. Esto lanzará un ataque de área que destruye todos los enemigos en pantalla
  4. Consume una bala por uso

- **Power-ups:** Alcanza los power-ups que caen desde arriba con las manos para recolectarlos

### Sistema de Juego

- **Vidas:** Empiezas con 3 vidas. Pierdes una vida cada vez que un enemigo te golpea sin escudo activo
- **Escudos:** Puedes tener hasta 3 escudos. Cada uso consume uno y tiene un cooldown de 4 segundos
- **Balas:** Puedes tener hasta 3 balas para el ataque de área
- **Rondas Progresivas:** Cada 50 puntos avanzas de ronda. Los enemigos se vuelven más rápidos y frecuentes
- **Puntuación:** Ganas 10 puntos por cada enemigo derrotado

### Power-ups

- **Corazón:** Recupera una vida (máximo 3)
- **Escudo:** Recupera un escudo (máximo 3)
- **Bala:** Recupera una bala (máximo 3)

---

## Modos de Juego y Postura del Jugador

Neon Caster permite jugar tanto **sentado** como **de pie**, adaptándose a distintos espacios y niveles de movilidad del jugador.

### Juego Sentado

El jugador puede realizar todos los gestos principales desde una posición sentada, manteniendo el torso y brazos visibles frente a la cámara.

Vídeo de ejemplo:
https://alumnosulpgc-my.sharepoint.com/:v:/g/personal/roberto_tejero101_alu_ulpgc_es/IQDEZA6_28htRKdY1EHStRS9AeeWfKcwhQc_BgtdQld8_Xo

### Juego de Pie

El modo de pie ofrece una experiencia más física e inmersiva, permitiendo mayor libertad de movimiento.

Vídeo de ejemplo:
https://alumnosulpgc-my.sharepoint.com/:v:/g/personal/roberto_tejero101_alu_ulpgc_es/IQAGLW4JzLcdSpJxVI1HPSFUAWbEbmhBtwA4_ce2pBZzxMs

---

## Instalación y Ejecución

### Requisitos

- Python 3.8 o superior
- Cámara web funcional

### Dependencias

```bash
pip install opencv-python mediapipe numpy pygame
```

### Ejecución

1. Asegúrate de tener todos los assets en la carpeta `assets/`
2. Abre el notebook `Trabajo_VC.ipynb` en Jupyter Notebook o VS Code
3. Ejecuta todas las celdas en orden
4. La última celda iniciará el juego
5. Colócate frente a la cámara con buena iluminación y espacio para moverte

---

## Características Técnicas

### Tecnologías Utilizadas

- **OpenCV:** Captura y procesamiento de video en tiempo real
- **MediaPipe Pose:** Detección de puntos clave del esqueleto humano (33 landmarks)
- **Pygame:** Motor de juego, renderizado de gráficos y gestión de audio
- **NumPy:** Cálculos matemáticos y manipulación de arrays

### Detección de Poses

El juego utiliza 13 puntos clave del cuerpo para detectar colisiones:
- Nariz (0)
- Hombros (11, 12)
- Codos (13, 14)
- Muñecas (15, 16)
- Caderas (23, 24)
- Rodillas (25, 26)
- Tobillos (27, 28)

### Configuración Personalizable

El juego incluye un sistema de configuración global con más de 30 parámetros ajustables:
- Dimensiones de pantalla y FPS
- Estadísticas del jugador (vidas, escudos, balas)
- Parámetros de cooldown y velocidades
- Comportamiento de enemigos y power-ups
- Sistema de rondas y dificultad

---

## Assets

El juego carga dinámicamente los siguientes recursos:

### Imágenes
- Sprites de enemigos (assets/enemies/)
- Iconos de HUD: corazones, escudos, balas
- Medallas de ronda (medal1.png, medal2.png, medal3.png)
- Efectos visuales (explosiones, escudo)

### Sonidos
- Impactos (`hit`)
- Bloqueo de escudo (`shield`)
- Ticks de cooldown (`tick`/`beep`)
- Banda sonora (`pixel`)
- Explosiones (`punch`)
- Game Over (`game_over`)
- Completado de ronda (`round`/`fanfare`/`victory`)
- Recolección de power-ups (`powerup`)

---

## Consejos de Juego

1. **Iluminación:** Asegúrate de tener buena iluminación frontal para una mejor detección
2. **Espacio:** Necesitas espacio suficiente para extender los brazos
3. **Cámara:** Colócate centrado en el encuadre de la cámara
4. **Ropa:** Evita ropa que se confunda con el fondo
5. **Estrategia:** Usa el escudo para enemigos individuales y guarda las balas para múltiples enemigos
6. **Power-ups:** Prioriza recoger power-ups cuando tus recursos estén bajos

---

## Notas de Desarrollo

- El juego usa detección de colisión basada en radio circular alrededor de los puntos clave del cuerpo
- Los enemigos tienen una fase de advertencia visual antes de aparecer
- El sistema de spawn se adapta dinámicamente a la puntuación y ronda actual
- Los power-ups solo aparecen cuando son necesarios (recursos no al máximo)
- Incluye sistema de efectos visuales (explosiones, flashes, ondas expansivas)

---

**¡Disfruta jugando a Neon Caster!**
