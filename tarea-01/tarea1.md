

---

## Nivel 1 — Conversión de bases (fundamentos)

### 1.1 Convierte los siguientes números decimales a binario: 45, 128, 255, 1000

*   **45:**
    Dividimos sucesivamente por 2 o sumamos potencias de 2:
    $45 = 32 + 8 + 4 + 1 = 2^5 + 2^3 + 2^2 + 2^0$
    *   **Resultado:** `101101` (o en 8 bits: `00101101`)

*   **128:**
    Es una potencia exacta de 2:
    $128 = 2^7$
    *   **Resultado:** `10000000`

*   **255:**
    $255 = 2^8 - 1$ (el valor máximo con 8 bits sin signo):
    *   **Resultado:** `11111111`

*   **1000:**
    Descomponiendo en potencias de 2:
    $1000 = 512 + 256 + 128 + 64 + 32 + 8 = 2^9 + 2^8 + 2^7 + 2^6 + 2^5 + 2^3$
    *   **Resultado:** `1111101000`

---

### 1.2 Convierte los siguientes números binarios a decimal: 1011, 10110110, 11111111, 100000000

*   **1011:**
    $1 \cdot 2^3 + 0 \cdot 2^2 + 1 \cdot 2^1 + 1 \cdot 2^0 = 8 + 0 + 2 + 1 = 11$
    *   **Resultado:** `11`

*   **10110110:**
    $1 \cdot 2^7 + 0 \cdot 2^6 + 1 \cdot 2^5 + 1 \cdot 2^4 + 0 \cdot 2^3 + 1 \cdot 2^2 + 1 \cdot 2^1 + 0 \cdot 2^0$
    $128 + 32 + 16 + 4 + 2 = 182$
    *   **Resultado:** `182`

*   **11111111:**
    $2^8 - 1 = 255$
    *   **Resultado:** `255`

*   **100000000:**
    Es un $1$ seguido de $8$ ceros, lo cual equivale a $2^8 = 256$.
    *   **Resultado:** `256`

---

### 1.3 Convierte a hexadecimal los siguientes números binarios: 10101100, 111100001111, 1010101010101010

*Para convertir de binario a hexadecimal agrupamos de 4 en 4 bits de derecha a izquierda:*

*   **1010 1100:**
    *   $1010_2 = A_{16}$
    *   $1100_2 = C_{16}$
    *   **Resultado:** `0xAC`

*   **1111 0000 1111:**
    *   $1111_2 = F_{16}$
    *   $0000_2 = 0_{16}$
    *   $1111_2 = F_{16}$
    *   **Resultado:** `0xF0F`

*   **1010 1010 1010 1010:**
    *   Cada grupo de `1010` es $A_{16}$
    *   **Resultado:** `0xAAAA`

---

### 1.4 Convierte de octal a decimal: 17, 254, 777

*   **17 (octal):**
    $1 \cdot 8^1 + 7 \cdot 8^0 = 8 + 7 = 15$
    *   **Resultado:** `15`

*   **254 (octal):**
    $2 \cdot 8^2 + 5 \cdot 8^1 + 4 \cdot 8^0 = 2 \cdot 64 + 5 \cdot 8 + 4 = 128 + 40 + 4 = 172$
    *   **Resultado:** `172`

*   **777 (octal):**
    $7 \cdot 8^2 + 7 \cdot 8^1 + 7 \cdot 8^0 = 7 \cdot 64 + 7 \cdot 8 + 7 = 448 + 56 + 7 = 511$
    *(Nota alternativa: $777_8 = 1000_8 - 1 = 8^3 - 1 = 512 - 1 = 511$)*
    *   **Resultado:** `511`

---

## Nivel 2 — Aritmética binaria básica

### 2.1 Realiza las siguientes sumas binarias (muestra el acarreo)

*   **Suma 1: 1011 + 0110**
    ```
      Acarreo:  1 1 1
        Sumando 1:    1 0 1 1  (11 en decimal)
      + Sumando 2:    0 1 1 0  (6 en decimal)
      -----------------------
        Resultado:  1 0 0 0 1  (17 en decimal)
    ```

*   **Suma 2: 11101 + 01011**
    ```
      Acarreo:  1 1 1 1 1
        Sumando 1:    1 1 1 0 1  (29 en decimal)
      + Sumando 2:    0 1 0 1 1  (11 en decimal)
      -------------------------
        Resultado:  1 0 1 0 0 0  (40 en decimal)
    ```

