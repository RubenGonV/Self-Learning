 
 🧾 **Lectura de archivos**
```python
# Leer todo el archivo como una lista de líneas
with open("input.txt") as f:
    lines = [line.strip() for line in f]

# Leer todo en un string
text = open("input.txt").read()
```

🔤 **Manipulación de strings**
```python
s = " Hola, Mundo! "

s.strip()          # "Hola, Mundo!"
s.lower()          # " hola, mundo! "
s.upper()          # " HOLA, MUNDO! "
s.replace(",", "") # " Hola Mundo! "

# Dividir y unir
s.split()          # ["Hola,", "Mundo!"]
",".join(["a", "b", "c"])  # "a,b,c"

# Substrings
s[0:4]   # " Hol"
s[::-1]  # reversa
```

📊 **Contar cosas**
```python
from collections import Counter

words = text.lower().split()
freq = Counter(words)

# Top 5 palabras más frecuentes
freq.most_common(5)

# Acceso directo
freq["hola"]
```

🧩 **Búsqueda de patrones**
```python
# Buscar subcadenas
"abc" in "zabcx"        # True
"zabcx".find("abc")     # 1 (índice)
"zabcx".count("a")      # 1

# Expresiones regulares
import re
re.findall(r"\d+", "id=123 code=45")  # ["123", "45"]
```

🗂️ **Diccionarios y sets**
```python
d = {}
d["alice"] = 3
d.get("bob", 0)   # valor por defecto si no existe

s = set("aabcc")  # {"a", "b", "c"}
len(s)            # 3
```

**Enumerate() in Python**
```python
a = ["Geeks", "for", "Geeks"]

# Iterating list using enumerate to get both index and element
for i, name in enumerate(a):
    print(f"Index {i}: {name}")

# Converting to a list of tuples
print(list(enumerate(a)))
```
>[!info] **Output**: 
>```
>Index 0: Geeks
>Index 1: for
>Index 2: Geeks
>[(0, 'Geeks'), (1, 'for'), (2, 'Geeks')]
>```
>


⏱️ **Paréntesis balanceados**
```python
def longest_valid_parentheses(s):
    stack, max_len = [-1], 0
    for i, ch in enumerate(s):
        if ch == "(":
            stack.append(i)
        else:
            stack.pop()
            if not stack:
                stack.append(i)
            else:
                max_len = max(max_len, i - stack[-1])
    return max_len
```

🔄 **Reglas de sustitución**
```python
rules = {"A": "BC", "B": "A"}
s = "A"

for _ in range(5):  # 5 pasos
    s = "".join(rules.get(c, c) for c in s)
```

🏃 **Substrings sin repetidos**
```python
def longest_unique_substring(s):
    seen, start, max_len = {}, 0, 0
    for i, ch in enumerate(s):
        if ch in seen and seen[ch] >= start:
            start = seen[ch] + 1
        seen[ch] = i
        max_len = max(max_len, i - start + 1)
    return max_len
```

**Ordenar un dict**
Ordenar por valor en un dict (valor descendente, clave ascendente como tie-breaker):

```python
d = {'apple': 2, 'banana': 3, 'cherry': 2} sorted(d.items(), key=lambda x: (-x[1], x[0])) 
# [('banana', 3), ('apple', 2), ('cherry', 2)]`
```

Explicación de `lambda x: (-x[1], x[0])`:
- `-x[1]` → hace que el sort por valor sea **descendente** (más grande primero).
- `x[0]` → en caso de empate en valores, ordena por clave **ascendente**.

```python
a = [1,2,3]
b = ['x','y']
list(zip(a,b))   # [(1,'x'), (2,'y')]  -> 3 desaparece porque b es más corto

# Si quieres emparejar sin truncar:
from itertools import zip_longest
list(zip_longest(a, b, fillvalue=None))  # [(1,'x'), (2,'y'), (3, None)]

