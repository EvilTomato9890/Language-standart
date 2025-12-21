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
const folder = "public/AST/Operators";
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

---
## Свойства и функционал 

### Функционал ASM
Какой функционал выполняет

>**Вид в ASM**
> ```
> Какой-то код на ASM
> Еще какой-то код на ASM
> ```

### Свойства
- *Какое-то свойство этого оператор, к примеру ассоциативность*

---

## Формат узла

> [!info] Обозначения
> **NC** (*no child*) — нулевой ребенок.
> **...** — нет необходимости в данных.

| child | имя | класс | группа| примечание |
|:-----:|:---:|:-----:|:-----:|:--------:|
| left  | ... | Какой-то класс | ... | ... |
| right | Какая-то конкретная операция | ... | Какая-то группа | ...|

**Иные требования к детям:**
- *Какое-то требование к детям, к примеру существование*

---

### Примеры

> Минимальный пример:
> ```
> Какой-то простой код
> ```


> Стандартный пример:
> ```
> Какой-то нормальный код
> ```

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

| File                                                  | Ссылается на                                                                                                                                                                                           | Ссылаются на него                                                        |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| [[Templates/operator_template.md\|operator_template]] | <ul><li>[[Templates/operator_template.md\|operator_template]]</li><li>[[Templates/operator_template.md\|operator_template]]</li><li>[[Templates/operator_template.md\|operator_template]]</li></ul> | <ul><li>[[Templates/operator_template.md\|operator_template]]</li></ul> |

%% DATAVIEW_PUBLISHER: end %%

>[!question] Что нужно обдумать
> Как дальше жить