---

### 2.2 Realiza las siguientes restas binarias usando préstamo (borrow)

*   **Resta 1: 1100 - 0101**
    ```
      Préstamo:     1 1
        Minuendo:     1 1 0 0  (12 en decimal)
      - Sustraendo:   0 1 0 1  (5 en decimal)
      -----------------------
        Resultado:    0 1 1 1  (7 en decimal)
    ```
    *Explicación:* El Bit 0 ($0-1$) pide prestado al Bit 1, que como es $0$, pide al Bit 2 ($1$). El Bit 2 queda en $0$, el Bit 1 pasa a ser $2$ y le presta $1$ al Bit 0. El Bit 0 calcula $2-1=1$. Luego el Bit 1 calcula $1-0=1$. En el Bit 2 ($0-1$) pide prestado al Bit 3, quedando $2-1=1$.

*   **Resta 2: 10000 - 00111**
    ```
      Préstamo:   1 1 1 1
        Minuendo:     1 0 0 0 0  (16 en decimal)
      - Sustraendo:   0 0 1 1 1  (7 en decimal)
      -------------------------
        Resultado:    0 1 0 0 1  (9 en decimal)
    ```
    *Explicación:* El bit más significativo (Bit 4) propaga el préstamo hacia la derecha. Bit 4 queda en $0$, bits 3, 2 y 1 quedan en $1$ temporalmente, y el Bit 0 queda con valor $2$. Las restas son: $2-1=1$, $1-1=0$, $1-1=0$, $1-0=1$, $0-0=0$.

---

### 2.3 Multiplica en binario: 1011 × 0101

Multiplicación tradicional paso a paso desplazando los resultados parciales:
```
        1 0 1 1    (11 en decimal)
      × 0 1 0 1    (5 en decimal)
      ---------
        1 0 1 1    (1011 × 1)
      0 0 0 0      (1011 × 0, desplazado)
    1 0 1 1        (1011 × 1, desplazado)
  0 0 0 0          (1011 × 0, desplazado)
  -------------
  1 1 0 1 1 1      (55 en decimal)
```
*Verificación:* $110111_2 = 32 + 16 + 4 + 2 + 1 = 55_{10}$.

---

## Nivel 3 — Complemento a dos

### 3.1 Representa los siguientes números decimales en complemento a dos usando 8 bits: -45, -1, -128, 27

*El rango representable para 8 bits con signo es de $[-128, 127]$.*

*   **-45:**
    1. Binario absoluto ($45$): `00101101`
    2. Invertir bits (complemento a 1): `11010010`
    3. Sumar 1: `11010011`
    *   **Resultado:** `11010011`

*   **-1:**
    1. Binario absoluto ($1$): `00000001`
    2. Invertir bits: `11111110`
    3. Sumar 1: `11111111`
    *   **Resultado:** `11111111`

*   **-128:**
    Es el valor límite inferior en 8 bits con signo. Su representación es directa por hardware:
    *   **Resultado:** `10000000`

*   **27:**
    Por ser positivo, su representación en complemento a dos es idéntica a su representación binaria directa (rellenando con ceros a la izquierda hasta los 8 bits):
    $27 = 16 + 8 + 2 + 1 = 00011011_2$
    *   **Resultado:** `00011011`

---

### 3.2 Dado el número en complemento a dos de 8 bits 11010110, indica su valor decimal.

1. Identificamos que el Bit de Signo (bit más a la izquierda) es $1$, por ende el número es **negativo**.
2. Para hallar su magnitud:
   *   Invertimos los bits: `00101001`
   *   Sumamos 1: `00101010`
   *   Convertimos el resultado absoluto a decimal: $32 + 8 + 2 = 42$.
3. Aplicamos el signo negativo:
*   **Resultado:** `-42`

---

### 3.3 Realiza la resta 45 - 60 usando complemento a dos con registros de 8 bits, y verifica el resultado.

La resta se plantea como una suma: $45 + (-60)$.
1. **$45$ en binario de 8 bits:** `00101101`
2. **$-60$ en complemento a dos:**
   *   $60$ absoluto: `00111100`
   *   Invertir bits: `11000011`
   *   Sumar 1: `11000100`
3. **Sumamos los valores:**
   ```
       00101101  (45)
     + 11000100  (-60)
     ----------
       11110001
   ```
