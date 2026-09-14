<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,20&height=180&section=header&text=Blogicum&fontSize=70&fontAlignY=35&desc=Django%20Blog%20Platform%20%7C%20Yandex%20Practicum&descAlignY=55&descSize=18" alt="Blogicum Banner" width="100%">

<img src="https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white" alt="Python">
<img src="https://img.shields.io/badge/Django-3.2.16-092E20?style=for-the-badge&logo=django&logoColor=white" alt="Django">
<img src="https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white" alt="SQLite">
<img src="https://img.shields.io/badge/Bootstrap-5.0.1-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white" alt="Bootstrap">

<br>

<img src="https://img.shields.io/badge/Pytest-7.1.3-0A9EDC?style=for-the-badge&logo=pytest&logoColor=white" alt="Pytest">
<img src="https://img.shields.io/badge/pytest--django-4.5.2-0A9EDC?style=for-the-badge&logo=pytest&logoColor=white" alt="pytest-django">
<img src="https://img.shields.io/badge/django--bootstrap5-22.2-7952B3?style=for-the-badge&logo=django&logoColor=white" alt="django-bootstrap5">
<img src="https://img.shields.io/badge/Flake8-5.0.4-yellow?style=for-the-badge&logo=python&logoColor=white" alt="Flake8">

<br>

<img src="https://img.shields.io/badge/Pillow-9.3.0-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Pillow">
<img src="https://img.shields.io/badge/mixer-7.2.2-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="mixer">
<img src="https://img.shields.io/badge/Faker-12.0.1-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Faker">
<img src="https://img.shields.io/badge/BeautifulSoup4-4.11.2-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="BeautifulSoup4">

<br><br>

<h2>📝 Blogicum — блог-платформа на Django</h2>

<p>
  <b>Учебный проект в рамках курса «Python-разработчик» от Яндекс Практикума</b>
</p>

</div>

---

## 📖 О проекте

**Blogicum** — учебная блог-платформа, разработанная на Django.

В четвёртом спринте проект получил полноценную систему пользователей и взаимодействия с публикациями. Помимо просмотра постов, категорий и локаций, пользователи могут регистрироваться, авторизовываться, менять и восстанавливать пароль, оставлять комментарии и редактировать собственные публикации.

Также проект был дополнен расширенным набором автоматических тестов, обработкой ошибок и отправкой писем через Django.

### 🎯 Что добавлено в Sprint 4

* 👤 Регистрация и авторизация пользователей.
* 🔐 Изменение пароля.
* 📧 Восстановление пароля через email.
* 💬 Добавление и редактирование комментариев.
* ✏️ Редактирование собственных публикаций.
* 📩 Работа с отправкой электронных писем.
* 🚫 Обработка страниц ошибок.
* 🧪 Расширенное автоматическое тестирование.
* 🎨 Использование `django-bootstrap5` для оформления форм.

---

## ✨ Основные возможности

### 📝 Работа с публикациями

* Просмотр ленты публикаций.
* Просмотр отдельной публикации.
* Фильтрация постов по категориям.
* Отображение автора, даты публикации и локации.
* Работа с опубликованными и актуальными записями.
* Редактирование собственных публикаций.

### 🗂️ Категории и локации

Публикации связаны с категориями и локациями через Django ORM.

Основные модели проекта:

```text
Category
Location
Post
```

### 👤 Пользователи

Для работы с пользователями используется стандартная система аутентификации Django:

```python
django.contrib.auth
```

Реализованы:

* регистрация нового пользователя;
* вход в аккаунт;
* выход из аккаунта;
* изменение пароля;
* восстановление пароля;
* подтверждение нового пароля;
* перенаправление пользователя после авторизации через параметр `next`.

### 💬 Комментарии

Авторизованные пользователи могут взаимодействовать с комментариями публикаций.

Реализована возможность:

* добавлять комментарии;
* редактировать собственные комментарии;
* работать с комментариями в рамках конкретной публикации.

### ✏️ Редактирование публикаций

Для пользователей предусмотрена работа с собственными публикациями.

Редактирование доступно автору соответствующей записи.

---

## 🔑 Аутентификация

Для стандартных операций с пользователями используются шаблоны Django authentication.

Основные страницы находятся в директории:

```text
templates/
└── registration/
    ├── login.html
    ├── logged_out.html
    ├── registration_form.html
    ├── password_change_form.html
    ├── password_change_done.html
    ├── password_reset_form.html
    ├── password_reset_done.html
    ├── password_reset_confirm.html
    └── password_reset_complete.html
```

### 🔐 Авторизация

При входе пользователь может быть перенаправлен на страницу, с которой он пришёл.

Для этого используется параметр:

```text
next
```

### 🔑 Изменение пароля

Авторизованный пользователь может изменить свой пароль через соответствующую форму.

После успешного изменения отображается отдельная страница подтверждения операции.

