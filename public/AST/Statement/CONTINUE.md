---
type: ast_node
node_kind: operator
node_name: CONTINUE
operator_class: Statement
short_info: Завершает текущую итерацию цикла и переходит к следующей
storage_fmt: CONTINUE
version: 0.1.0
status: draft
tags:
  - node
  - operator
created: 2026-02-01
---

# CONTINUE

Завершает текущую итерацию цикла и переходит к следующей

---
## Свойства и функционал 

### Функционал ASM
Совершает переход на метку начала цикла

>**Вид в ASM**
> ```
> :while_start
> PUSHR RAX
> PUSH 1
>
> JNE :while_end
> PUSHR RAX
> PUSH 0
>
> JE :1
> JMP :while_start # Это и есть CONTINUE
> :1
>
> PUSH 1 #Какое-то тело цикла
> OUT
> JMP :while_start
> :while_end
> ```

### Свойства и особенности
- Не может существовать без цикла

---

## Формат узла

> [!info] Обозначения
> **...** — нет ограничений.

| Ребенок | Имя | Класс |  Примечание |
|:-----:|:---:|:-----:|:--------:|
| left  | ... | Void | ... |
| right | ... | Void | ...|

**Иные требования к детям:** Отсутствуют

---

### Примеры

> **Минимальныe примеры:**
> ```
> WHILE (1 () ()) (SEQ (CONTINUE () ()) 
> 				     (PRINT () (1 () ()))
> ```
> *Результат: бесконечный цикл, который ничего не делает*


> **Стандартныe примеры:**
> ```
> Не сильно отличаются от минимальных примеров
> ```

> **Пограничныe примеры:**
> ```
> Отсутсвуют
> ```

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