4. **Verificación del resultado `11110001`:**
   *   Invertir bits: `00001110`
   *   Sumar 1: `00001111` $\rightarrow 8 + 4 + 2 + 1 = 15$.
   *   El valor decimal es $-15$.
*   **Resultado final en binario:** `11110001` (que equivale a $-15$ decimal).

---

## Nivel 4 — Desbordamiento (overflow) y banderas

### 4.1 Determina si ocurre overflow al sumar, en complemento a dos de 8 bits:

*   **Suma A: 01111111 + 00000001**
    *   Decimal: $127$ (positivo) + $1$ (positivo).
    *   Operación binaria:
        ```
            01111111
          + 00000001
          ----------
            10000000  (que representa -128)
        ```
    *   **¿Ocurre overflow?: SÍ.**
    *   *Explicación:* Sumamos dos números positivos y el resultado tiene el bit de signo en 1 (negativo). El resultado matemático real ($128$) excede el límite máximo de un entero con signo de 8 bits ($127$). El acarreo entrante al bit de signo ($C_{in} = 1$) difiere del acarreo saliente ($C_{out} = 0$).

*   **Suma B: 10000000 + 11111111**
    *   Decimal: $-128$ (negativo) + $-1$ (negativo).
    *   Operación binaria:
        ```
            10000000
          + 11111111
          ----------
          1 01111111  --> descartando el bit de acarreo de 9 bits queda: 01111111 (+127)
        ```
    *   **¿Ocurre overflow?: SÍ.**
    *   *Explicación:* Sumamos dos números negativos y el resultado tiene el bit de signo en 0 (positivo). El resultado real ($-129$) cae por debajo del límite mínimo representable de 8 bits con signo ($-128$). El acarreo entrante es $C_{in} = 0$ y el saliente es $C_{out} = 1$.

---

### 4.2 Explica, con tus propias palabras, la diferencia entre carry (acarreo) y overflow en una suma con signo, y da un ejemplo de cada caso usando registros de 4 bits.

*   **Carry (Acarreo):** Se produce cuando la suma aritmética de los bits más significativos genera un bit adicional ("el carry de salida") que no cabe en el registro. Se utiliza en operaciones **sin signo** para indicar que el resultado se desbordó del tamaño asignado.
*   **Overflow (Desbordamiento):** Se produce cuando la suma de dos números con signo en representación de complemento a dos genera un resultado matemáticamente inválido porque se sale del rango de valores representables (el resultado tiene un signo incoherente con los operandos).

#### Ejemplos en registros de 4 bits (Rango con signo: $[-8, +7]$, Rango sin signo: $[0, 15]$)

1.  **Ocurre Carry pero NO Overflow:**
    *   Operación: $-3 + (-2) = -5$
    *   Binario: `1101` + `1110`
    *   Operación:
        ```
            1101  (-3)
          + 1110  (-2)
          ------
          1 1011  --> Registro queda en 1011 (-5)
        ```
    *   *Análisis:* Hay acarreo de salida ($C_{out} = 1$, hay **Carry**). Pero el resultado `1011` representa $-5$, que está en el rango $[-8, 7]$ y mantiene el signo negativo (no hay **Overflow**).

2.  **Ocurre Overflow pero NO Carry:**
    *   Operación: $5 + 4 = 9$
    *   Binario: `0101` + `0100`
    *   Operación:
        ```
            0101  (5)
          + 0100  (4)
          ------
            1001  --> Registro queda en 1001 (-7)
        ```
    *   *Análisis:* No hay acarreo de salida ($C_{out} = 0$, no hay **Carry**). Sin embargo, sumamos dos positivos y obtuvimos uno negativo (`1001` es $-7$ en complemento a dos), lo cual es erróneo porque el resultado correcto $9$ excede el rango máximo de $7$ (ocurrió **Overflow**).

---

### 4.3 (práctico en Ubuntu) Escribe un programa en C que sume dos enteros int8_t propensos a overflow (por ejemplo 120 + 20), compílalo con gcc, ejecútalo, y explica por qué el resultado impreso no es el esperado matemáticamente. Adjunta el comando de compilación y la salida.

#### Código C (`overflow_test.c`)
```c
#include <stdio.h>
#include <stdint.h>

int main() {
    int8_t a = 120;
    int8_t b = 20;
    int8_t resultado = a + b;

    printf("Operación: %d + %d\n", a, b);
    printf("Resultado en int8_t: %d\n", resultado);

    return 0;
}
```

