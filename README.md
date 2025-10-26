# **ЗВІТ З ЛАБОРАТОРНОЇ РОБОТИ **

## **Тема роботи**

Операції з масивами в бібліотеці **NumPy**.
Створення, обробка та аналіз багатовимірних масивів у середовищі **Jupyter Notebook**.

---

## **Мета роботи**

Ознайомитися з основними можливостями бібліотеки **NumPy**,
навчитись створювати масиви `ndarray`, виконувати з ними базові та лінійні операції,
використовувати векторизацію замість циклів, а також порівнювати ефективність різних підходів обчислення.

---

## **Лістинги комірок**

### **Вправа 2.**

Створити матрицю `n×n`, у якій елементи 1 та 0 розташовані в шаховому порядку, починаючи з 1.
Виконати двома способами: через функції **NumPy** та через цикли.

```python
def task_2_numpy(n: int):
    a = np.zeros((n, n), dtype=int)
    a[::2, ::2] = 1
    a[1::2, 1::2] = 1
    return a
```

<img width="152" height="30" alt="image" src="https://github.com/user-attachments/assets/69f917a8-e279-412c-87e7-35dbf1f9e147" />


---

### **Вправа 4.**

Вивести матрицю `n×m`, у якій перший рядок містить числа від 0 до m−1, а всі інші — нулі.

```python
def task_4_numpy(n: int, m: int):
    a = np.zeros((n, m), dtype=int)
    a[0] = np.arange(m)
    return a
```

<img width="156" height="92" alt="image" src="https://github.com/user-attachments/assets/c5b53d85-6710-4945-9f12-bf28fbe385ef" />


---

### **Вправа 5.**

Створити квадратну матрицю `n×n`, де у рядках з парними індексами стоять одиниці,
а в інших — нулі.

```python
def task_5_numpy(n: int):
    a = np.zeros((n, n), dtype=int)
    a[::2, :] = 1
    return a
```

<img width="233" height="124" alt="image" src="https://github.com/user-attachments/assets/7c40d476-b647-4719-aeee-da1836cacf83" />


---

### **Вправа 8.**

З клавіатури вводиться масив. Порахувати кількість нульових і ненульових елементів.

```python
def task_8_numpy(arr):
    zeros = np.count_nonzero(arr == 0)
    nonzeros = arr.size - zeros
    return zeros, nonzeros
```

<img width="336" height="23" alt="image" src="https://github.com/user-attachments/assets/38755d32-82e2-4d8f-804a-c02769b89115" />


---

### **Вправа 9.**

Створити масив значень від `n` до `0`.

```python
def task_9_numpy(n: int):
    return np.arange(n, -1, -1)
```

<img width="411" height="25" alt="image" src="https://github.com/user-attachments/assets/b924be2c-a47d-4055-af9f-b948d5c03b58" />


---

### **Вправа 12.**

Створити матрицю одиниць `n×n`, у якій рамка утворена нулями.

```python
def task_12_numpy(n: int):
    a = np.ones((n, n), dtype=float)
    a[0, :] = a[-1, :] = a[:, 0] = a[:, -1] = 0.0
    return a
```

<img width="193" height="108" alt="image" src="https://github.com/user-attachments/assets/cd22b6a5-c871-4688-927a-f833d4db08d9" />


---

### **Вправа 13.**

Розмістити на полі `8×8` нулі та одиниці у шаховому порядку, використовуючи функцію повторення `tile()`.

```python
def task_13_numpy():
    base = np.array([[0,1],[1,0]], dtype=int)
    return np.tile(base, (4,4))
```

<img width="234" height="193" alt="image" src="https://github.com/user-attachments/assets/5289cbfe-26c3-45ca-909c-ed97943e772f" />


---

### **Вправа 15.**

Заповнити парні стовпчики матриці `n×n` одиницями, а непарні — нулями.

```python
def task_15_numpy(n: int):
    a = np.zeros((n, n), dtype=int)
    a[:, 1::2] = 1
    return a
```

<img width="172" height="132" alt="image" src="https://github.com/user-attachments/assets/f36f8191-2677-4708-ba7c-9e78a88d5542" />


---

### **Вправа 19.**

Згенерувати вектор з `n` елементів, рівномірно розміщених на інтервалі (0,1),
не включаючи кінці інтервалу. Вивести значення з точністю до 3 знаків після коми.

