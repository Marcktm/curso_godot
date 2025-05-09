
# 🎮 Clase 2 - Nuestro Primer Juego en Godot

En esta clase construimos nuestro primer juego **interactivo con colisiones** en Godot. Creamos un escenario en el que un **camioncito rojo** se mueve por una carretera y, al chocar con un **auto azul rival**, aparece un cartel de **Game Over**. 🚗💥

---

## 🧩 Objetivos de la clase

- Aplicar movimiento básico con `CharacterBody2D`.
- Detectar colisiones con otros objetos usando `get_slide_collision_count()` y `get_slide_collision()`.
- Mostrar un cartel de "Game Over" al colisionar.
- Agregar un fondo decorativo (la carretera).
- Restringir los límites del movimiento usando nodos de colisión.

---

## 🗂️ Nodos utilizados

- `Camioncito`: nodo principal con script de movimiento.
- `Rival`: nodo con `CollisionShape2D` que actúa como obstáculo.
- `GameOverLabel`: nodo `Label` o `TextureRect` oculto que aparece al perder.
- `Fondo`: imagen o `Sprite2D` de la carretera.
- `Limites`: `StaticBody2D` o `Area2D` con colisionadores para evitar que el jugador se salga.

---

## 🧠 Lógica del movimiento y colisión

```gdscript
# Movimiento
if Input.is_action_pressed("ui_right"):
    direccion.x += 1

# Normalizamos para que no sea más rápido en diagonal
direccion = direccion.normalized()
velocity = direccion * velocidad
move_and_slide()

# Colisión
if get_slide_collision_count() > 0:
    for i in range(get_slide_collision_count()):
        var colision = get_slide_collision(i)
        if colision.get_collider().name == "rival":
            mostrar_game_over()
```

---

## 🟥 Función de Game Over

```gdscript
func mostrar_game_over():
    var game_over = get_tree().get_current_scene().get_node("GameOverLabel")
    game_over.visible = true
    set_physics_process(false)  # Detenemos el movimiento
```

---

## 🎨 Personalización y diseño

- Usamos un **fondo** con diseño de carretera (`fondo.tscn`).
- Configuramos **límites** laterales para evitar que el personaje se salga.
- Usamos `CollisionShape2D` en el personaje y en los bordes.
- Los alumnos pueden usar el nodo `Sprite2D` para cambiar el diseño del personaje o rival.

---

## 🎯 Desafío para los alumnos

Cada alumno debe:

✅ Crear su **propio personaje jugable** (puede ser un elfo, robot, etc.).

✅ Diseñar su propio **fondo/escenario**.

✅ Colocar **un rival u obstáculo** contra el que perder.

✅ Configurar **límites** con nodos de colisión.

✅ Personalizar su estilo y gráficos como prefieran.

Este será su **primer mini-juego funcional en Godot** 🚀

---

## 🧠 Aprendizajes clave

- Cómo mover un personaje en 2D.
- Cómo detectar colisiones y reaccionar ante ellas.
- Cómo mostrar/ocultar nodos.
- Cómo organizar una escena con varios nodos hijos.

---

¡Nos vemos en la próxima clase para seguir avanzando en nuestro mundo de juegos! 🎮🔥