#### Comandos de Compilación y Ejecución en Ubuntu
```bash
gcc -o overflow_test overflow_test.c
./overflow_test
```

#### Salida del Programa
```
Operación: 120 + 20
Resultado en int8_t: -116
```

#### Explicación
El tipo `int8_t` almacena enteros con signo de 8 bits usando complemento a dos, con un rango de $[-128, 127]$. 
Matemáticamente, $120 + 20 = 140$. Dado que $140$ es mayor que $127$, ocurre un desbordamiento.
Al sumarse en binario:
*   $120_{10} = 01111000_2$
*   $20_{10} = 00010100_2$
*   Suma binaria: `01111000` + `00010100` = `10001100`.
El patrón `10001100` tiene el bit más significativo en $1$, lo que representa un número negativo. Calculando su complemento a dos: invertir bits (`01110011`) + $1$ = `01110100` ($116_{10}$). Por lo tanto, el sistema interpreta este bit pattern como el número `-116`.

---

## Nivel 5 — Punto flotante (IEEE 754)

### 5.1 Representa el número decimal 10.25 en formato IEEE 754 de precisión simple (32 bits), mostrando signo, exponente y mantisa por separado.

1.  **Signo (1 bit):** El número es positivo, por lo tanto, $S = 0$.
2.  **Conversión a binario:**
    *   Parte entera: $10_{10} = 1010_2$
    *   Parte fraccionaria: $0.25_{10} = 1/4 = 0.01_2$
    *   Número completo: $10.25_{10} = 1010.01_2$
3.  **Normalización (notación científica binaria):**
    Desplazamos la coma 3 posiciones hacia la izquierda:
    $1010.01_2 = 1.01001_2 \times 2^3$
    El exponente real es $e = 3$.
4.  **Exponente Sesgado (8 bits):**
    Para precisión simple, sumamos el sesgo de $127$:
    $E = e + 127 = 3 + 127 = 130_{10}$.
    En binario de 8 bits: $130 = 128 + 2 = 10000010_2$.
5.  **Mantisa / Significando (23 bits):**
    Tomamos la parte fraccionaria del número normalizado (`01001`) y completamos con ceros hasta los 23 bits:
    $M = 01001000000000000000000_2$

#### Representación Final IEEE 754 (32 bits):
```
Signo (1b) | Exponente (8b) | Mantisa (23b)
-----------------------------------------------------------
    0      |    10000010    | 01001000000000000000000
```
*   **En Hexadecimal:** `0x41240000`

---

### 5.2 Dado el patrón de bits IEEE 754 de 32 bits `1 10000010 01100000000000000000000`, calcula su valor decimal.

1.  **Signo (S):** Bit 31 es $1 \rightarrow$ El número es **negativo**.
2.  **Exponente Sesgado (E):** `10000010`
    *   $10000010_2 = 128 + 2 = 130_{10}$.
    *   Exponente real: $e = E - 127 = 130 - 127 = 3$.
3.  **Mantisa (M):** `01100000000000000000000`
    *   Significando normalizado con bit implícito: $1.011_2$.
4.  **Cálculo del Valor:**
    $\text{Valor} = -1 \cdot (1.011_2) \cdot 2^3$
    Desplazando la coma 3 posiciones hacia la derecha debido al exponente $2^3$:
    $\text{Valor} = - (1011_2)$
    $1011_2 = 8 + 2 + 1 = 11_{10}$
*   **Valor Decimal:** `-11.0`

---

### 5.3 Explica qué es la pérdida de precisión en punto flotante y demuéstralo con un ejemplo numérico (por ejemplo, sumar 0.1 + 0.2 en punto flotante).

#### Explicación
La pérdida de precisión ocurre porque los ordenadores representan números decimales usando una cantidad limitada de bits (por ejemplo, 32 o 64 bits bajo el estándar IEEE 754). Muchos números fraccionarios cotidianos en base 10 (como $0.1$ o $0.2$) no tienen una representación binaria exacta finita; se convierten en fracciones periódicas infinitas en base 2 (similar a $1/3 = 0.3333...$ en base 10). Al truncar o redondear este flujo infinito de bits para guardarlo en la mantisa, se introduce una pequeña discrepancia. Al hacer cálculos repetidos o sumarlos, este error de redondeo se propaga.