### 📧 Восстановление пароля

Реализован стандартный Django-процесс восстановления пароля:

```text
Запрос восстановления
        ↓
Ввод email
        ↓
Отправка письма
        ↓
Переход по ссылке
        ↓
Установка нового пароля
        ↓
Подтверждение операции
```

Для учебного проекта используется консольный email backend.

Содержимое письма с инструкцией по восстановлению пароля выводится непосредственно в терминал, поэтому для проверки функциональности не требуется настоящий почтовый сервер.

---

## 🎨 Формы и интерфейс

Для оформления Django-форм используется библиотека:

```text
django-bootstrap5
```

Формы интегрированы с Bootstrap и отображаются в едином стиле с остальными элементами интерфейса.

Для визуального оформления используются Bootstrap-карточки и стандартные компоненты Bootstrap.

---

## 🎨 Система шаблонов

Проект использует наследование Django-шаблонов для уменьшения дублирования HTML-кода.

Базовый шаблон:

```text
base.html
```

На его основе строятся страницы приложения.

```text
base.html
    ├── blog/
    │   ├── index.html
    │   ├── category.html
    │   └── detail.html
    │
    ├── pages/
    │   ├── about.html
    │   └── rules.html
    │
    └── registration/
        ├── login.html
        ├── registration_form.html
        └── password_*.html
```

Также используются переиспользуемые компоненты:

```text
includes/
├── header.html
├── footer.html
├── post_card.html
└── category_link.html
```

---

## 🔗 Namespace-маршрутизация

Для организации URL используются именованные маршруты и пространства имён.

Основные маршруты:

```text
blog:index
blog:post_detail
blog:category_posts

pages:about
pages:rules
```

Это позволяет обращаться к URL через их имена и уменьшает зависимость кода от конкретных путей.

---

## 🧪 Расширенное тестирование

В четвёртом спринте значительно расширен набор автоматических тестов.

Для тестирования используется:

* **Pytest**
* **pytest-django**
* **mixer**
* **Faker**
* **BeautifulSoup4**

### 📂 Структура тестов

```text
tests/
├── adapters/
├── fixtures/
├── form/
├── conftest.py
├── test_comment.py
├── test_content.py
├── test_edit.py
├── test_emails.py
├── test_err_pages.py
├── test_post.py
├── test_static_pages.py
└── test_users.py
```

### 🔍 Основные направления тестирования

| Раздел                   | Что проверяется                            |
| :----------------------- | :----------------------------------------- |
| **Пользователи**         | Регистрация, авторизация и работа аккаунта |
| **Формы**                | Корректность пользовательского ввода       |
| **Публикации**           | Отображение и работа с постами             |
| **Комментарии**          | Создание и редактирование комментариев     |
| **Редактирование**       | Возможность изменения собственных данных   |
| **Email**                | Отправка писем для восстановления пароля   |
| **Ошибки**               | Корректная обработка страниц ошибок        |
| **Статические страницы** | Работа страниц проекта                     |

Запуск полного набора тестов:

```bash
pytest
```

---

## 🗃️ Данные проекта

Для первоначального заполнения базы данных используется дамп:

```text
db.json
```

Загрузка данных:

```bash
python manage.py loaddata db.json
```

После применения миграций и загрузки фикстур проект готов к запуску.

---

## 🛠️ Технологический стек

| Технология            | Версия | Назначение                    |
| :-------------------- | :----- | :---------------------------- |
| **Python**            | 3.10+  | Основной язык разработки      |
| **Django**            | 3.2.16 | Веб-фреймворк                 |
| **SQLite**            | —      | База данных                   |
| **Bootstrap**         | 5.0.1  | Стилизация интерфейса         |
| **django-bootstrap5** | 22.2   | Bootstrap-интеграция с Django |
| **Pytest**            | 7.1.3  | Автоматическое тестирование   |
| **pytest-django**     | 4.5.2  | Интеграция Pytest с Django    |
| **Pillow**            | 9.3.0  | Работа с изображениями        |
| **mixer**             | 7.2.2  | Генерация тестовых данных     |
| **Faker**             | 12.0.1 | Генерация фиктивных данных    |
| **BeautifulSoup4**    | 4.11.2 | Анализ HTML в тестах          |
| **Flake8**            | 5.0.4  | Проверка качества кода        |

### 🔧 Плагины Flake8

В проекте также используются:

```text
flake8-docstrings
pep8-naming
```

Они позволяют дополнительно контролировать документацию и соответствие соглашениям именования Python-кода.

---

## 📂 Структура проекта

