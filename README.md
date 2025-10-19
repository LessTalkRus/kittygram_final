# 🐾 Kittygram

![Kittygram workflow status](https://github.com/LessTalkRus/kittygram_final/actions/workflows/kittygram_workflow.yml/badge.svg)

**Kittygram** — это веб‑приложение, где пользователи делятся фото питомцев, ставят лайки и просматривают котиков других участников.  
Проект на **Django + React**, упакован в Docker и развёрнут через **Nginx** и **GitHub Actions CI/CD**.

---

## ⚙️ Стек

**Backend:** Python 3.10 • Django 3.2 • DRF • Djoser • PostgreSQL  
**Frontend:** React • Node.js  
**DevOps:** Docker & Compose • Nginx • GitHub Actions

---

## 🚀 Локальный запуск

### 1) Клонирование
```bash
git clone https://github.com/LessTalkRus/kittygram_final.git
cd kittygram_final
```

### 2) .env (в корне проекта)
```env
POSTGRES_USER=django_user
POSTGRES_PASSWORD=mysecretpassword
POSTGRES_DB=django
DB_HOST=db
DB_PORT=5432

SECRET_KEY=django-insecure-cg6*%6d51ef8f#4!r3*$vmxm4)abgjw8mo!4y-q*uq1!4$-89$
DEBUG=False

ALLOWED_HOSTS=mykittygram67dev.servemp3.com,127.0.0.1,localhost
CSRF_TRUSTED_ORIGINS=https://mykittygram67dev.servemp3.com
```

### 3) Сборка и запуск
```bash
docker compose up -d --build
```
Приложение будет доступно по адресу: `http://localhost:9000/`

---

## 🧩 Volumes

| Volume  | Назначение |
|---------|------------|
| `pg_data` | Данные PostgreSQL |
| `static`  | Статика (общий для backend, frontend, gateway) |
| `media`   | Медиа, загружаемые пользователями |

---

## 🔄 CI/CD (GitHub Actions)

Пуш в ветку **main** запускает:
1. Тесты backend и frontend  
2. Сборку Docker‑образов  
3. Публикацию на Docker Hub  
4. Деплой на сервер (Docker Compose)  
5. Миграции, сбор статики, перенос в volume  
6. Уведомление в Telegram об успешном деплое

---

## 🧪 Тесты и `tests.yml`

Создайте файл `tests.yml` в корне:
```yaml
repo_owner: LessTalkRus
kittygram_domain: https://mykittygram67dev.servemp3.com
taski_domain: https://taskiserver.sytes.net
dockerhub_username: lesstalkrus
```

Локальный запуск тестов:
```bash
cd backend
pip install -r requirements.txt
cd ..
pytest
```

---

## 🌐 Доступность

- Kittygram: https://mykittygram67dev.servemp3.com  
- Taski: https://taskiserver.sytes.net  
- Docker Hub: https://hub.docker.com/u/lesstalkrus

---

## 👨‍💻 Автор

**Вячеслав Максимов** — [LessTalkRus](https://github.com/LessTalkRus)

---

## ✅ Чек‑лист

- Проекты доступны по доменам из `tests.yml`  
- Пуш в `main` — тесты и деплой проходят успешно  
- Приходит Telegram‑уведомление о деплое  
- В корне есть `kittygram_workflow.yml`
