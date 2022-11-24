# Деление с остатком

Пусть мы хотим получить остаток от деления $a % b = r$, причем $0 \leq r < b$. Перепишем это так: $a = q\cdot b + r$, где $0 \leq q \leq \cfrac{a}{b}, 0 \leq r < b$

Будем говорить $a \vdots b$, если $a = k \cdot b$

# НОД

НОД(a, b) = k значит, что $a = k \cdot q_a, b = k \cdot q_b$, причем $k -$ максимально возможное

*Примеры:* НОД(5, 7) = 1, НОД(5, 25) = 5, НОД(28, 28) = 28, НОД(0, х) = х, НОД(х, 0) = х

# Алгоритм Евклида

Допустим, мы ищем НОД(a, b) = n, причем $a > b$. Давайте посмотрим на $a % b$, мы уже знаем, что это $a - b \cdot q = r$. Но смотрите, $a \vdots n, b \vdots n$, а значит и $r \vdots n$.

Теперь у нас есть $b \vdots n, r \vdots n$ и мы знаем $b > r$. Будем проделывать тот же фокус: НОД(a, b) = НОД(b, r) = ...

А если однажды $a % b = 0$? Значит $b$ и было нужным нам НОД'ом.

# Реализация

```python
a = int(input())
b = int(input())
a, b = min(a, b), max(a, b) # нам принципиально a >= b! >=, кстати, значит, что наш алгоритм не сломается, например, при вычислении НОД(100500, 100500)

while b != 0:
	a, b = b, a % b # на новом шаге, а - это b из предыдущего шага, а b - это r из объяснения или просто остаток от деления
print(a)
```