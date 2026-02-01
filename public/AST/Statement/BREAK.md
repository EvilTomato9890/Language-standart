---
type: ast_node
node_kind: operator
node_name: BREAK
operator_class: Statement
short_info: Прерывает исполнение [[WHILE]]
storage_fmt: BREAK
version: 0.1.0
status: draft
tags:
  - node
  - operator
created: 2026-01-31
---

# BREAK

Прерывает исполнение [[WHILE]]

---
## Свойства и функционал 

### Функционал ASM
Совершает переход на метку конца цикла

>**Вид в ASM**
> ```
> :while_start
> PUSHR RAX
> PUSH 1
> JNE :while_end
> JMP :while_end # Это и есть BREAK
> PUSH 1
> OUT
> JMP :while_start
> :while_end
> ```

### Свойства и особенности
- Не может существовать вне цикла

---

## Формат узла

> [!info] Обозначения
> **...** — нет ограничений.

| child | имя | класс |  примечание |
|:-----:|:---:|:-----:|:--------:|
| left  | ... | Void |  ... |
| right | ... | Void |  ...|

**Иные требования к детям:** Отсутстсвуют

---

### Примеры

> **Минимальныe примеры:**
> ```
> WHILE (1 () ()) (BREAK () ())
> ```
> *Результат: цикл, который запуститься и сразу завершиться*


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