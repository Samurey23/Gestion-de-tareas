# ===============================
# Sistema de Gestión de Tareas
# ===============================

def agregar_tarea(lista, tarea):
    """Inserta una tarea en la lista"""
    lista.append(tarea)

def eliminar_tarea(lista, tarea):
    """Elimina una tarea de la lista si existe"""
    if tarea in lista:
        lista.remove(tarea)

def buscar_tarea(lista, tarea):
    """Localiza una tarea dentro de la lista"""
    return tarea in lista

def push_pila(pila, tarea):
    """Agrega tarea al tope de la pila"""
    pila.append(tarea)

def pop_pila(pila):
    """Elimina la última tarea agregada (LIFO)"""
    if pila:
        return pila.pop()
    return None

def encolar(cola, tarea):
    """Agrega tarea al final de la cola"""
    cola.append(tarea)

def desencolar(cola):
    """Elimina la primera tarea de la cola (FIFO)"""
    if cola:
        return cola.pop(0)
    return None

class Nodo:
    def __init__(self, tarea):
        self.tarea = tarea
        self.izq = None
        self.der = None

def insertar_nodo(raiz, tarea):
    """Inserta un nodo en el árbol (ordenado alfabéticamente)"""
    if raiz is None:
        return Nodo(tarea)
    if tarea < raiz.tarea:
        raiz.izq = insertar_nodo(raiz.izq, tarea)
    else:
        raiz.der = insertar_nodo(raiz.der, tarea)
    return raiz

def inorden(raiz):
    """Recorrido inorden del árbol"""
    if raiz:
        inorden(raiz.izq)
        print(raiz.tarea)
        inorden(raiz.der)


# ===============================
# DEMOSTRACIÓN DEL SISTEMA
# ===============================
if __name__ == "__main__":
    tareas = []
    agregar_tarea(tareas, "Revisar reportes")
    agregar_tarea(tareas, "Enviar correo")
    eliminar_tarea(tareas, "Enviar correo")
    print("Lista de tareas:", tareas)

    pila = []
    push_pila(pila, "Tarea A")
    push_pila(pila, "Tarea B")
    print("Pila antes de sacar:", pila)
    print("Tarea sacada de la pila:", pop_pila(pila))
    print("Pila después de sacar:", pila)

    cola = []
    encolar(cola, "Tarea 1")
    encolar(cola, "Tarea 2")
    encolar(cola, "Tarea 3")
    print("Cola de tareas:", cola)
    print("Primera tarea en la cola:", cola[0])
    print("Última tarea en la cola:", cola[-1])
    desencolar(cola)
    print("Cola después de atender una tarea:", cola)

    raiz = None
    raiz = insertar_nodo(raiz, "Proyecto X")
    raiz = insertar_nodo(raiz, "Análisis")
    raiz = insertar_nodo(raiz, "Diseño")
    raiz = insertar_nodo(raiz, "Implementación")

    print("Árbol de tareas (inorden):")
    inorden(raiz)
