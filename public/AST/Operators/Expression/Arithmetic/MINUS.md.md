---
type: ast_node
node_kind: operator
node_name: "MINUS"
operator_class: "Expression"
operator_group: "Arithmetic"
short_info: "Вычитает из 1-ого числа 2-ое"
storage_fmt: "MINUS"
version: 0.1.0
status: draft
tags:
 - node
 - operator
created: 2025-12-21
---

# MINUS

Вычитает из 1-ого числа 2-ое

---
## Свойства и функционал 

### Функционал ASM
Вычитает из 1-ого числа второе и бросает результат на стэк

>**Вид в ASM**
> ```
> PUSH 1
> PUSH 1
> SUB
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
- Оба ребенка должны существовать

---

### Примеры

> Минимальный пример:
> ```
> MINUS (0 () ()) (0 () ())
> ```
> *Результат: 0*


> Стандартный пример:
> ```
> MINUS (MINUS (1 () ())
> 			(-1) () ())
> 	  (1 () ())
> ```
> *Результат 1*

> Пограничный пример:
> ```
> Какой-то страшный код
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

| File                                                                 | Ссылается на | Ссылаются на него |
| -------------------------------------------------------------------- | ------------ | ----------------- |
| [[public/AST/Operators/Expression/Arithmetic/MINUS.md.md\|MINUS.md]] | <ul></ul>    | <ul></ul>         |

%% DATAVIEW_PUBLISHER: end %%
>[!question] Что нужно обдумать
> Как дальше жить