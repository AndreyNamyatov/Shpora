## **Файл README.md**

Как правило, в `README.md` проекта можно найти следующую информацию:

1. Название проекта и его краткое описание: кем создан, для чего, какие решает задачи и какие закрывает проблемы.
2. Технологии, которые применяются в проекте. В чём его отличие от аналогичных.
3. Документация проекта — подробная инструкция о том, что представляет собой проект.
4. Планы проекта, если они есть.

Преимущество `README.md` в том, что средства командной работы (такие, как GitHub) могут отображать его содержимое в браузере в виде удобной разметки. Для этого нужно не просто залить текст, но и настроить шрифт, заголовки и отступы с помощью markdown. **Маркда́ун** — это специальный язык разметки. Он позволяет красиво отформатировать текстовый документ.

**Заголовки, абзацы и перенос**

- **Заголовки** разных уровней создают решётками.

```bash
# H1 — заголовок первого уровня, самый большой
## H2 — заголовок второго уровня, поменьше
### H3
#### H4
##### H5
###### H6 — заголовок шестого уровня, самый маленький
```

- Можно добавить **черту под заголовком или абзацем**.

```bash
#### Заголовок 4

Текст над чертой

---

Текст под чертой
```

- Чтобы сделать **разрыв строки**, нужно поставить два пробела (в примере ниже они обозначены точками `⋅⋅`) или сочетание символов `<br>`.

```bash

Текст до переноса⋅⋅  
Текст после переноса <br>
Текст после второго переноса
```

- Чтобы начать **новый параграф**, в конце предыдущей строки должно стоять два символа переноса. Для этого нужно нажать `Enter` два раза.

```markdown
line

another line
```

Если сделать один перенос строки, как в примере ниже, и не поставить два пробела, текст сольётся в одну строку.

```bash
line 
another line
```

**Выделение текста**

- Чтобы выделить текст **курсивом** (`текст*`), его заключают в звёздочки (астериски) или нижние подчёркивания.

```markdown
Курсив — это *звёздочки* или _подчёркивания_.
```

- Чтобы выделить текст **полужирным шрифтом** (`*текст**`), его окружают двойными звёздочками или двойными нижними подчёркиваниями.

```markdown
Полужирный шрифт — двойные **звёздочки** или двойные __подчёркивания__.
Можно совместить выделение **звёздочки и _подчёркивания_**.
```

- Чтобы **зачеркнуть текст** (`~~текст~~`), его окружают двойными волнистыми линиями — тильдами.

```markdown
~~Зачёркнутый текст.~~
```

### Списки

- Для оформления **нумерованного списка** достаточно поставить в начало строки цифры с точкой.

```markdown
1. Первый пункт нумерованного списка.
2. Второй пункт.
```

- **Ненумерованный список** создаётся звёздочкой с пробелом в начале строки либо дефисом с пробелом.

```markdown
* первый пункт ненумерованного списка;
* второй пункт ненумерованного списка

- первый пункт ненумерованного списка;
- второй пункт ненумерованного списка
```

### **Ссылки**

- Чтобы сделать ссылкой часть текста, его заключают в квадратные скобки, а затем указывают нужный адрес в круглых скобках.

```markdown
[Яндекс](https://www.yandex.ru)
```

- Также можно добавить ссылке **тайтл** (от англ *title* — «название», «заголовок»). Тайтл — это всплывающая подсказка, которая появляется при наведении мыши на ссылку. Тайтл нужно заключить в кавычки и указать внутри скобок после адреса.

```markdown
[Яндекс](https://www.yandex.ru "Я Yandex!")
```

### **Код**

Чтобы оформить текст как код, нужно окружить его тройками косых кавычек — грависов. После первой тройки грависов указывают язык программирования, на котором написан код. В маркдауне есть поддержка синтаксиса почти всех популярных языков и инструментов.

```markdown
```bash
ls - la
```
```html
<h1>А я просто текст</h1>
```

# HEAD — всему голова

При вызове команды `git log` вы также могли заметить надпись `(HEAD -> master)` после хеша одного из коммитов. В этом уроке расскажем, что она означает.

### Файл `HEAD`

Файл `HEAD` (англ. «голова», «головной») — один из служебных файлов папки `.git`. Он указывает на коммит, который сделан последним (то есть на самый новый).

Внутри `HEAD` — ссылка на служебный файл: `refs/heads/master` (или `refs/heads/main` в зависимости от названия ветки). Если заглянуть в этот файл, можно увидеть хеш последнего коммита.

Супер! Папка `.git` содержит много непонятных файлов — об одном из них мы рассказали в этом уроке. Подытожим:

- В числе прочих файлов в папке `.git` есть служебный файл `HEAD`. Он указывает на самый свежий коммит.
- Вместо хеша последнего коммита можно написать слово `HEAD` — Git вас поймёт.

## **Статусы файлов в Git**

### Статусы `untracked`/`tracked`, `staged` и `modified`

Одна из ключевых задач Git — отслеживать изменения файлов в репозитории. Для этого каждый файл помечается каким-либо статусом. Рассмотрим основные.

- **`untracked`** (англ. «неотслеживаемый»)
Мы говорили, что новые файлы в Git-репозитории помечаются как `untracked`, то есть неотслеживаемые. Git «видит», что такой файл существует, но не следит за изменениями в нём. У `untracked`файла нет предыдущих версий, зафиксированных в коммитах или через команду `git add`.
- **`staged`** (англ. «подготовленный»)
    
    После выполнения команды `git add` файл попадает в **staging area** (от англ. *stage* — «сцена», «этап [процесса]» и *area* — «область»), то есть в список файлов, которые войдут в коммит. В этот момент файл находится в состоянии `staged`.
    
    💡 **Staging area, index и cache**
    
    Staging area также называют **index** (англ. «каталог») или **cache** (англ. «кеш»), а состояние файла `staged` иногда называют `indexed` или `cached`.
    
    Все три варианта могут встречаться в документации и в качестве флагов команд Git. А также в интернете — например, в вопросах и ответах [на сайте Stack Overflow](https://stackoverflow.com/).
    
    - **`tracked`** (англ. «отслеживаемый»)
    Состояние `tracked` — это противоположность `untracked`. Оно довольно широкое по смыслу: в него попадают файлы, которые уже были зафиксированы с помощью `git commit`, а также файлы, которые были добавлены в staging area командой `git add`. То есть все файлы, в которых Git так или иначе отслеживает изменения.
    - **`modified`** (англ. «изменённый»)
    Состояние `modified` означает, что Git сравнил содержимое файла с последней сохранённой версией и нашёл отличия. Например, файл был закоммичен и после этого изменён.
    
    💡 Для файлов в состояниях `staged` и `modified` обычно не указывают, что они также `tracked`, потому что это состояние подразумевается.

```mermaid 
graph TD;
	A[Untracked] -- git add --> B[staged];
	B -- git commit --> C[tracked] --> D[modified];
	D -- git add --> B;
	B --> D;
```