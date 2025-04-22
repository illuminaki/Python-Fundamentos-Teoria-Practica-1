# Teoría de Fundamentos de Python

Este archivo contiene explicaciones detalladas y extensas sobre los fundamentos de Python. Está dirigido a personas que están comenzando en la programación y desean comprender a fondo cómo funciona cada concepto.

---

## 1. Ingreso de datos por consola en Python

Python permite interactuar con el usuario solicitando datos mediante la función `input()`. Esta función siempre devuelve una **cadena de texto** (`str`). Por eso, si necesitas trabajar con números, deberás convertir la entrada con `int()` o `float()`.

### Solicitud y almacenamiento de datos
```python
nombre = input("¿Cuál es tu nombre? ")
edad = input("¿Cuántos años tienes? ")
```

La función `input()` muestra el mensaje entre paréntesis al usuario y espera a que este introduzca datos por teclado. Cuando el usuario presiona Enter, la función devuelve lo que se ha escrito como una cadena de texto y el programa continúa su ejecución.

### Conversión de tipo
```python
edad = int(edad)  # Convertimos el dato a entero
```

Esta conversión es necesaria porque `input()` siempre devuelve texto, incluso si el usuario ingresa números. Si intentas realizar operaciones matemáticas con un número en formato de texto, Python generará un error:

```python
edad = input("¿Cuántos años tienes? ")
edad_siguiente = edad + 1  # ¡ERROR! No se puede sumar un entero a una cadena
```

La forma correcta sería:
```python
edad = int(input("¿Cuántos años tienes? "))
edad_siguiente = edad + 1  # Ahora funciona correctamente
```

### Manejo de errores en la entrada de datos
Si el usuario ingresa algo que no puede convertirse al tipo esperado, Python lanzará una excepción. Por ejemplo:

```python
try:
    edad = int(input("¿Cuántos años tienes? "))
except ValueError:
    print("¡Error! Debes ingresar un número entero.")
```

### Impresión de resultados
```python
print("Hola", nombre, "tienes", edad, "años.")
```
También puedes usar **f-strings** (disponibles desde Python 3.6):
```python
print(f"Hola {nombre}, tienes {edad} años.")
```

Las f-strings son la forma más moderna y eficiente de formatear cadenas en Python. Permiten insertar variables y expresiones directamente dentro de las llaves `{}`.

#### Otras formas de formatear cadenas:

1. **Método format()**:
```python
print("Hola {}, tienes {} años.".format(nombre, edad))
```

2. **Operador %** (estilo antiguo):
```python
print("Hola %s, tienes %d años." % (nombre, edad))
```

---

## 2. Tipos de datos en Python

Los tipos de datos definen la naturaleza del valor que se guarda en una variable. Python es un lenguaje de **tipado dinámico**, es decir, no necesitas declarar el tipo de dato, se infiere automáticamente.

### Principales tipos de datos

- **int**: Números enteros sin parte decimal.
  ```python
  edad = 25
  población = 7_800_000_000  # Los guiones bajos mejoran la legibilidad
  ```

- **float**: Números con decimales.
  ```python
  precio = 19.99
  pi = 3.14159265359
  notación_científica = 1.23e-4  # Equivale a 0.000123
  ```

- **str**: Cadenas de texto. Pueden definirse con comillas simples o dobles.
  ```python
  nombre = "Sebastián"
  apellido = 'González'
  frase = """Este texto
  puede ocupar
  varias líneas"""  # Triple comilla para texto multilínea
  ```

- **bool**: Booleanos (`True` o `False`). Representan valores de verdad.
  ```python
  es_mayor = True
  tiene_permiso = False
  ```

### Tipos de datos adicionales

- **list**: Colecciones ordenadas y modificables de elementos.
  ```python
  colores = ["rojo", "verde", "azul"]
  números = [1, 2, 3, 4, 5]
  mixta = [1, "dos", True, 3.14]  # Pueden contener diferentes tipos
  ```

- **tuple**: Colecciones ordenadas e inmutables.
  ```python
  coordenadas = (10, 20)
  rgb = (255, 0, 0)  # Rojo en RGB
  ```

- **dict**: Diccionarios que almacenan pares clave-valor.
  ```python
  persona = {
      "nombre": "Ana",
      "edad": 28,
      "profesión": "Ingeniera"
  }
  ```

- **set**: Conjuntos de elementos únicos y desordenados.
  ```python
  frutas = {"manzana", "naranja", "plátano"}
  ```

- **None**: Representa la ausencia de valor.
  ```python
  resultado = None  # Útil para inicializar variables
  ```

### Verificación de tipos
Para conocer el tipo de una variable, puedes usar la función `type()`:

```python
x = 10
print(type(x))  # <class 'int'>

y = "Hola"
print(type(y))  # <class 'str'>
```

### Conversión entre tipos
```python
int("5")      # Convierte una cadena a entero: 5
float("3.14") # Convierte una cadena a flotante: 3.14
str(10)       # Convierte un número a texto: "10"
bool(1)       # True si el valor es distinto de 0 o vacío
list("abc")   # Convierte a lista: ['a', 'b', 'c']
tuple([1,2,3])# Convierte a tupla: (1, 2, 3)
```

#### Valores que se evalúan como False en contextos booleanos:
- `0` (cero)
- `""` (cadena vacía)
- `[]` (lista vacía)
- `()` (tupla vacía)
- `{}` (diccionario o conjunto vacío)
- `None`

Todo lo demás se evalúa como `True`.

---

## 3. Operadores en Python