# Desempaquetar (transpose):
pairs = [(1,'a'), (2,'b')]
nums, letters = zip(*pairs)  # nums=(1,2), letters=('a','b')
```

**`any()` / `all()`**

- `any(iterable)` → `True` si **algún** elemento es True.
- `all(iterable)` → `True` si **todos** son True.
- **Evaluación perezosa (short-circuit)**: para `any`, para al encontrar `True`; para `all`, para al encontrar `False`.

```python
any([0, "", None, 5])     # True (porque 5 es truthy)
all([1, 2, 3])            # True
all([])                   # True  -> atención: vacuamente verdadero
any([])                   # False -> vacío no tiene elemento True
```


---------------

Buena pregunta — vamos al grano. Con el **cheatsheet** que te di tienes una **base sólida** (parsing, Counter, sliding-window, stacks, diccionarios, regex básicos). Pero la lista contiene problemas de **dificultad media y alta** que requieren algoritmos/estructuras concretas que no estaban en el cheatsheet. Abajo te digo, problema por problema, **si lo puedes resolver ya** con lo que tienes, **qué técnica** necesitas y **qué añadir** mínimo (snippet/idea) si hace falta.

---

# ✅ La que puedes resolver **con lo que ya tienes + pequeños ajustes**

(cheatsheet suficiente o con un par de líneas extra)

1. **First Repeating Character** — usar `dict`/`Counter`.
    
2. **First Non-Repeating Character** — `Counter` o map con orden; sliding window si variante.
    
3. **K’th Non-repeating Character** — mantener orden (deque) + map.
    
4. **Check for Rotation** — `s1 in s2+s2` o KMP si quieres rendimiento worst-case. _(cheatsheet OK; añadir KMP si eres quisquilloso)_
    
5. **Implement atoi** — parsing seguro con checks (signos, overflow). _(cheatsheet OK)_
    
6. **Validate IP Address** — `split('.')` y checks numéricos; regex opcional. _(cheatsheet OK)_
    
7. **Add n Binary Strings** — suma bit a bit con carry; `int()` si aceptable. _(cheatsheet OK)_
    
8. **Isomorphic Strings** — map de mapeo bidireccional. _(cheatsheet OK)_
    
9. **Remove Adjacent** — stack simple. _(cheatsheet OK)_
    
10. **Roman to Integer** — map + scan derecho->izquierdo. _(cheatsheet OK)_
    
11. **Permutations of a String** — backtracking / `itertools.permutations`. _(cheatsheet OK)_
    
12. **Anagram substrings** — sliding window + Counter. _(cheatsheet OK)_
    
13. **Binary strings without consecutive 1’s** — DP simple (fibonacci-like). _(cheatsheet OK)_
    
14. **Lexicographically next string** — next-permutation algorithm (impleméntalo). _(cheatsheet OK)_
    
15. **Split String into four distinct strings** — combinatoria + pruning/brute-force limitada. _(cheatsheet OK con backtracking)_
    
16. **String to mobile numeric keypad sequence** — map char->digits. _(cheatsheet OK)_
    

---

# ⚠️ Necesitan **técnicas adicionales moderadas** (añadir 1–2 snippets o estructuras)

(cheatsheet útil pero incompleto; añade snippet pequeño)

1. **First Repeating / Non-** (si vienen con streaming o ventanas grandes en constraints) — usar deque + map (añade snippet).
    
2. **Add n Binary Strings** (si n grandes y streaming) — implementar suma por chunks.
    
3. **Interleaved Strings** — **DP 2D** (subconjuntos: típico: `dp[i][j]`). Añadir template DP 2D.
    
4. **Longest Palindromic Substring** — **Manacher** (óptimo O(n)) o DP O(n²). Añadir snippet Manacher (recomendado).
    
5. **Split String (variantes con restricciones)** — backtracking con memo. Añadir memoization pattern.
    
6. **Word Break Problem** — DP/Trie approach. Añadir template DP booleano `dp[i]`.
    
7. **Minimum Swaps for Bracket Balancing** — greedy o stack (snippet en cheatsheet similar a paréntesis).
    
8. **Shortest path to print a string on screen** — problema tipo BFS/DP sobre estados; añadir plantilla BFS sobre estados.
    

---

# 🔥 Hard — requieren conocimientos/estructuras avanzadas o ideas no triviales

(aunque resolubles, requieren prácticas y snippets concretos)

1. **Lexicographic Rank of a String** — combinatoria + factorials mod (si pedían módulo), manejo de repetidos. Añade factorial precompute + combinatorics.
    
2. **Multiply Large Numbers / Multiply 2 Strings** — algoritmo escolar (FFT no obligatorio, pero multiplicación por convolution si límites altos). Añadir función multiply-strings O(n*m).
    
3. **Ways to increase LCS length of 2 strings by one** — DP LCS + análisis; requiere entendimiento avanzado de DP y reconstrucción.
    
4. **Alien Dictionary** — construir grafo de precedencias + **topological sort** + detección de ciclos. Añadir snippet de topo sort (Kahn o DFS).
    
5. **Make two strings Anagram / Without Deletion** — conteo de frecuencias; para versión sin borrado puede implicar matching greedy; detalles.
    
6. **Palindrome Substring Queries** — precálculo con **palindromic tree (Eertree)** o Manacher + RMQ; depende de tipo de query/updates. Eertree es la herramienta correcta para queries masivas.
    
7. **Word Search (8 directions / zig-zag)** — **Trie + DFS backtracking** (para encontrar muchas palabras eficientemente). Añadir snippet Trie + backtracking + pruning.
    
8. **Minimum bracket reversals to make balanced** — conteo y fórmula (si sólo {} o paréntesis). Requiere análisis.
    
9. **Word Wrap problem** — DP minima raggedness (classic O(n²) DP). Añadir DP template.
    
10. **Decode a string encoded with recursive substring counts** (`3[a2[c]]`) — stack-based parsing/recursion; cheatsheet has basic stack but añadir parser snippet.
    
11. **Multiply Large Numbers** (reiterado) — same as earlier.
    
12. **Make two Strings Anagram Without Deletion** — variant subtle; requires case-by-case.
    

---

# Conclusión práctica (sin rodeos)

- **Con el cheatsheet actual** puedes resolver **muchos problemas de la lista (sobre todo medium)**: counting, sliding-window, stacks, parsing, DP básicos y backtracking.
    
- **Para los problemas “moderados”** necesitas añadir ~4–6 snippets: **DP 2D template**, **Manacher**, **KMP (opcional pero útil)**, **Trie**, **topological sort (Kahn/DFS)**, **string-multiplication escolar**.
    
- **Para los “hard”** (Alien Dictionary, Palindrome substring queries a gran escala, Word Search masivo, LCS tweaks, etc.) tienes que practicar y añadir estructuras/algoritmos avanzados: **Eertree (palindromic tree)**, **FFT/convolution** (solo si límites muy altos), y dominar **trie+dfs** y **graph topo**.
    

---

# Qué te propongo (si quieres que lo haga ahora)

Puedo:

- Generar **snippets Python listos para copiar** de las piezas que faltan: **Manacher, KMP, Trie + Boggle solver, Topological sort, DP 2D template, Multiply strings**, y **un template “examen”** con lectura/tiempo/estructura de respuesta.
    
- O bien darte un **plan de práctica**: 10 ejercicios (de fácil→duro) con orden recomendado.
    

Dime cuál prefieres y en 1 respuesta te suelto los snippets listos para usar (sin florituras). ¿Qué quieres primero: **snippets** o **plan de práctica**?

Perfecto 🚀  
Aquí va tu **colección de snippets Python**, todos **bien comentados** y con explicación de **para qué sirven**. Esto cubre los huecos que tu cheatsheet no tenía y te arma un arsenal listo para atacar problemas de strings de nivel _medium → hard_.

---

# 🔎 **1. KMP (Knuth-Morris-Pratt) – búsqueda de patrón**

Sirve para: buscar si un string `pattern` está dentro de otro `text` en **O(n)** sin retrocesos tontos (mejor que `.find()` si hay límites grandes).

```python
def kmp_search(text, pattern):
    """
    Devuelve la lista de índices donde aparece 'pattern' en 'text'.
    Útil para Check for Rotation, Anagram Substrings o cualquier búsqueda eficiente.
    """
    # Preprocesar patrón -> longest prefix-suffix (lps)
    lps = [0] * len(pattern)
    j = 0
    for i in range(1, len(pattern)):
        while j > 0 and pattern[i] != pattern[j]:
            j = lps[j - 1]
        if pattern[i] == pattern[j]:
            j += 1
            lps[i] = j

    # Buscar
    res, j = [], 0
    for i in range(len(text)):
        while j > 0 and text[i] != pattern[j]:
            j = lps[j - 1]
        if text[i] == pattern[j]:
            j += 1
        if j == len(pattern):
            res.append(i - j + 1)
            j = lps[j - 1]
    return res
