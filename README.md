# Практика

## Краткое описание порядка действий, команды для репозитория

1. Создадим папку с проектом на локальном компьютере.```mkdir my_project```
2. Перейдем в созданную папку.```cd my_project```
3. Инициализируем git.```git init```
4. Зададим глобальные параметры.```git config --global user.name "Maksim Monakhov"```
5. Создадим файл.```touch README.md```
6. Поместим в "корзину".```git add --all```
7. Синхронизируемся с гитом.```git remote add origin git@github.com:MaksimMonakhov/practic_1.git```
8. Проверь, что репозитории действительно связались ```git remote -v```
9. Коммитим.```git commit -m 'Практика 1'```
10. Пушим.```git push -u origin master```
    Далее```git push```

Далее возможно просто изменять файл и...
```
git add --all
git commit -m 'Изменения'
git push
```

## Просмотр информации о коммитах
```git log``` (от англ. log, «журнал [записей]») — выведи подробную историю коммитов;

```git log --oneline``` (от англ. log, «журнал [записей]» + oneline, «одной строкой») — покажи краткую информацию о коммитах: сокращённый хеш и сообщение.

## Просмотр состояния файлов
```git status``` (от англ. status, «статус», «состояние») — покажи текущее состояние репозитория.

## Вставляем mermaid

### Простой mermaid

```mermaid
graph LR;
  untracked -- "git add" --> staged;
  staged    -- "???"     --> tracked/comitted;

%% стрелка без текста для примера: 
  A --> B;
``` 

### Сложнее

```mermaid
sequenceDiagram
    participant dotcom
    participant iframe
    participant viewscreen
    dotcom->>iframe: loads html w/ iframe url
    iframe->>viewscreen: request template
    viewscreen->>iframe: html & javascript
    iframe->>dotcom: iframe ready
    dotcom->>iframe: set mermaid data on iframe
    iframe->>iframe: render mermaid
```

```mermaid
  flowchart LR;
      A[CI MULTI CHAPTCHA]-->B{Select captcha service by developer?};
      classDef green color:#022e1f,fill:#00f500;
      classDef red color:#022e1f,fill:#f11111;
      classDef white color:#022e1f,fill:#fff;
      classDef black color:#fff,fill:#000;
      B--YES-->C[How to use?]:::green;
      
      C-->U[I choose recaptcha.]:::green;
      U--Views-->Q["echo CIMC_JS('recaptcha');\n echo CIMC_HTML(['captcha_name'=>'recaptcha']);"]:::green;
      U--Controller-->W["CIMC_RULE('recaptcha');"]:::green;
      
      C-->I[I choose arcaptcha.]:::white;
      I--Views-->O["echo CIMC_JS('arcaptcha');\n echo CIMC_HTML(['captcha_name'=>'arcaptcha']);"]:::white;
      I--Controller-->P["CIMC_RULE('arcaptcha');"]:::white;
      
      C-->X[I choose bibot.]:::red;
      X--Views-->V["echo CIMC_JS('bibot');\n echo CIMC_HTML(['captcha_name'=>'bibot']);"]:::red;
      X--Controller-->N["CIMC_RULE('bibot');"]:::red;
      
      B--NO-->D[How to use?]:::black;
      D---Views:::black-->F["echo CIMC_JS('randomcaptcha');\n echo CIMC_HTML(['captcha_name'=>'randomcaptcha']);"]:::black; 
      D---Controller:::black-->T["CIMC_RULE('archaptcha,recaptcha,bibot');"]:::black;
```

## Добавление изменений в последний коммит
```git commit --amend --no-edit``` (от англ. amend, «исправить») — добавь изменения к последнему коммиту и оставь сообщение прежним;

```git commit --amend -m "Новое сообщение"``` — измени сообщение к последнему коммиту на Новое сообщение.

## Сделать шаг назад, если что-то пошло не так

- Команда ```git restore --staged <file>``` переведёт файл из staged обратно в modified или untracked. Эта команда уберёт файл из списка на коммит, и он вернётся в состояние  untracked.
- Команда ```git reset --hard <commit hash>``` «откатит» историю до коммита с хешем <hash>. Более поздние коммиты потеряются!
- Команда ```git restore <file>``` «откатит» изменения в файле до последней сохранённой (в коммите или в staging) версии.

## Просмотр изменений в файлах

После коммита внесли изменения в файл, посмотреть изменения - ```git diff```

```git diff a9928ab 11bada1``` — выведи разницу между двумя коммитами;

После ```git add``` посмотреть изменения - ```git diff --staged```

# Шпаргалка. Работа с ветками

В этой шпаргалке мы собрали все ключевые команды модуля — они наверняка пригодятся вам в реальной работе с ветками!

## Клонирование чужого репозитория

```git clone git@github.com:YandexPraktikum/first-project.git``` (от англ. clone, «клон», «копия») — склонируй репозиторий с URL first-project.git из аккаунта YandexPraktikum на мой локальный компьютер.

## Создание веток

- ```git branch feature/the-finest-branch``` (от англ. branch, «ветка») — создай ветку от текущей с названием feature/the-finest-branch;
- ```git checkout -b feature/the-finest-branch``` — создай ветку feature/the-finest-branch и сразу переключись на неё.

## Навигация по веткам

- ```git branch``` (от англ. branch, «ветка») — покажи, какие есть ветки в репозитории и в какой из них я нахожусь (текущая ветка будет отмечена символом *);
- ```git branch -a``` — покажи все известные ветки, как локальные (в локальном репозитории), так и удалённые (в origin, или на GitHub).
- ```git checkout feature/br``` — переключись на ветку feature/br.

## Сравнение веток

- ```git diff main HEAD``` (от англ. difference, «отличие», «разница») — покажи разницу между веткой main и указателем на HEAD;
- ```git diff HEAD~2 HEAD``` — покажи разницу между тем коммитом, который был два коммита назад, и текущим.

## Удаление веток

- ```git branch -d br-name``` — удали ветку br-name, но только если она является частью main;
- ```git branch -D br-name``` — удали ветку br-name, даже если она не объединена с main.

## Слияние веток

```git merge main``` (от англ. merge, «сливать», «поглощать») — объедини ветку main с текущей активной веткой. 

## Работа с удалённым репозиторием

- ```git push -u origin my-branch``` (от англ. push, «толкнуть», «протолкнуть») — отправь новую ветку my-branch в удалённый репозиторий и свяжи локальную ветку с удалённой, чтобы при дополнительных коммитах можно было писать просто git push без -u;
- ```git push my-branch``` — отправь дополнительные изменения в ветку my-branch, которая уже существует в удалённом репозитории;
- ```git pull``` (от англ. pull, «вытянуть») — подтяни изменения текущей ветки из удалённого репозитория.