
---
type: ast_node
node_kind: operator
node_name: "IF"
operator_class: "Statement"
operator_group: "COndition"
short_info: "Делает побайтовое сравнение аргумента с 1 и если все сравнение успешно, то выполняет код"
storage_fmt: "IF"
version: 0.1.0
status: draft
tags:
 - node
 - operator
created: 2025-12-21
---

# IF

Делает побайтовое сравнение аргумента с 1 и если все сравнение успешно, то выполняет код

## Назначение и функционал в ASM
Что делает этот узел

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
%% DATAVIEW_PUBLISHER: start
```dataview

TABLE

  file.outlinks AS "Ссылается на",

  file.inlinks  AS "Ссылаются на него"

FROM ""

WHERE file.path = this.file.path

```
%%

| File                                                  | Ссылается на | Ссылаются на него                                                            |
| ----------------------------------------------------- | ------------ | ---------------------------------------------------------------------------- |
| [[AST/Operators/Statement/COndition/IF.md.md\|IF.md]] | <ul></ul>    | <ul><li>[[AST/Operators/Statement/COndition/ELSE.md.md\|ELSE.md]]</li></ul> |

%% DATAVIEW_PUBLISHER: end %%

