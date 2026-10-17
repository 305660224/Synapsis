# Especificaciones Técnicas del Rig 2D (Avatar Elfo Alto)

## 1. Motor Gráfico Recomendado
Utilizar **PixiJS** (Web Canvas/WebGL) dentro de la aplicación para renderizar el Scene Graph.

## 2. Jerarquía de Capas (Z-Index)
Renderizar de atrás hacia adelante (0 es el fondo, 19 es el frente):
0. `hair_back`
1. `legs_L`, `legs_R` (Piernas de red)
2. `boots_L`, `boots_R` (Botas)
3. `arm_upper_L` (Brazo izquierdo atrás)
4. `neck` (Cuello)
5. `torso` (Top con cruz invertida rosa)
6. `bottom_shorts` (Shorts con bordes blancos)
7. `cardigan_back` (Parte trasera del cárdigan)
8. `arm_upper_R` (Brazo derecho frente)
9. `forearm_L`, `forearm_R` (Antebrazos)
10. `hand_L_idle`, `hand_R_idle` (Manos)
11. `ear_L`, `ear_R` (Orejas de elfo largas)
12. `head_base` (Rostro moteado)
13. `blush` (Rubor)
14. `mouth_neutral` (o el visema activo)
15. `eyes_open` (o el estado de ojos activo)
16. `eyebrows_neutral`
17. `hair_sides` (Mechones laterales)
18. `hair_bangs` (Flequillo)
19. `hat_beret` (Boina blanca)

## 3. Puntos de Pivote (Anchor Points X, Y)
Valores normalizados (0 a 1) para las rotaciones:
- `torso`: (0.5, 0.70) - Eje de la cintura.
- `bottom_shorts`: (0.5, 0.20) - Unión con el torso.
- `head_base`: (0.5, 0.90) - Base del cuello.
- `legs`: (0.5, 0.10) - Salida del muslo del short.
- `boots`: (0.5, 0.90) - Talón/Tobillo.
- `arms` y `forearms`: (0.5, 0.15) - Hombros y codos.
- `ears`, `hair_sides`: (0.5, 0.10) - Para oscilación elástica.

## 4. Comportamientos y Sincronización Labial
- **Idle (Reposo):** El `torso` escala suavemente en el eje Y (1.0 a 1.015) usando una función Seno para simular respiración. Parpadeo aleatorio (`eyes_open` -> `eyes_blink` -> `eyes_open`) cada 3 a 5 segundos.
- **Lip-Sync (Sin colmillos):** Al emitir texto/voz, alternar rápidamente entre `mouth_A`, `mouth_E`, `mouth_I`, `mouth_O`, `mouth_U`, y `mouth_HappyOpen`. Todas estas bocas usan dientes planos humanos.