
---
type: ast_node
node_kind: operator
node_name: "ELSE"
operator_class: "Statement"
operator_group: "COndition"
short_info: "Если if не выполняется. то выполняется он сам"
storage_fmt: "ELSE"
version: 0.1.0
status: draft
tags:
 - node
 - operator
created: 2025-12-21
---

# ELSE

Если if не выполняется. то выполняется он сам

## Назначение и функционал в ASM
[[IF.md]]

## Формат узла

### Дети

> [!info] Обозначения
> **NC** (*no child*) — ребенок отсутствует).
> **NS** (*not specified*) — ребенок любой, но существует.
> **ANY**  — ребенок любой и можент не существовать

| child | имя | роль | описание |
|---:|-----|:----:|------|----------|
| left  | NS | NS | NS |
| right | NS | NS | NS |

**Валидатор обязан проверить:**
- структура: количество детей, обязательность, порядо
- ограничения по scope
- ограничения по control-flow

>[!node] Минимальный пример
>

>[!node] Стандартный пример
>

>[!node] Пограничный пример
>

## Семантика и интерпретация

### Порядок вычисления

- …


## Представление в ASM

Как выглядит в ASM
  

## Связанные операторы

```dataview

TABLE

  file.outlinks AS "Ссылается на",

  file.inlinks  AS "Ссылаются на него"

FROM ""

WHERE file.path = this.file.path

```