```text
django_sprint4/
├── blog/
│   ├── migrations/
│   ├── admin.py
│   ├── apps.py
│   ├── forms.py
│   ├── models.py
│   ├── urls.py
│   └── views.py
│
├── pages/
│   ├── apps.py
│   ├── urls.py
│   └── views.py
│
├── templates/
│   ├── blog/
│   ├── includes/
│   ├── pages/
│   │
│   └── registration/
│       ├── login.html
│       ├── logged_out.html
│       ├── registration_form.html
│       ├── password_change_form.html
│       ├── password_change_done.html
│       ├── password_reset_form.html
│       ├── password_reset_done.html
│       ├── password_reset_confirm.html
│       └── password_reset_complete.html
│
├── tests/
│   ├── adapters/
│   ├── fixtures/
│   ├── form/
│   ├── conftest.py
│   ├── test_comment.py
│   ├── test_content.py
│   ├── test_edit.py
│   ├── test_emails.py
│   ├── test_err_pages.py
│   ├── test_post.py
│   ├── test_static_pages.py
│   └── test_users.py
│
├── .gitignore
├── LICENSE
├── README.md
├── db.json
├── manage.py
├── pytest.ini
├── requirements.txt
└── setup.cfg
```

---

## 🚀 Запуск проекта

### 📋 Требования

Перед началом работы убедитесь, что установлены:

* **Python 3.10+**
* **pip**
* **Git**

<details>
<summary><b>1. Клонирование репозитория</b></summary>

```bash
git clone https://github.com/DarkSwordman999/django_sprint4.git
cd django_sprint4
```

</details>

<details>
<summary><b>2. Создание виртуального окружения</b></summary>

```bash
python -m venv venv
```

**Windows:**

```bash
venv\Scripts\activate
```

**macOS / Linux:**

```bash
source venv/bin/activate
```

</details>

<details>
<summary><b>3. Установка зависимостей</b></summary>

```bash
pip install -r requirements.txt
```

</details>

<details>
<summary><b>4. Применение миграций</b></summary>

```bash
python manage.py migrate
```

</details>

<details>
<summary><b>5. Загрузка тестовых данных</b></summary>

```bash
python manage.py loaddata db.json
```

</details>

<details>
<summary><b>6. Запуск сервера разработки</b></summary>

```bash
python manage.py runserver
```

После запуска приложение будет доступно по адресу:

```text
http://127.0.0.1:8000/
```

Административная панель:

```text
http://127.0.0.1:8000/admin/
```

</details>

---

## 🧪 Запуск тестов

Для запуска полного набора автоматических тестов выполните:

```bash
pytest
```

Для более подробного вывода:

```bash
pytest -v
```

Конфигурация Pytest находится в:

```text
pytest.ini
```

---

## 🧹 Линтинг

Для проверки качества Python-кода используется **Flake8**.

Конфигурация находится в:

```text
setup.cfg
```

Запуск проверки:

```bash
flake8 .
```

В проекте дополнительно используются плагины:

```text
flake8-docstrings
pep8-naming
```

---

## 📧 Проверка восстановления пароля

Так как проект использует консольный email backend, письма не отправляются на реальный почтовый ящик.

Чтобы проверить восстановление пароля:

1. Откройте страницу восстановления пароля.
2. Укажите email пользователя.
3. Отправьте форму.
4. Перейдите в терминал, где запущен Django.
5. Найдите сгенерированное письмо.
6. Скопируйте ссылку восстановления.
7. Откройте её в браузере.
8. Установите новый пароль.

Такой подход позволяет полностью проверить механизм восстановления пароля без настройки внешнего SMTP-сервера.

---

## 🚧 В разработке

Проект является частью учебной серии спринтов Яндекс Практикума.

На текущем этапе реализованы основные механизмы блог-платформы, включая:

* публикации;
* категории;
* локации;
* пользователей;
* аутентификацию;
* восстановление пароля;
* комментарии;
* редактирование;
* обработку ошибок;
* автоматические тесты.

Дальнейшее развитие проекта зависит от следующих этапов курса.

---

## 📄 Лицензия

Проект распространяется в соответствии с лицензией, указанной в файле [`LICENSE`](./LICENSE).

---

## 👤 Автор

<div align="center">

### DarkSwordman999

<a href="https://github.com/DarkSwordman999">
  <img src="https://img.shields.io/badge/GitHub-DarkSwordman999-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
</a>

</div>

---

<div align="center">

### ⭐ Понравился проект?

Если **Blogicum** оказался полезным или интересным,
**поставьте ⭐ репозиторию на GitHub** — это лучшая поддержка проекта!

<a href="https://github.com/DarkSwordman999/django_sprint4">
  <img src="https://img.shields.io/badge/⭐%20Star%20repository-181717?style=for-the-badge&logo=github&logoColor=white" alt="Star repository">
</a>

<br><br>

<i>Спасибо за интерес к проекту! 🚀</i>

</div>

---

<div align="center">

### 🎓 Yandex Practicum

**Проект создан в рамках курса «Python-разработчик» от Яндекс Практикума.**

<i>Учебный проект. Создан в образовательных целях.</i>

</div>
