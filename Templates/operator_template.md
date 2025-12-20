<%*
const sanitize = (s) => (s ?? "").trim().replace(/[\\\/:*?"<>|]/g, "_");

const raw_op = await tp.system.prompt("Имя оператора (например IF, PLUS, CALL)");
if (raw_op === null) throw new Error("Canceled: raw_op");

const op_class = await tp.system.suggester(
  ["Expression", "Statement"],
  ["Expression", "Statement"],
  true,
  "Класс оператора"
);

const op_group = await tp.system.suggester(
  ["Arithmetic", "Bool", "Condition", "Cycle", "Functions", "Structure", "IO"],
  ["Arithmetic", "Bool", "Condition", "Cycle", "Functions", "Structure", "IO"],
  true,
  "Группа оператора"
);

const short_desc = await tp.system.prompt("Коротко: что делает оператор (1 фраза)") ?? "";
if (short_desc === null) throw new Error("Canceled: short_desc");

const op = sanitize(raw_op || "OPERATOR");
const folder = "AST/Operators";
const targetDir  = `${folder}/${sanitize(op_class)}/${sanitize(op_group)}`;
const targetPath = `${targetDir}/${op}.md`;

if (!(await app.vault.adapter.exists(targetDir))) {
  await app.vault.createFolder(targetDir);
  new Notice(`📁 Создал папку: ${targetDir}`, 4500);
}

await tp.file.move(targetPath);
-%>

---
type: ast_node
node_kind: operator
node_name: "<% op %>"
operator_class: "<% op_class %>"
operator_group: "<% op_group %>"
short_info: "<% short_desc %>"
storage_fmt: "<% op %>"
version: 0.1.0
status: draft
tags:
 - node
 - operator
created: <% tp.date.now("YYYY-MM-DD") %>
---

# <% op %>

<% short_desc %>

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

```dataview

TABLE

  file.outlinks AS "Ссылается на",

  file.inlinks  AS "Ссылаются на него"

FROM ""

WHERE file.path = this.file.path

```


>[!question] Что нужно обдумать
> Как храним else/elseif