#### Demostración Numérica ($0.1 + 0.2$ en Python/IEEE 754 Doble Precisión)
Si ejecutamos en la terminal interactiva de Python:
```python
>>> 0.1 + 0.2
0.30000000000000004
>>> 0.1 + 0.2 == 0.3
False
```
Esto ocurre porque:
*   $0.1_{10} \approx 0.00011001100110011001100110011..._2$
*   $0.2_{10} \approx 0.00110011001100110011001100110..._2$
Al redondear y sumarlos, la representación binaria acumulada da un valor ligeramente superior a la representación redondeada de $0.3$ ($0.0100110011001100..._2$). Este error insignificante en escala humana puede causar fallos lógicos graves si los programadores comparan números en punto flotante con una igualdad estricta (`==`).

---

## Nivel 6 — Integración: script de verificación (el más difícil)

### 6.1 (práctico en Ubuntu) Escribe un script en Python (o Bash) que reciba un número entero decimal, imprima su representación en binario, octal y hexadecimal, en complemento a dos de 8, 16 y 32 bits, e indique si produce overflow en 8 bits con signo.

#### Código del Script (`verificar.py`)
```python
import sys

def get_twos_complement(val, bits):
    # Rango firmado permitido
    min_val = - (1 << (bits - 1))
    max_val = (1 << (bits - 1)) - 1
    if val < min_val or val > max_val:
        return "No aplica (fuera de rango)"
    
    # Cálculo de complemento a dos
    if val < 0:
        val = (1 << bits) + val
    
    binary_str = f"{val:0{bits}b}"
    # Agrupamos de 4 en 4 bits para facilitar su lectura
    grouped_binary = " ".join(binary_str[i:i+4] for i in range(0, len(binary_str), 4))
    return f"{grouped_binary} (Hex: 0x{val:0{bits//4}X})"

def main():
    if len(sys.argv) > 1:
        try:
            num = int(sys.argv[1])
        except ValueError:
            print("Error: El argumento debe ser un número entero.")
            sys.exit(1)
    else:
        try:
            num = int(input("Ingrese un número entero decimal: "))
        except ValueError:
            print("Error: Entrada no válida. Debe ser un número entero.")
            sys.exit(1)
            
    print(f"\nResultados para el número decimal: {num}")
    print("-" * 50)
    
    if num >= 0:
        print(f"Binario (bin):                 {bin(num)}")
        print(f"Octal (oct):                   {oct(num)}")
        print(f"Hexadecimal (hex):             {hex(num)}")
    else:
        print(f"Binario (bin):                 -{bin(abs(num))[2:]}")
        print(f"Octal (oct):                   -{oct(abs(num))[2:]}")
        print(f"Hexadecimal (hex):             -{hex(abs(num))[2:]}")
        
    print("\nRepresentaciones en Complemento a Dos:")
    print(f" 8 bits: {get_twos_complement(num, 8)}")
    print(f"16 bits: {get_twos_complement(num, 16)}")
    print(f"32 bits: {get_twos_complement(num, 32)}")
    
    # Overflow en 8 bits con signo
    if num < -128 or num > 127:
        print("\n¿Produce overflow en 8 bits con signo?: SÍ")
        print(f"Explicación: El valor {num} está fuera del rango de 8 bits con signo [-128, 127].")
    else:
        print("\n¿Produce overflow en 8 bits con signo?: NO")
        print(f"Explicación: El valor {num} está dentro del rango de 8 bits con signo [-128, 127].")
        
if __name__ == "__main__":
    main()
```

#### Pruebas del Script (Salidas Reales)

