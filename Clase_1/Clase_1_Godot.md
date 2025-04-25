
# 🎮 Clase 1: Primeros Pasos con Godot - "Aventura del Enano y el Barril"

---

## 🎯 Objetivo de la clase

- Conocer la interfaz de Godot Engine.
- Crear un escenario básico con fondo, suelo, personaje y objeto.
- Controlar el movimiento del personaje con el teclado.
- Organizar la escena de forma ordenada.

---

## 🧰 Archivos utilizados

- `main.tscn`: Escena principal del juego.
- `personaje.tscn` y `personaje.gd`: Personaje jugable.
- `Barril.tscn`: Objeto decorativo/interactivo.
- `static_body_2d.tscn`: Suelo del escenario.
- `fondo.png`: Imagen de fondo.
- `barril.png`: Imagen del barril.

---

## 🧭 Parte 1: Exploramos Godot

1. Abrimos el proyecto en **Godot Engine 4.x**.
2. Vemos los paneles:
   - Escena
   - Inspector
   - Vista 2D
   - Consola
3. Explicamos qué es un nodo y cómo se estructura una escena.

---

## 🛠️ Parte 2: Creamos el escenario

1. Abrimos la escena `main.tscn`.
2. Agregamos un Sprite2D y cargamos la imagen de fondo.
3. Agregamos el `static_body_2d.tscn` como suelo.
4. Posicionamos ambos para que formen un paisaje continuo.

---

## 🧍 Parte 3: Agregamos el personaje

1. Instanciamos `personaje.tscn` como hijo de `main.tscn`.
2. Revisamos su script `personaje.gd`:

```gdscript
extends CharacterBody2D

@export var velocidad: float = 200.0

func _physics_process(delta: float) -> void:
    var direccion = Vector2.ZERO
    if Input.is_action_pressed("ui_right"):
        direccion.x += 1
    if Input.is_action_pressed("ui_left"):
        direccion.x -= 1
    if Input.is_action_pressed("ui_down"):
        direccion.y += 1
    if Input.is_action_pressed("ui_up"):
        direccion.y -= 1
    direccion = direccion.normalized()
    velocity = direccion * velocidad
    move_and_slide()
```

3. Probamos el movimiento con `F6`.

---

## 🪵 Parte 4: Colocamos barriles

1. Instanciamos `Barril.tscn`.
2. Posicionamos uno o varios en la escena.
3. Explicamos cómo duplicarlos (`Ctrl+D`) y moverlos con el mouse.

---

## 📷 Resultado esperado

![Resultado](1206b077-04e2-48a1-a797-939a79578616.png)

---

## 🧠 Actividad para estudiantes

### Desafío 1
Mover el personaje hasta tocar todos los barriles sin atravesarlos.

### Desafío 2 (opcional)
Agregar una colisión al barril para que no se pueda atravesar.

---

## 📚 Tarea

- Practicar mover el personaje y duplicar nodos.
- Pensar ideas para obstáculos o enemigos simples.

---

## 🧑‍🏫 Para el profe

Este material está pensado para una clase de 90 minutos. Se recomienda usar Godot 4.x y proyectar la vista del profesor para guiar a los estudiantes paso a paso.
