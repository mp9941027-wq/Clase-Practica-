

Implementación de una lista simplemente enlazada genérica (`<T>`) con tres
operaciones sobre nodos:

1. **Eliminar elementos repetidos** — recorre la lista y elimina los nodos
   duplicados, dejando solo la primera aparición de cada dato.
2. **Rotar una posición a la derecha** — el último nodo pasa a ser el primero.
   Ejemplo: `A-B-C-D` → `D-A-B-C`
3. **Concatenar dos listas** — enlaza el último nodo de la primera lista con
   la cabeza de la segunda.
   Ejemplo: `A-B-C-D` + `E-F-G-H` → `A-B-C-D-E-F-G-H`

## Estructura

| Clase | Descripción |
|-------|-------------|
| `Nodo<T>` | Nodo genérico con dato y referencia al siguiente nodo |
| `ListaEnlazada<T>` | Lista con las operaciones: agregar, eliminar repetidos, rotar y concatenar |
