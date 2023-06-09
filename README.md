# Тестовое задание для компании "Лавивион"

> Оригинал файла лежит [тут](./test.docx).

## Вопросы

* Какой индекс будет у элемента "text" в следующем массиве `$array = array("one", "2", 9 => "plus", "text")` ?

> Индексом элемента 'text' будет номер 10 ... потому как перед ним идёт элемент 9 ... который задаёт значение индекса.

* Какое значение будет в переменной $_POST['color'] после отправки следующей формы?
```html
<form action="" method='post'>
    <input type='text'name="color" value="blue" />
    <input type='text'name="color" value="gren" />
    <input type='text'name="color" value="red" />
</form>
```
> в $_POST['color'] будет передано значение последнего элемента color  = «red» .. ибо оно перебивает все предыдущие значения для того же поля.

* Как правильно осуществить несколько запросов  базе данных?

```php
    mysqli_query($q1); mysqli_query($q2);
    mysqli_multi_query($q1, $q2);
    mysqli_query($q1, $q2);
```

> Правильным вызовом будет вызов в первой строке (подряд два вызова mysqli_query(); Выполнение остальных вариантов приведёт к ошибке..

### GIT

* Как в Git установить значение «Имя пользователя»?
```bash
    git config --global user.name
    git config user.name
    git user.name
```

> Установить значение «Имя пользователя» можно первой командой .. Вторая — отобразит значение сохранённое в настройке user.name. Третья - выдаст ошибку ..

* Возможен ли git pull, если в файле в рабочем каталоге есть незафиксированные изменения? Ответ нужно обосновать.

> git pull с незафиксированными изменениями возможен, если эти изменения не конфликтуют с файлами во внешней ветке, которые подлежат обновлению. В противном случае будет конфликт т pull не сработает

* Что делают команды «git reset –mixed» и «git merge –abort»?

> `git reset –mixed` = восстанавливает файлы в рабочей области (действие поумолчанию для команды reset). = происходит сброс индекса. `git merge –abort` = команда отменяет процесс слияния веток зашедший в конфликт. В результате файлы текущй ветки возвращаются в исходное состояние (до запуска команды git merge).


## Задача 1

Создайте форму, состав и внешний вид полей которой показан на скриншоте. Скрипт, который будет обрабатывать данные формы на сервере, должен проверять заполнение полей имени и фамилии и в случае ошибки выводить предупреждение и прерывать скрипт. Что касается аватарки, то скрипт должен либо вывести аватарку после имени и фамилии, либо сообщить о незагруженной аватарке (см. [скриншот](./imgs/job-1.png) задачи). Для получения имени, размера и временной папки для хранения загруженных файлов используйте суперглобальный массив `$_FILES`. Для перемещения загруженной аватарки в целевую папку используйте функцию `move_uploaded_file()` (в качестве целевой создайте папку avatars). Чтобы правильно указать путь к вставляемой на страницу аватарке, не забудьте начать его с http://localhost/test/. При желании можете добавить проверку загружаемой аватарки на соответствие типу изображения и т. д.

> Реализация этой задачи выполнена в файлах [code.php](./job1/code.php) и [index.php](./job1/index.php). Проверить реализацию можно запустив сборку докер-контейнеров, которая располагается в корне репозитария командой `docker compose up -d`. Далее в браузере перейти по [адресу](http://localhost:1381). Валидацию поля загрузки картинки организовали выставлением атрибута `accept` с указанием mime-типа "все картинки" (image/*)


## Задача 2.1 (Yii2)

Используя фреймворк Yii2 (basic):

* Реализовать сущности авторы и книги

* Реализовать административную часть
    a. CRUD операции для авторов и книг
    b. вывести список книг с обязательным указанием имени автора в списке
    c. вывести список авторов с указанием кол-ва книг

*    Реализовать публичную часть сайта с отображение авторов и их книг (простой вывод списка на странице)

*    Реализовать выдачу данных в формате json по RESTful протоколу отдельным контроллером
    * GET /api/v1/books/list получение списка книг с именем автора
    * GET /api/v1/books/by-id получение данных книги по id
    * POST /api/v1/books/update обновление данных книги
    * DELETE /api/v1/books/id удаление записи книги из бд

Результат представить ссылкой на репозиторий.
Желательно, в репозиторий залить пустой каркас приложения, а затем с внесёнными изменениями, чтобы можно было проследить diff.

## Задача 2.2 (Yii2)

* Методом login использует фреймворк и базу данных осуществите валидацию и вход на сайт.
* Проведите юнит тестирование написанного года.

> реалиазция этих задач располагается в каталге [job2](./job2). Просмотр доступен по [адресу](http://localhost:1382)