```

---

# 🪞 **2. Manacher’s Algorithm – Longest Palindromic Substring en O(n)**

Sirve para: encontrar el palíndromo más largo dentro de un string. Problema muy común.

```python
def manacher(s):
    """
    Devuelve el palíndromo más largo en O(n).
    Transformación con '#' para unificar casos par/impar.
    """
    # Transformar: "abba" -> "^#a#b#b#a#$"
    T = "^#" + "#".join(s) + "#$"
    n = len(T)
    P = [0] * n
    C = R = 0  # centro, derecha actual
    for i in range(1, n - 1):
        mirror = 2 * C - i
        if i < R:
            P[i] = min(R - i, P[mirror])
        # expandir
        while T[i + 1 + P[i]] == T[i - 1 - P[i]]:
            P[i] += 1
        # actualizar centro y derecha
        if i + P[i] > R:
            C, R = i, i + P[i]
    # Encontrar el máximo
    max_len, center = max((v, i) for i, v in enumerate(P))
    start = (center - max_len) // 2  # índice en s original
    return s[start:start + max_len]
```

---

# 📚 **3. Word Break – DP booleana**

Sirve para: comprobar si un string puede partirse en palabras de un diccionario (Word Break Problem).

```python
def word_break(s, wordDict):
    """
    Devuelve True si 's' puede segmentarse en palabras del diccionario.
    Técnica: DP booleana.
    """
    word_set = set(wordDict)
    n = len(s)
    dp = [False] * (n + 1)
    dp[0] = True

    for i in range(1, n + 1):
        for j in range(i):
            if dp[j] and s[j:i] in word_set:
                dp[i] = True
                break
    return dp[n]
