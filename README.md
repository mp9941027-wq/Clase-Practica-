# Clase-Practica-

class Nodo<T> {
    T dato;
    Nodo<T> siguiente;

    Nodo(T dato) {
        this.dato = dato;
    }
}

public class ListaEnlazada<T> {
    Nodo<T> cabeza;

    // Agrega al final 
    void agregar(T dato) {
        Nodo<T> nuevo = new Nodo<>(dato);
        if (cabeza == null) {
            cabeza = nuevo;
        } else {
            Nodo<T> actual = cabeza;
            while (actual.siguiente != null) {
                actual = actual.siguiente;
            }
            actual.siguiente = nuevo;
        }
    }

    // Elimina elementos repetidos
    void eliminarRepetidos() {
        Nodo<T> actual = cabeza;
        while (actual != null) {
            Nodo<T> comparador = actual;
            while (comparador.siguiente != null) {
                if (comparador.siguiente.dato.equals(actual.dato)) {
                    comparador.siguiente = comparador.siguiente.siguiente;
                } else {
                    comparador = comparador.siguiente;
                }
            }
            actual = actual.siguiente;
        }
    }

    //  Rota una posición a la derecha
    void rotarDerecha() {
        if (cabeza == null || cabeza.siguiente == null) return;

        Nodo<T> penultimo = cabeza;
        while (penultimo.siguiente.siguiente != null) {
            penultimo = penultimo.siguiente;
        }

        Nodo<T> ultimo = penultimo.siguiente;
        penultimo.siguiente = null;
        ultimo.siguiente = cabeza;
        cabeza = ultimo;
    }

    //  Concatena otra lista al final
    void concatenar(ListaEnlazada<T> otra) {
        if (cabeza == null) {
            cabeza = otra.cabeza;
            return;
        }
        Nodo<T> actual = cabeza;
        while (actual.siguiente != null) {
            actual = actual.siguiente;
        }
        actual.siguiente = otra.cabeza;
    }

    // Muestra la lista
    void mostrar() {
        Nodo<T> actual = cabeza;
        while (actual != null) {
            System.out.print(actual.dato);
            if (actual.siguiente != null) System.out.print("-");
            actual = actual.siguiente;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        // Lista de Strings
        ListaEnlazada<String> lista1 = new ListaEnlazada<>();
        lista1.agregar("Ana"); lista1.agregar("Luis");
        lista1.agregar("Ana"); lista1.agregar("Maria");
        System.out.print("Original: "); lista1.mostrar();
        lista1.eliminarRepetidos();
        System.out.print("Sin repetidos: "); lista1.mostrar();

        // Lista de Integers
        ListaEnlazada<Integer> lista2 = new ListaEnlazada<>();
        lista2.agregar(1); lista2.agregar(2);
        lista2.agregar(3); lista2.agregar(4);
        System.out.print("Original: "); lista2.mostrar();
        lista2.rotarDerecha();
        System.out.print("Rotada: "); lista2.mostrar();

        // Concatena listas de Characters
        ListaEnlazada<Character> listaA = new ListaEnlazada<>();
        listaA.agregar('A'); listaA.agregar('B');
        listaA.agregar('C'); listaA.agregar('D');
        ListaEnlazada<Character> listaB = new ListaEnlazada<>();
        listaB.agregar('E'); listaB.agregar('F');
        listaB.agregar('G'); listaB.agregar('H');
        listaA.concatenar(listaB);
        System.out.print("Concatenada: "); listaA.mostrar();
    }
}