```python
def task_19_numpy(n: int):
    v = np.linspace(0, 1, n+2, endpoint=False)[1:]
    return np.round(v, 3)
```


---

<img width="796" height="52" alt="image" src="https://github.com/user-attachments/assets/bfdc5920-175c-4481-b84a-84807de4e35e" />


[
\begin{cases}
x_2 - 3x_3 + 4x_4 = -5 \
x_1 - 2x_3 + 3x_4 = -4 \
3x_1 + 2x_2 - 5x_4 = 12 \
4x_1 + 3x_2 - 5x_3 = 5
\end{cases}
]

Розв’язано 4-ма способами:

1. Через обернену матрицю (A^{-1}b)
2. Через `numpy.linalg.solve`
3. За формулою Крамера
4. Методом Гаусса (цикли)

<img width="681" height="112" alt="image" src="https://github.com/user-attachments/assets/944825cb-3fe4-480b-8afb-85d4aea0eb6e" />


---

### **Матричний вираз**

[
(A^2 - B^2) \cdot (A + B)
]

Порівняно результати обчислення за допомогою NumPy та циклів,
проведено перевірку збігу результатів через `numpy.allclose()`.

<img width="361" height="129" alt="image" src="https://github.com/user-attachments/assets/ddd6badd-db7c-4ba8-bfc7-8d1cf67fd7e1" />


---

## **Висновки**

* Бібліотека **NumPy** дозволяє виконувати операції з великими масивами значно швидше, ніж стандартні цикли Python.
* Використання векторизації зменшує кількість коду і підвищує швидкодію.
* Для розв’язання систем лінійних рівнянь найефективніший метод — `numpy.linalg.solve`.
* Отримані результати для всіх способів співпали (`numpy.allclose = True`), що підтверджує коректність реалізації.
* Функції `perf_counter` дозволили виміряти реальний час виконання для порівняння ефективності.

---

## **Контрольні запитання**

1. **Основна мета створення NumPy:**
   Забезпечити ефективну роботу з багатовимірними масивами числових даних, оптимізовану під швидке виконання у мові Python.

2. **Відмінність ndarray від списків Python:**

   * Елементи одного типу.
   * Підтримує векторизацію операцій.
   * Фіксований розмір.
   * Працює значно швидше завдяки реалізації на C.

3. **Основні атрибути ndarray:**
   `ndim` — кількість вимірів,
   `shape` — форма,
   `size` — кількість елементів,
   `dtype` — тип даних,
   `itemsize` — розмір одного елемента в байтах.

4. **Способи створення масивів ndarray:**
   `np.array()`, `np.zeros()`, `np.ones()`, `np.arange()`, `np.linspace()`, `np.random.rand()` тощо.

5. **Основні типи даних NumPy:**
   `int8`, `int16`, `int32`, `float32`, `float64`, `complex64`, `bool` тощо.

6. **Що станеться при `a[0] = 4.897` у масиві `dtype=int`:**
   Значення буде **перетворене до цілого числа (4)**.

7. **Що станеться при `a[0] = 'hello'` у масиві `dtype=int`:**
   Виникне **помилка типу (`ValueError`)**, оскільки рядок не може бути перетворений у `int`.

8. **Різниця між `reshape()` і `resize()`:**

   * `reshape()` створює **новий об’єкт** без зміни початкового масиву.
   * `resize()` **змінює поточний масив на місці**.

9. **Способи вимірювання часу виконання коду:**
   `time.time()`, `time.perf_counter()`, модуль `timeit`, функція `%%time` у Jupyter.

10. **Арифметичні функції NumPy:**
    `add`, `subtract`, `multiply`, `divide`, `power`, `mod`, `abs`, `sqrt`.

11. **Агрегатні функції NumPy:**
    `sum`, `mean`, `max`, `min`, `std`, `var`, `argmax`, `argmin`.
    Викликаються як `np.sum(a)` або `a.sum()`.

12. **Відмінність функцій NumPy від стандартних Python:**
    Функції NumPy працюють **з векторами та матрицями одразу**,
    тоді як стандартні Python-функції — **поелементно та значно повільніше**.

---

<img width="1013" height="993" alt="image" src="https://github.com/user-attachments/assets/f73f5fc3-c6e8-4ae0-b3b3-5c1b6631af0b" />

---