### Aritméticos
Permiten realizar operaciones matemáticas básicas:
```python
+   # Suma
-   # Resta
*   # Multiplicación
/   # División (siempre devuelve un float)
//  # División entera (sin decimales, trunca hacia abajo)
%   # Módulo (residuo de la división)
**  # Potencia
```

Ejemplos:
```python
suma = 10 + 5        # 15
resta = 10 - 5       # 5
multiplicación = 10 * 5  # 50
división = 10 / 3    # 3.3333333333333335 (float)
división_entera = 10 // 3  # 3 (int)
módulo = 10 % 3      # 1 (el residuo de 10/3)
potencia = 2 ** 3    # 8 (2 elevado a la 3)
```

#### Precedencia de operadores
Python sigue las reglas matemáticas estándar de precedencia:
1. Paréntesis `()`
2. Exponentes `**`
3. Multiplicación, división, módulo `*, /, //, %`
4. Suma y resta `+, -`

```python
resultado = 2 + 3 * 4    # 14 (no 20, porque * tiene mayor precedencia)
resultado = (2 + 3) * 4  # 20 (los paréntesis cambian la precedencia)
```

### Operadores de asignación
Se utilizan para guardar valores en variables o modificar su valor:
```python
x = 10        # Asignación básica
x += 5        # Equivale a x = x + 5
x -= 3        # Equivale a x = x - 3
x *= 2        # Equivale a x = x * 2
x /= 4        # Equivale a x = x / 4
x //= 2       # Equivale a x = x // 2
x %= 3        # Equivale a x = x % 3
x **= 2       # Equivale a x = x ** 2
```

### Operadores de cadenas
```python
# Concatenación
nombre = "Juan"
apellido = "Pérez"
nombre_completo = nombre + " " + apellido  # "Juan Pérez"

# Repetición
línea = "-" * 10  # "----------"
```

---

## 4. Operadores relacionales

Se usan para comparar valores. Devuelven un **booleano** (`True` o `False`).
```python
==   # Igual a
!=   # Distinto de
>    # Mayor que
<    # Menor que
>=   # Mayor o igual que
<=   # Menor o igual que
```

Ejemplos:
```python
edad = 18
print(edad == 18)  # True (edad es igual a 18)
print(edad != 20)  # True (edad no es igual a 20)
print(edad > 15)   # True (edad es mayor que 15)
print(edad < 21)   # True (edad es menor que 21)
print(edad >= 18)  # True (edad es mayor o igual a 18)
print(edad <= 17)  # False (edad no es menor o igual a 17)
```

### Comparación de cadenas
Las cadenas se comparan alfabéticamente (según su valor ASCII):
```python
print("a" < "b")    # True
print("abc" < "abd")  # True
print("Z" < "a")    # True (mayúsculas vienen antes que minúsculas en ASCII)
```

### Comparación de objetos
Para tipos complejos como listas:
```python
print([1, 2] == [1, 2])  # True (mismo contenido)
print([1, 2] is [1, 2])  # False (diferentes objetos en memoria)
```

El operador `is` compara identidad (si son el mismo objeto), mientras que `==` compara igualdad (si tienen el mismo valor).

---

## 5. Operadores lógicos

Permiten construir condiciones más complejas:
```python
and  # Devuelve True si ambas condiciones son verdaderas
or   # Devuelve True si al menos una es verdadera
not  # Niega el valor de verdad
```

Ejemplos:
```python
edad = 20
es_mayor = edad >= 18
es_menor_que_30 = edad < 30

if es_mayor and es_menor_que_30:
    print("Tienes entre 18 y 29 años.")

# Uso directo sin variables intermedias
if edad >= 18 and edad < 30:
    print("Tienes entre 18 y 29 años.")

# Uso de OR
tiene_permiso = False
es_administrador = True
if tiene_permiso or es_administrador:
    print("Acceso concedido")

# Uso de NOT
if not tiene_permiso:
    print("No tienes permiso")
```

### Cortocircuito en operadores lógicos
Python evalúa las expresiones de izquierda a derecha y se detiene cuando ya conoce el resultado:

- `and`: Si el primer operando es `False`, el resultado será `False` sin evaluar el segundo operando.
- `or`: Si el primer operando es `True`, el resultado será `True` sin evaluar el segundo operando.

Esto es útil para evitar errores:
```python
# Evita error de división por cero
if divisor != 0 and número / divisor > 1:
    print("El resultado es mayor que 1")
```

### Operadores de pertenencia
```python
in    # Verifica si un valor está en una secuencia
not in # Verifica si un valor no está en una secuencia
```

Ejemplos:
```python
frutas = ["manzana", "naranja", "plátano"]
print("manzana" in frutas)  # True
print("pera" not in frutas)  # True

texto = "Python es genial"
print("Python" in texto)  # True
print("Java" in texto)    # False
```

---

## 6. Estructuras de control

### Condicionales (if-elif-else)
Permiten ejecutar diferentes bloques de código según se cumplan ciertas condiciones:

```python
edad = 18

if edad < 18:
    print("Eres menor de edad")
elif edad == 18:
    print("Acabas de cumplir la mayoría de edad")
else:
    print("Eres mayor de edad")
```

#### Operador ternario (expresión condicional en una línea)
```python
mensaje = "Mayor de edad" if edad >= 18 else "Menor de edad"
```

### Recursos adicionales para profundizar

- [Documentación oficial de Python](https://docs.python.org/es/3/)
- [Real Python](https://realpython.com/) - Tutoriales y artículos en inglés
- [Python para todos](https://www.py4e.com/) - Curso gratuito en varios idiomas
- [Automate the Boring Stuff with Python](https://automatetheboringstuff.com/) - Libro gratuito en inglés