```

---

# 🕸 **4. Topological Sort (Alien Dictionary)**

Sirve para: ordenar letras según precedencias dadas (grafo dirigido acíclico).

```python
from collections import defaultdict, deque

def alien_dictionary(words):
    """
    Dadas palabras en "idioma alienígena", deduce el orden de las letras.
    Grafo + BFS (Kahn).
    """
    # Construir grafo
    graph = defaultdict(set)
    indegree = {c: 0 for word in words for c in word}

    for w1, w2 in zip(words, words[1:]):
        for c1, c2 in zip(w1, w2):
            if c1 != c2:
                if c2 not in graph[c1]:
                    graph[c1].add(c2)
                    indegree[c2] += 1
                break

    # Topological sort
    q = deque([c for c in indegree if indegree[c] == 0])
    res = []
    while q:
        c = q.popleft()
        res.append(c)
        for nei in graph[c]:
            indegree[nei] -= 1
            if indegree[nei] == 0:
                q.append(nei)

    return "".join(res) if len(res) == len(indegree) else ""
```

---

# 🔢 **5. Multiplicar Strings grandes**

Sirve para: multiplicar números enormes representados como strings (cuando `int()` no vale).

```python
def multiply_strings(num1, num2):
    """
    Multiplica dos números grandes representados como strings.
    Algoritmo escolar O(n*m).
    """
    if num1 == "0" or num2 == "0":
        return "0"

    m, n = len(num1), len(num2)
    res = [0] * (m + n)

    for i in range(m - 1, -1, -1):
        for j in range(n - 1, -1, -1):
            mul = int(num1[i]) * int(num2[j])
            summ = mul + res[i + j + 1]
            res[i + j + 1] = summ % 10
            res[i + j] += summ // 10

    # convertir a string
    result = "".join(map(str, res)).lstrip("0")
    return result