```bash
# Caso Límite Superior dentro de rango: 127
$ python verificar.py 127
Resultados para el número decimal: 127
--------------------------------------------------
Binario (bin):                 0b1111111
Octal (oct):                   0o177
Hexadecimal (hex):             0x7f

Representaciones en Complemento a Dos:
 8 bits: 0111 1111 (Hex: 0x7F)
16 bits: 0000 0000 0111 1111 (Hex: 0x007F)
32 bits: 0000 0000 0000 0000 0000 0000 0111 1111 (Hex: 0x0000007F)

¿Produce overflow en 8 bits con signo?: NO
Explicación: El valor 127 está dentro del rango de 8 bits con signo [-128, 127].

# Caso Límite Superior fuera de rango (Overflow positivo): 128
$ python verificar.py 128
Resultados para el número decimal: 128
--------------------------------------------------
Binario (bin):                 0b10000000
Octal (oct):                   0o200
Hexadecimal (hex):             0x80

Representaciones en Complemento a Dos:
 8 bits: No aplica (fuera de rango)
16 bits: 0000 0000 1000 0000 (Hex: 0x0080)
32 bits: 0000 0000 0000 0000 0000 0000 1000 0000 (Hex: 0x00000080)

¿Produce overflow en 8 bits con signo?: SÍ
Explicación: El valor 128 está fuera del rango de 8 bits con signo [-128, 127].

# Caso Límite Inferior dentro de rango: -128
$ python verificar.py -128
Resultados para el número decimal: -128
--------------------------------------------------
Binario (bin):                 -10000000
Octal (oct):                   -200
Hexadecimal (hex):             -80

Representaciones en Complemento a Dos:
 8 bits: 1000 0000 (Hex: 0x80)
16 bits: 1111 1111 1000 0000 (Hex: 0xFF80)
32 bits: 1111 1111 1111 1111 1111 1111 1000 0000 (Hex: 0xFFFFFF80)

¿Produce overflow en 8 bits con signo?: NO
Explicación: El valor -128 está dentro del rango de 8 bits con signo [-128, 127].

# Caso Límite Inferior fuera de rango (Overflow negativo): -129
$ python verificar.py -129
Resultados para el número decimal: -129
--------------------------------------------------
Binario (bin):                 -10000001
Octal (oct):                   -201
Hexadecimal (hex):             -81

Representaciones en Complemento a Dos:
 8 bits: No aplica (fuera de rango)
16 bits: 1111 1111 0111 1111 (Hex: 0xFF7F)
32 bits: 1111 1111 1111 1111 1111 1111 0111 1111 (Hex: 0xFFFFFF7F)

¿Produce overflow en 8 bits con signo?: SÍ
Explicación: El valor -129 está fuera del rango de 8 bits con signo [-128, 127].

# Caso Cero: 0
$ python verificar.py 0
Resultados para el número decimal: 0
--------------------------------------------------
Binario (bin):                 0b0
Octal (oct):                   0o0
Hexadecimal (hex):             0x0

Representaciones en Complemento a Dos:
 8 bits: 0000 0000 (Hex: 0x00)
16 bits: 0000 0000 0000 0000 (Hex: 0x0000)
32 bits: 0000 0000 0000 0000 0000 0000 0000 0000 (Hex: 0x00000000)

¿Produce overflow en 8 bits con signo?: NO
Explicación: El valor 0 está dentro del rango de 8 bits con signo [-128, 127].
```

---

### 6.2 A partir del resultado de tu script, redacta un párrafo explicando qué pasaría si un sensor de hardware reporta temperaturas como enteros de 8 bits con signo y se produce un overflow silencioso: ¿qué valor vería el sistema y por qué es peligroso en un contexto real (por ejemplo, un sistema embebido)?

Si el sensor de hardware reporta temperaturas usando un tipo de datos con signo de 8 bits (rango de $-128^\circ\text{C}$ a $+127^\circ\text{C}$) y la temperatura real del entorno sube de $127^\circ\text{C}$ a $128^\circ\text{C}$, se producirá un **desbordamiento silencioso (silent overflow)**. Físicamente, el patrón de bits cambiará de `01111111` ($+127$) a `10000000` (el cual en formato signed de 8 bits se interpreta como $-128$). En consecuencia, el sistema informático interpretará de manera errónea que la temperatura ha caído repentinamente a **$-128^\circ\text{C}$**. 

En un sistema embebido real (como un controlador de caldera industrial, un autoclave médico o un sistema de control automotriz), esto es extremadamente peligroso por dos razones fundamentales:
1.  **Fallo de los sistemas de parada de emergencia:** Un algoritmo que apague la caldera al superar los $110^\circ\text{C}$ no se activará, porque para el microcontrolador la temperatura actual reportada es de $-128^\circ\text{C}$ (lo cual considera seguro y muy lejano al umbral de peligro).
2.  **Activación inversa e incentivo al sobrecalentamiento:** La lógica de control del bucle de retroalimentación (por ejemplo, un controlador PID) puede interpretar la lectura de $-128^\circ\text{C}$ como que el sistema se está congelando y necesita calentarse con urgencia. En lugar de activar los ventiladores o válvulas de alivio para enfriarlo, encenderá los calentadores a máxima potencia. Esto generará un proceso de **retroalimentación desbocada (runaway)** que podría culminar en un incendio, explosión o daño estructural irreparable en el equipo.
