---
type: ast_node
node_kind: operator
node_name: MUL
operator_class: Expression
short_info: Перемножает 2 числа
storage_fmt: MUL
version: 0.1.0
status: draft
tags:
  - node
  - operator
created: 2026-01-31
---

# MUL

Перемножает 2 числа

---
## Свойства и функционал 

### Функционал ASM
Умножает 2-ое число со стека на 1-ое число со стека

>**Вид в ASM**
> ```
> PUSH 1
> PUSH 1
> MUL
> ```
### Свойства и особенности
Отсутствуют

---

## Формат узла

> [!info] Обозначения
> **...** — нет ограничений.

| Ребенок | Имя | Класс | Примечание |
|:-----:|:---:|:-----:|:----------:|
| left  | ... | Expression |  ...  |
| right | ... | Expression |  ...  |

**Иные требования к детям:** Отсутствуют

---

### Примеры

> **Минимальныe примеры:**
> ```
> MUL (1 () ()) (1 () ())
> ```
> *Результат: 1*


> **Стандартныe примеры:**
> ```
> NUL (2 () ()) 
> 	(PLUS (1 () ()) 
> 		  (1 () ()))
> ```
> *Результат: 4*

> **Пограничныe примеры:**
> ```
> MUL (10 () ()) (0 () ())
> ```
> *Результат: 0*

## Связанные операторы
%% DATAVIEW_PUBLISHER: start
```dataview

TABLE

  file.outlinks AS "Ссылается на",

  file.inlinks  AS "Ссылаются на него"

FROM ""

WHERE file.path = this.file.path

```
%%
%% DATAVIEW_PUBLISHER: end %%

---
