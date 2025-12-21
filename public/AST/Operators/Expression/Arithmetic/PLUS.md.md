---
type: ast_node
node_kind: operator
node_name: "PLUS"
operator_class: "Expression"
operator_group: "Arithmetic"
short_info: "Складывает 2 числа"
storage_fmt: "PLUS"
version: 0.1.0
status: draft
tags:
 - node
 - operator
created: 2025-12-21
---

# PLUS

Складывает 2 числа

---

## Свойства и функционал 

### Функционал ASM
Складывает 2 числа и бросает результат на стэк.

>**Вид в ASM**
> ```
> PUSH 1
> PUSH 1
> ADD
> ```

### Свойства
- Левоассоциативен

---

## Формат узла

> [!info] Обозначения
> **NC** (*no child*) — нулевой ребенок.
> **...** — нет необходимости в данных.

| child | имя | класс | группа| примечание |
|:-----:|:---:|:-----:|:-----:|:--------:|
| left  | ... | Expression | ... | ... |
| right | ... | Expression | ... | ...|

**Иные требования к детям:**
- Оба ребенка ненулевые

---

### Примеры

> Минимальный пример:
> ```
> PLUS (1 () ()) (1 () ())
> ```


> Стандартный пример:
> ```
> PLUS (PLUS (1 () ()) 
>            (1 () ()))
> 	 (1 () ())
> ```


  

## Связанные операторы

```dataview

TABLE

  file.outlinks AS "Ссылается на",

  file.inlinks  AS "Ссылаются на него"

FROM ""

WHERE file.path = this.file.path

```


>[!question] Что нужно обдумать
> Как храним else/elseif