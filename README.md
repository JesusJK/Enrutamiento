# Algoritmo Floyd-Warshall

## 📋 Descripción

El algoritmo **Floyd-Warshall** es un algoritmo de programación dinámica que encuentra las distancias más cortas entre **todos los pares de vértices** en un grafo ponderado dirigido. A diferencia de algoritmos como Dijkstra que encuentran el camino más corto desde un vértice fuente, Floyd-Warshall resuelve el problema para todos los pares de vértices de una sola vez.

## 🎯 Características

- **Complejidad temporal**: O(V³) donde V es el número de vértices
- **Complejidad espacial**: O(V²)
- **Maneja pesos negativos**: Sí (pero no ciclos negativos)
- **Tipo de grafo**: Dirigido y ponderado
- **Paradigma**: Programación dinámica

## 🧮 Funcionamiento del Algoritmo

El algoritmo utiliza una matriz de distancias que se actualiza iterativamente:

```
Para cada vértice k de 0 a n-1:
    Para cada vértice i de 0 a n-1:
        Para cada vértice j de 0 a n-1:
            Si distancia[i][k] + distancia[k][j] < distancia[i][j]:
                distancia[i][j] = distancia[i][k] + distancia[k][j]
```

### Explicación paso a paso:

1. **Inicialización**: Se crea una matriz con las distancias directas entre vértices
2. **Iteración**: Para cada vértice k, se verifica si pasar por k mejora la distancia entre cualquier par de vértices i,j
3. **Actualización**: Si encontrar un camino más corto, se actualiza la matriz
4. **Resultado**: Al final, la matriz contiene las distancias mínimas entre todos los pares

## 📁 Archivos del Proyecto

- `floyd_warshall.py` - Implementación en Python
- `floyd_warshall.cpp` - Implementación en C++
- `ejemplos_grafos.py` - Ejemplos diversos para probar el algoritmo
- `README.md` - Este archivo de documentación

## 🚀 Uso

### Python

```bash
# Ejecutar implementación básica
python floyd_warshall.py

# Ejecutar ejemplos diversos
python ejemplos_grafos.py
```

### C++

```bash
# Compilar
g++ -o floyd_warshall floyd_warshall.cpp

# Ejecutar
./floyd_warshall
```

## 💡 Ejemplos de Uso

### Ejemplo 1: Grafo Simple

```
Grafo Original:
     0     1     2
 0:  0     4     ∞
 1:  ∞     0     2
 2:  1     ∞     0

Distancias Mínimas:
     0     1     2
 0:  0     4     6
 1:  3     0     2
 2:  1     5     0
```

### Ejemplo 2: Con Pesos Negativos

```
Grafo Original:
     0     1     2     3
 0:  0     1     ∞     4
 1:  ∞     0    -3     2
 2:  ∞     ∞     0     3
 3:  ∞    -1     ∞     0

Distancias Mínimas:
     0     1     2     3
 0:  0     1    -2     1
 1:  ∞     0    -3     0
 2:  ∞     ∞     0     3
 3:  ∞    -1    -4    0
```

## ⚠️ Limitaciones

1. **Ciclos negativos**: El algoritmo no funciona correctamente si el grafo contiene ciclos negativos
2. **Memoria**: Requiere O(V²) espacio, puede ser problemático para grafos muy grandes
3. **Tiempo**: Con complejidad O(V³), puede ser lento para grafos con muchos vértices

## 🔍 Aplicaciones

- **Redes de transporte**: Encontrar rutas más cortas entre todas las ciudades
- **Redes de comunicación**: Optimizar rutas de datos
- **Juegos**: Pathfinding en mapas pequeños
- **Análisis de grafos**: Detectar componentes fuertemente conectados
- **Economía**: Análisis de arbitraje en mercados financieros

## 📊 Comparación con Otros Algoritmos

| Algoritmo | Complejidad | Desde un vértice | Todos los pares | Pesos negativos |
|-----------|-------------|------------------|-----------------|-----------------|
| Dijkstra | O(V² + E) | ✅ | ❌ | ❌ |
| Bellman-Ford | O(VE) | ✅ | ❌ | ✅ |
| Floyd-Warshall | O(V³) | ❌ | ✅ | ✅ |

## 🧪 Casos de Prueba

El proyecto incluye varios casos de prueba:

1. **Grafo simple** (3 vértices)
2. **Grafo completo** (todos conectados)
3. **Grafo desconectado** (componentes separados)
4. **Grafo con pesos negativos**
5. **Análisis de complejidad** (diferentes tamaños)

## 🎓 Conceptos Teóricos

### Programación Dinámica
Floyd-Warshall es un ejemplo clásico de programación dinámica donde:
- **Subproblemas**: Distancia mínima entre i y j usando vértices {0,1,...,k}
- **Recurrencia**: `dp[i][j][k] = min(dp[i][j][k-1], dp[i][k][k-1] + dp[k][j][k-1])`
- **Optimización de espacio**: Solo necesitamos la iteración actual

### Invariante del Bucle
Después de la k-ésima iteración, `distancia[i][j]` contiene la distancia más corta del vértice i al vértice j usando solo los vértices {0, 1, 2, ..., k-1} como vértices intermedios.

## 📚 Referencias

- Cormen, T. H., Leiserson, C. E., Rivest, R. L., & Stein, C. (2009). Introduction to Algorithms (3rd ed.)
- Floyd, R. W. (1962). Algorithm 97: Shortest Path. Communications of the ACM
- Warshall, S. (1962). A theorem on Boolean matrices. Journal of the ACM

---

**Nota**: Este proyecto fue desarrollado para la materia de Análisis de Algoritmos. ¡Esperamos que te ayude a entender este algoritmo fundamental! 🚀
