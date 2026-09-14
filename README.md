<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,20&height=180&section=header&text=Kittygram&fontSize=70&fontAlignY=35&desc=Fullstack%20App%20in%20Docker%20%7C%20CI%2FCD%20%7C%20Yandex%20Practicum&descAlignY=55&descSize=18" alt="Banner" width="100%">

<img src="https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white" alt="Python">
<img src="https://img.shields.io/badge/Django-3.2.3-092E20?style=for-the-badge&logo=django&logoColor=white" alt="Django">
<img src="https://img.shields.io/badge/DRF-3.12.4-092E20?style=for-the-badge&logo=django&logoColor=white" alt="Django REST Framework">
<img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker">
<img src="https://img.shields.io/badge/Nginx-1.22.1-009639?style=for-the-badge&logo=nginx&logoColor=white" alt="Nginx">

<br>

<img src="https://img.shields.io/badge/PostgreSQL-13-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL">
<img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React">
<img src="https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white" alt="GitHub Actions">
<img src="https://img.shields.io/badge/Yandex-Practicum-red?style=for-the-badge&logo=yandex&logoColor=white" alt="Yandex Practicum">

<br><br>

<h2>🐱 Kittygram — приложение для любителей котиков</h2>

<p><b>Финальный проект курса «Python-разработчик» от Яндекс Практикума</b></p>

</div>

<hr>

<h2>📖 О проекте</h2>

<p><b>Kittygram</b> — веб-приложение, где можно делиться фотографиями своих котиков, указывать их достижения и породы. Проект состоит из трёх частей:</p>

<ul>
  <li><b>Backend</b> — Django + DRF. API для работы с котиками, достижениями и пользователями.</li>
  <li><b>Frontend</b> — SPA на React.</li>
  <li><b>Gateway</b> — Nginx 1.22.1: раздача статики фронтенда.</li>
</ul>

<p>Все сервисы упакованы в <b>Docker-контейнеры</b>, оркестрация через <code>docker-compose</code>. Настроен CI/CD через GitHub Actions.</p>

<hr>

<h2>✅ Что реализовано</h2>

<ul>
  <li>Backend на Django + DRF: модели <code>Achievement</code>, <code>Cat</code>, <code>AchievementCat</code>.</li>
  <li>API для котиков и достижений (<code>CatViewSet</code>, <code>AchievementViewSet</code>).</li>
  <li>Аутентификация и регистрация через <code>djoser</code>.</li>
  <li>Валидация цвета кота через <code>webcolors</code>.</li>
  <li>Frontend на React, сборка в статику через <code>npm run build</code>.</li>
  <li>Nginx-контейнер, который раздаёт статику фронтенда.</li>
  <li>Docker Compose: сервисы <code>db</code>, <code>backend</code>, <code>frontend</code>, <code>gateway</code>.</li>
  <li>Переменные окружения для БД (<code>.env.example</code>).</li>
  <li>Тесты (<code>pytest</code>) для бэкенда.</li>
</ul>

<hr>

<h2>🚧 Что в разработке</h2>

<ul>
  <li>Проксирование <code>/api/</code> и <code>/admin/</code> на backend через Nginx (сейчас строки <code>proxy_pass</code> закомментированы).</li>
  <li>Вынос настроек Django (<code>SECRET_KEY</code>, <code>DEBUG</code>, <code>ALLOWED_HOSTS</code>) в переменные окружения.</li>
  <li>CI/CD на GitHub Actions: тестирование, сборка и деплой.</li>
  <li>Уведомления о результатах в Telegram.</li>
</ul>

<hr>

<h2>🗃️ Модели данных</h2>

<div align="center">

<table>
  <thead>
    <tr>
      <th align="left">Модель</th>
      <th align="left">Поля</th>
      <th align="left">Описание</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>Achievement</b></td>
      <td><code>name</code></td>
      <td>Достижение котика</td>
    </tr>
    <tr>
      <td><b>Cat</b></td>
      <td><code>name</code>, <code>color</code>, <code>birth_year</code>, <code>owner</code>, <code>achievements</code>, <code>image</code></td>
      <td>Котик с привязкой к владельцу</td>
    </tr>
    <tr>
      <td><b>AchievementCat</b></td>
      <td><code>achievement</code>, <code>cat</code></td>
      <td>Промежуточная модель M2M</td>
    </tr>
  </tbody>
</table>

</div>

<p>Связь <code>Cat</code> ↔ <code>Achievement</code> реализована через <code>ManyToManyField</code> с промежуточной моделью <code>AchievementCat</code>. Владелец (<code>owner</code>) подставляется автоматически из <code>request.user</code> при создании.</p>

