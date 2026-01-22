# 🐹 HamsterVault

**HamsterVault** — self-hosted open-source сервис для безопасного хранения паролей и секретов  
с поддержкой **LDAP / Active Directory** и **локальной аутентификации**.

Проект создаётся как pet-project, но с production-подходом к архитектуре, безопасности и инфраструктуре.

---

## 📌 Features

- 🔐 Хранение паролей и секретов
- 👤 Аутентификация:
  - LDAP / Active Directory
  - Локальные пользователи
- 🗄 PostgreSQL как основная база данных
- 📜 Аудит и логирование входов
- 📬 Уведомления о входе через Telegram
- 🐳 Docker / Docker Compose
- 🔒 Secure-by-design подход

---

## 🧩 Authentication

HamsterVault поддерживает **два режима аутентификации**, которые могут использоваться одновременно:

### LDAP / Active Directory
- Корпоративная аутентификация
- Централизованное управление пользователями
- Поддержка AD-доменов

### Локальная аутентификация
- Встроенные пользователи
- Хэширование паролей
- Подходит для standalone и lab-окружений

Приоритет и логика выбора источника аутентификации настраиваются.

---

## 🏗 Architecture

```text
Client (Browser / API)
        │
        ▼
   Reverse Proxy
      (Nginx)
        │
        ▼
  HamsterVault (Go)
        │
        ├── PostgreSQL
        ├── LDAP / Active Directory
        └── Telegram Bot API