```

---

# 🌳 **6. Trie + Word Search (tipo Boggle)**

Sirve para: encontrar muchas palabras en una grid (DFS + Trie para pruning rápido).

```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.word = None

def build_trie(words):
    root = TrieNode()
    for w in words:
        node = root
        for c in w:
            node = node.children.setdefault(c, TrieNode())
        node.word = w
    return root

def find_words(board, words):
    """
    Busca palabras en el tablero usando Trie + DFS.
    Útil para Word Search con múltiples direcciones.
    """
    root = build_trie(words)
    res, m, n = set(), len(board), len(board[0])

    def dfs(i, j, node):
        c = board[i][j]
        if c not in node.children:
            return
        nxt = node.children[c]
        if nxt.word:
            res.add(nxt.word)
        board[i][j] = "#"  # marcar visitado
        for dx, dy in [(1,0),(-1,0),(0,1),(0,-1),(1,1),(-1,-1),(1,-1),(-1,1)]:
            ni, nj = i + dx, j + dy
            if 0 <= ni < m and 0 <= nj < n and board[ni][nj] != "#":
                dfs(ni, nj, nxt)
        board[i][j] = c

    for i in range(m):
        for j in range(n):
            dfs(i, j, root)
    return list(res)
```

---

# 🧩 **7. DP 2D Template (Interleaving Strings, LCS, etc.)**

Sirve para: cualquier problema donde se comparan dos strings caracter a caracter.

```python
def is_interleave(s1, s2, s3):
    """
    Comprueba si s3 es interleaving de s1 y s2.
    Classic DP 2D.
    """
    if len(s1) + len(s2) != len(s3):
        return False
    dp = [[False] * (len(s2) + 1) for _ in range(len(s1) + 1)]
    dp[0][0] = True

    for i in range(len(s1) + 1):
        for j in range(len(s2) + 1):
            if i > 0:
                dp[i][j] |= dp[i - 1][j] and s1[i - 1] == s3[i + j - 1]
            if j > 0:
                dp[i][j] |= dp[i][j - 1] and s2[j - 1] == s3[i + j - 1]
    return dp[-1][-1]
```

---

# 🎁 Bonus: **Decode Nested Encoded Strings** (`3[a2[c]]`)

Sirve para: stack parsing de expresiones tipo "decode string".

```python
def decode_string(s):
    """
    Decodifica string como '3[a2[c]]' -> 'accaccacc'.
    Stack para números y substrings.
    """
    stack, curr_num, curr_str = [], 0, ""
    for ch in s:
        if ch.isdigit():
            curr_num = curr_num * 10 + int(ch)
        elif ch == "[":
            stack.append((curr_str, curr_num))
            curr_str, curr_num = "", 0
        elif ch == "]":
            prev_str, num = stack.pop()
            curr_str = prev_str + curr_str * num
        else:
            curr_str += ch
    return curr_str
```

---

✅ Con estos snippets tienes:

- **Búsqueda eficiente (KMP)**
    
- **Palíndromos largos (Manacher)**
    
- **DP en strings (Word Break, Interleaving)**
    
- **Grafos con dependencias (Alien Dictionary)**
    
- **Multiplicación de strings grandes**
    
- **Trie + DFS para word search**
    
- **Decodificación de strings recursivos**
    

Es decir, justo lo que faltaba en tu arsenal para cubrir la lista de problemas medium/hard.

---

👉 ¿Quieres que te arme un **mapa directo de qué snippet aplicar a cada problema de tu lista** (como “usar snippet 2 para Longest Palindromic Substring, snippet 4 para Alien Dictionary”, etc.), o prefieres que te deje con esta caja de herramientas y tú vas mapeando?