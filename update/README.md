# College Lab - Система бронювання аудиторій 🎓

## Встановлення

### 1. Встановити Node.js
Завантажте та встановіть Node.js з [nodejs.org](https://nodejs.org/)

### 2. Встановити залежності
```bash
npm install
```

## Запуск

### Запустити сервер:
```bash
npm start
```

Або для розробки (автоматичне перезавантаження):
```bash
npm run dev
```

### Відкрити в браузері:
```
http://localhost:3000
```

## Особливості

### ✅ Завжди 4 пари
Незалежно від дня тижня, завжди відображається 4 пари:
- I пара: 08:30 — 09:30
- II пара: 09:40 — 10:40
- III пара: 11:10 — 12:10
- IV пара: 12:20 — 13:20

### ✅ Збереження в файл
Всі бронювання зберігаються в файл `bookings.json`:
- Автоматичне збереження при кожній зміні
- Дані не зникають при перезавантаженні
- Можна робити backup файлу

### ✅ Акаунти викладачів
- **Адміністратор**: admin / admin123
- **Аушев М.О**: aushev / 123
- **Петренко Ю.О**: Petrenko / 123

## Структура файлів

```
.
├── zero.html           # Головна сторінка
├── Recording.html      # Сторінка бронювання
├── rooms.html          # Список аудиторій
├── one.css            # Стилі
├── two.js             # JavaScript логіка
├── server.js          # Backend сервер
├── bookings.json      # Файл з бронюваннями (створюється автоматично)
└── package.json       # Налаштування проекту
```

## API Endpoints

### GET /api/bookings
Отримати всі бронювання
```javascript
fetch('/api/bookings')
  .then(res => res.json())
  .then(data => console.log(data))
```

### POST /api/bookings
Зберегти бронювання
```javascript
fetch('/api/bookings', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify(bookings)
})
```

## Backup

### Створити backup:
```bash
copy bookings.json bookings.backup.json
```

### Відновити з backup:
```bash
copy bookings.backup.json bookings.json
```

## Troubleshooting

### Порт 3000 зайнятий?
Змініть порт в `server.js`:
```javascript
const PORT = 3001 // Змініть на інший порт
```

### Дані не зберігаються?
1. Перевірте, що сервер запущений
2. Перевірте консоль браузера на помилки
3. Перевірте, що файл `bookings.json` створився

### Помилка "Cannot find module 'express'"?
Запустіть:
```bash
npm install
```

## Версія
**v1.6.0** - Завжди 4 пари + збереження в файл

## Автор
College Lab Team

## Ліцензія
MIT