<hr>

<h2>🌐 API</h2>

<div align="center">

<table>
  <thead>
    <tr>
      <th align="left">Метод</th>
      <th align="left">Endpoint</th>
      <th align="left">Назначение</th>
    </tr>
  </thead>
  <tbody>
    <tr><td><code>GET / POST</code></td><td><code>/cats/</code></td><td>Список / создание котиков</td></tr>
    <tr><td><code>GET / PUT / PATCH / DELETE</code></td><td><code>/cats/{id}/</code></td><td>Работа с конкретным котиком</td></tr>
    <tr><td><code>GET / POST</code></td><td><code>/achievements/</code></td><td>Список / создание достижений</td></tr>
    <tr><td><code>GET / PUT / PATCH / DELETE</code></td><td><code>/achievements/{id}/</code></td><td>Работа с достижением</td></tr>
    <tr><td><code>POST</code></td><td><code>/auth/users/</code></td><td>Регистрация пользователя (djoser)</td></tr>
    <tr><td><code>POST</code></td><td><code>/auth/token/login/</code></td><td>Получение токена (djoser)</td></tr>
  </tbody>
</table>

</div>

<p>Для <code>CatViewSet</code> используется пагинация <code>PageNumberPagination</code>. Для <code>AchievementViewSet</code> пагинация отключена (<code>pagination_class = None</code>).</p>

<hr>

<h2>🛠️ Технологии</h2>

<div align="center">

<table>
  <thead>
    <tr>
      <th align="left">Технология</th>
      <th align="left">Версия</th>
      <th align="left">Назначение</th>
    </tr>
  </thead>
  <tbody>
    <tr><td><b>Python</b></td><td>3.10+</td><td>Язык разработки</td></tr>
    <tr><td><b>Django</b></td><td>3.2.3</td><td>Веб-фреймворк</td></tr>
    <tr><td><b>Django REST Framework</b></td><td>3.12.4</td><td>Построение REST API</td></tr>
    <tr><td><b>djoser</b></td><td>2.1.0</td><td>Аутентификация и регистрация</td></tr>
    <tr><td><b>webcolors</b></td><td>1.11.1</td><td>Валидация цветов</td></tr>
    <tr><td><b>psycopg2-binary</b></td><td>2.9.3</td><td>Драйвер PostgreSQL</td></tr>
    <tr><td><b>Pillow</b></td><td>9.0.0</td><td>Работа с изображениями</td></tr>
    <tr><td><b>PostgreSQL</b></td><td>13</td><td>База данных</td></tr>
    <tr><td><b>React</b></td><td>—</td><td>Frontend</td></tr>
    <tr><td><b>Nginx</b></td><td>1.22.1</td><td>Раздача статики</td></tr>
    <tr><td><b>Docker / Docker Compose</b></td><td>—</td><td>Контейнеризация и оркестрация</td></tr>
    <tr><td><b>Pytest</b></td><td>6.2.4</td><td>Тестирование</td></tr>
    <tr><td><b>pytest-django</b></td><td>4.4.0</td><td>Интеграция pytest с Django</td></tr>
  </tbody>
</table>

</div>

<hr>

<h2>📂 Структура проекта</h2>

<pre><code>kittygram-final-ad/
├── backend/
│   ├── cats/
│   │   ├── migrations/
│   │   ├── admin.py
│   │   ├── apps.py
│   │   ├── models.py           # Achievement, Cat, AchievementCat
│   │   ├── serializers.py      # CatSerializer, AchievementSerializer
│   │   ├── tests.py
│   │   └── views.py            # CatViewSet, AchievementViewSet
│   ├── kittygram_backend/      # Настройки проекта
│   ├── manage.py
│   ├── requirements.txt
│   └── README.md
├── frontend/
│   ├── public/
│   ├── src/
│   ├── .dockerignore
│   ├── Dockerfile
│   ├── package.json
│   ├── package-lock.json
│   └── README.md
├── nginx/
│   ├── Dockerfile              # FROM nginx:1.22.1
│   └── nginx.conf              # Раздача статики, проксирование (в разработке)
├── tests/                      # Сквозные тесты
├── .env.example                # Переменные окружения
├── .gitignore
├── README.md
├── docker-compose.yml
└── pytest.ini</code></pre>

<hr>

<h2>🐳 Состав Docker Compose</h2>

<div align="center">

