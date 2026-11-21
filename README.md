# Flugzeug Radar

Приложение для отслеживания самолётов в реальном времени по данным ADS-B. Визуализирует траектории полётов на интерактивной карте с поддержкой WebSocket.

## ✨ Особенности

- Отслеживание самолётов в реальном времени по ADS-B
- Интерактивная карта на базе Leaflet
- 3D-модели самолётов
- WebSocket для мгновенных обновлений
- Сохранение истории полётов в базу данных (Prisma + SQLite)
- Статистика по полётам
- Поддержка нескольких точек наблюдения
- Опциональная аутентификация

## 🚀 Быстрый старт

### Требования

- Node.js 18+
- Yarn
- RTL-SDR приёмник
- readsb для декодирования ADS-B

### 1. Запуск readsb

```bash
./readsb --quiet --net --net-sbs-port 30003 --device-type rtlsdr --gain auto --interactive
```

### 2. Настройка окружения

Создайте файл `.env` на основе `.env.example`:

```env
SBS_HOST=localhost
SBS_PORT=30003
APP_PORT=7103
STATE_MAX_AGE_MS=30000
DATABASE_URL=file:./prisma/dev.db
APP_AUTH_PASSWORD=your_password
SPOT_NAME=MyLocation
```

### 3. Установка и запуск

```bash
yarn install
yarn build
yarn start
```

Откройте `http://localhost:7103` в браузере.

## 📁 Структура проекта

```
flugzeug-radar/
├── src/
│   ├── index.ts              # Точка входа
│   ├── config.ts             # Конфигурация
│   ├── sbs-client.ts         # Клиент для подключения к readsb
│   ├── parser.ts             # Парсер SBS сообщений
│   ├── state.ts              # Состояние отслеживаемых самолётов
│   ├── http-server.ts        # HTTP сервер
│   ├── ws-server.ts          # WebSocket сервер
│   ├── database-manager.ts   # Работа с БД
│   └── statisticsManager.ts  # Статистика
├── public/
│   ├── index.html            # Главная страница
│   ├── app.js                # Клиентский JavaScript
│   ├── app.css               # Стили
│   └── airplane.glb          # 3D модель самолёта
├── prisma/
│   └── schema.prisma         # Схема базы данных
└── package.json
```

## 🛠 Использование

### Команды

| Команда | Описание |
|---------|----------|
| `yarn dev` | Запуск в режиме разработки |
| `yarn build` | Сборка проекта |
| `yarn start` | Запуск собранного приложения |
| `yarn db:studio` | Открыть Prisma Studio |
| `yarn db:migrate` | Применить миграции БД |

### Сетевой доступ

Приложение доступно с любого устройства в локальной сети:
- Узнайте IP сервера (например, `192.168.1.100`)
- Откройте `http://192.168.1.100:7103` на любом устройстве

## 🧪 Технологии

- **TypeScript** — язык программирования
- **Node.js** — серверная платформа
- **Prisma** — ORM для работы с базой данных
- **WebSocket (ws)** — real-time коммуникация
- **Leaflet** — интерактивные карты
- **Three.js** — 3D визуализация (для моделей самолётов)

Подпись относится к текущей версии проекта.

---

Автор: legenda  
Telegram: [@LEGENDA_SD](https://t.me/LEGENDA_SD)
