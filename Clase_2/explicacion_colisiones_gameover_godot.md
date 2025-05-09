# 🧠 Explicación detallada del código de colisiones y Game Over en Godot

## 🚗 Sección de Detección de Colisiones

```gdscript
if get_slide_collision_count() > 0:
```

### 🔍 ¿Qué es `get_slide_collision_count()`?
- Método de `CharacterBody2D`.
- Devuelve la cantidad de colisiones ocurridas tras ejecutar `move_and_slide()`.
- Si colisionaste con dos objetos, devuelve 2.

---

```gdscript
for i in range(get_slide_collision_count()):
```

- Bucle que recorre todas las colisiones registradas.

---

```gdscript
var colision = get_slide_collision(i)
```

### 🔍 ¿Qué es `get_slide_collision(i)`?
- También de `CharacterBody2D`.
- Devuelve un objeto `KinematicCollision2D`.
- Contiene detalles como: objeto chocado, punto de impacto, normal, etc.

---

```gdscript
if colision.get_collider().name == "rival":
```

### 🔍 ¿Qué es `get_collider()`?
- Devuelve el **nodo con el que colisionaste**.
- `.name` accede al nombre de ese nodo.
- Aquí se comprueba si ese nodo se llama `"rival"`.

---

```gdscript
mostrar_game_over()
```

- Si hubo colisión con "rival", se ejecuta esta función para mostrar el cartel de Game Over.

---

## 🟥 Función `mostrar_game_over()`

```gdscript
var game_over = get_tree().get_current_scene().get_node("GameOverLabel")
```

### 🔍 ¿Qué hacen estos métodos?
- `get_tree()`: accede al árbol de nodos de la escena activa.
- `get_current_scene()`: devuelve la escena en ejecución.
- `get_node("GameOverLabel")`: busca dentro de esa escena un nodo con ese nombre.

---

```gdscript
game_over.visible = true
```

- Muestra visualmente el nodo `GameOverLabel` (probablemente estaba oculto).

---

```gdscript
set_process(false)
```

### 🔍 ¿Qué hace `set_process(false)`?
- Detiene el método `_process(delta)` del nodo.
- En tu caso, es más correcto usar:

```gdscript
set_physics_process(false)
```

- Esto detiene `_physics_process(delta)`, que es el que estás usando.

---

## ✳️ Tabla resumen de métodos usados

| Método                         | Pertenece a             | Descripción                                      |
|-------------------------------|--------------------------|--------------------------------------------------|
| `get_slide_collision_count()` | `CharacterBody2D`        | Número de colisiones                            |
| `get_slide_collision(i)`      | `CharacterBody2D`        | Devuelve colisión específica                    |
| `get_collider()`              | `KinematicCollision2D`   | Nodo contra el que colisionaste                |
| `get_tree()`                  | `Node`                   | Accede al árbol de nodos                        |
| `get_current_scene()`         | `SceneTree`              | Devuelve la escena actual                       |
| `get_node("...")`             | `Node`                   | Busca un nodo por nombre                        |
| `set_process(false)`          | `Node`                   | Detiene `_process(delta)`                       |
| `set_physics_process(false)`  | `Node`                   | Detiene `_physics_process(delta)`              |

---

## ✅ Conclusión

Tu código:
1. Detecta colisiones.
2. Verifica si son contra un "rival".
3. Si lo son, muestra el cartel de Game Over.
4. Detiene la ejecución del personaje.