<table>
  <thead>
    <tr>
      <th align="left">Сервис</th>
      <th align="left">Образ / сборка</th>
      <th align="left">Назначение</th>
    </tr>
  </thead>
  <tbody>
    <tr><td><b>db</b></td><td><code>postgres:13</code></td><td>База данных, volume <code>pg_data</code></td></tr>
    <tr><td><b>backend</b></td><td><code>./backend/</code></td><td>Django-приложение</td></tr>
    <tr><td><b>frontend</b></td><td><code>./frontend/</code></td><td>React, копирует билд в volume <code>static</code></td></tr>
    <tr><td><b>gateway</b></td><td><code>./nginx/</code></td><td>Nginx, порт <code>9000:80</code>, читает статику из <code>static</code></td></tr>
  </tbody>
</table>

</div>

<h3>Конфигурация Nginx</h3>

<p>Файл <code>nginx/nginx.conf</code> монтируется в контейнер как шаблон <code>default.conf.template</code>. Nginx:</p>

<ul>
  <li>Раздаёт статику фронтенда из <code>/static/</code> на <code>location /</code> с SPA-fallback (<code>try_files $uri $uri/ /index.html</code>).</li>
  <li>Имеет заготовки для <code>location /api/</code> и <code>location /admin/</code>, но строки <code>proxy_pass</code> пока <b>закомментированы</b> — проксирование на backend ещё не подключено.</li>
</ul>

<hr>

<h2>🔧 Переменные окружения</h2>

<p>В корне лежит <code>.env.example</code> с текущими переменными:</p>

<pre><code>POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
DB_NAME=kittygram</code></pre>

<p>Для запуска скопируйте его в <code>.env</code>:</p>

<pre><code>cp .env.example .env</code></pre>

<p>Переменные для Django (<code>SECRET_KEY</code>, <code>DEBUG</code>, <code>ALLOWED_HOSTS</code>) пока не вынесены — их добавление в планах.</p>

<hr>

<h2>🚀 Запуск проекта</h2>

<h3>Требования</h3>
<ul>
  <li><b>Docker</b> и <b>Docker Compose</b>.</li>
  <li><b>Git</b> для клонирования репозитория.</li>
</ul>

<h3>Шаги</h3>
<ol>
  <li>
    <b>Клонируйте репозиторий:</b>
    <pre><code>git clone https://github.com/DarkSwordman999/kittygram-final-ad.git
cd kittygram-final-ad</code></pre>
  </li>
  <li>
    <b>Создайте файл <code>.env</code>:</b>
    <pre><code>cp .env.example .env</code></pre>
  </li>
  <li>
    <b>Запустите контейнеры:</b>
    <pre><code>docker compose up -d --build</code></pre>
  </li>
  <li>
    <b>Примените миграции:</b>
    <pre><code>docker compose exec backend python manage.py migrate</code></pre>
  </li>
  <li>
    <b>Соберите статику:</b>
    <pre><code>docker compose exec backend python manage.py collectstatic --no-input</code></pre>
  </li>
  <li>
    <b>Создайте суперпользователя (опционально):</b>
    <pre><code>docker compose exec backend python manage.py createsuperuser</code></pre>
  </li>
</ol>

<p>После запуска статика фронтенда доступна по адресу <code>http://localhost:9000/</code>. Для работы API через браузер нужно раскомментировать <code>proxy_pass</code> в <code>nginx.conf</code>.</p>

<hr>

<h2>🧪 Тестирование</h2>

<p>Для локального запуска тестов создайте виртуальное окружение, установите зависимости и запустите <code>pytest</code> из корня проекта:</p>

<pre><code>python -m venv venv
source venv/bin/activate  # или venv\Scripts\activate на Windows
pip install -r backend/requirements.txt
pytest</code></pre>

<hr>

<h2>📁 Вложенные README</h2>

<ul>
  <li><a href="./backend/README.md">backend/README.md</a> — как запустить бэкенд локально и в Docker.</li>
  <li><a href="./frontend/README.md">frontend/README.md</a> — как запустить фронтенд локально и в Docker.</li>
</ul>

<hr>

<h2>👤 Автор</h2>

<div align="center">

<p><b>DarkSwordman999</b></p>

<a href="https://github.com/DarkSwordman999">
  <img src="https://img.shields.io/badge/GitHub-DarkSwordman999-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
</a>

</div>

<hr>

<div align="center">

<h3>🎓 Проект создан в рамках курса «Python-разработчик» от <a href="https://practicum.yandex.ru/">Яндекс Практикума</a></h3>

<p><i>Учебный проект. Создан в образовательных целях.</i></p>

</div>
