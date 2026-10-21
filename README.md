# Лабораторная работа №6

## Система контроля версий



**Студент:** Климина В. А.

**Группа:** 4515



## Цель работы



Изучить базовые возможности Git и получить опыт работы

с локальным и удалённым репозиториями.



## 1. Установка и настройка Git



Установлен Git. Настроены имя автора коммитов и email.



![Настройки Git](screenshots/01-git-settings.png)



## 2. Создание личного репозитория



Через Fork создана копия репозитория преподавателя Kurtyanik/LR6.



![Fork репозитория](screenshots/02-fork.png)



Репозиторий клонирован на компьютер.

Проверены адрес удалённого репозитория и список веток.



![Клонирование](screenshots/03-clone.png)



## 3. Получение изменений с GitHub



Через интерфейс GitHub создан файл github-note.txt.



![Файл на GitHub](screenshots/04-github-file.png)



Выполнена команда git pull origin master.

Проверено содержимое локального файла.



![Проверка синхронизации](screenshots/04-pull.png)

## 4. Просмотр истории веток



Просмотрена история коммитов веток master и branch1.

Также выведен общий граф истории репозитория.



![История веток](screenshots/05-history.png)



## 5. Просмотр последних изменений



Командой git show HEAD просмотрен последний коммит.

Командой git diff master origin/branch1 изучены различия веток.



![Просмотр изменений](screenshots/06-changes.png)



## 6. Слияние веток и разрешение конфликта



Создана локальная ветка branch1 на основе origin/branch1.

После переключения в master выполнена команда git merge branch1.



В файле mergefile.txt возник конфликт, поскольку в обеих ветках

был изменён один и тот же участок текста.



![Конфликт слияния](screenshots/07-conflict.png)



Файл открыт в Блокноте. Вручную выбран итоговый текст,

удалены маркеры конфликта и сохранены изменения.



![Исправленный файл](screenshots/08-conflict-resolved.png)



Исправленный файл добавлен командой git add mergefile.txt.

Слияние завершено коммитом.

После успешного слияния локальная ветка branch1 удалена

командой git branch -d branch1.



![Завершение слияния и удаление ветки](screenshots/09-merge-and-delete-branch.png)



## 7. Создание нескольких коммитов



В ветке master создан файл practice.txt.

Последовательно выполнены три изменения с отдельными коммитами:



1. Создан файл со строкой First line.

2. Добавлена строка Second line.

3. Добавлена строка Temporary line.



![Последовательные коммиты](screenshots/11-commits.png)



## 8. Откат коммита



Командой git revert --no-edit HEAD отменено добавление

строки Temporary line.



Создан отдельный коммит отмены. Исходный коммит остался

в истории. В файле сохранились строки First line и Second line.



![Откат коммита](screenshots/12-revert.png)



## 9. Создание ветки отчёта



Командой git switch -c otchet создана отдельная ветка otchet.

В ней оформляется отчёт README.md и сохраняются скриншоты.

В процессе оформления выполняются промежуточные коммиты.


## 10. Журнал команд

Основные выполненные команды без результатов их выполнения:

```bash
git --version
git config --get user.name
git config --get user.email
git clone https://github.com/lenerally/LR6.git
cd LR6
git remote -v
git branch -a
git pull origin master
cat github-note.txt
git log master --oneline
git log origin/branch1 --oneline
git log --all --graph --oneline --decorate
git show HEAD
git diff master origin/branch1
git switch -c branch1 --track origin/branch1
git switch master
git status
git merge branch1
notepad mergefile.txt
git add mergefile.txt
git commit -m "Объединены master и branch1, конфликт разрешён"
git log --graph --oneline --decorate -8
git branch -d branch1
git branch
echo "First line" > practice.txt
git add practice.txt
git commit -m "Создан учебный файл"
echo "Second line" >> practice.txt
git add practice.txt
git commit -m "Добавлена вторая строка"
echo "Temporary line" >> practice.txt
git add practice.txt
git commit -m "Добавлена временная строка"
cat practice.txt
git log --oneline -5
git revert --no-edit HEAD
cat practice.txt
git log --oneline -6
git switch -c otchet
notepad README.md
mv screenshots~ screenshots
git add README.md screenshots/
git commit -m "Добавлены настройка Git и подготовка репозитория в отчёт"
git add README.md
git commit -m "Добавлены история веток, слияние и откат в отчёт"
sed -i 's/\\//g' README.md
git add README.md
git commit -m "Исправлено Markdown-оформление отчёта"
git log --all --date=short --pretty=format:"%h | %ad | %an | %s"
```

## 11. Форматированная история коммитов

```text
854dd57 | 2026-10-21 | 4515 Климина В. А. | Исправлено Markdown-оформление отчёта
92bb40f | 2026-10-21 | 4515 Климина В. А. | Добавлены история веток, слияние и откат в отчёт
ef88f71 | 2026-10-21 | 4515 Климина В. А. | Добавлены настройка Git и подготовка репозитория в отчёт
23032ba | 2026-10-21 | 4515 Климина В. А. | Revert "Добавлена временная строка"
9acf966 | 2026-10-21 | 4515 Климина В. А. | Добавлена временная строка
f75a841 | 2026-10-21 | 4515 Климина В. А. | Добавлена вторая строка
19f8b1b | 2026-10-21 | 4515 Климина В. А. | Создан учебный файл
4bed0a4 | 2026-10-21 | 4515 Климина В. А. | Объединены master и branch1, конфликт разрешён
c672fa7 | 2026-10-21 | lenerally | Create github-note.txt
921f53b | 2020-11-21 | Kurtyanik | Обновление информации
0f9f50d | 2020-11-21 | Kurtyanik | Заполнил файл
c08a654 | 2020-11-21 | Kurtyanik | Файл создан пустым
3c6e913 | 2020-11-21 | Kurtyanik | Initial commit
```

## Вывод

В ходе лабораторной работы освоены настройка Git, создание Fork,
клонирование репозитория и получение изменений с GitHub.
Просмотрены история коммитов и различия между ветками.
Выполнены слияние, ручное разрешение конфликта и удаление
побочной ветки. Созданы последовательные коммиты и выполнен
откат с сохранением истории. Отчёт оформлен в Markdown
в отдельной ветке otchet.

