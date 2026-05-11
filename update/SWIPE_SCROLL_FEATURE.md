# Swipe/Scroll функціонал календаря 📱

## Нові можливості

### 1. Білі стрілки навігації ⬅️➡️
- Стрілки тепер білого кольору для кращої видимості
- Контрастують з темним фоном
- Легко помітні на всіх пристроях

### 2. Прокрутка календаря 🔄

#### На мобільних пристроях (Touch):
- **Swipe вгору** ⬆️ — наступний місяць
- **Swipe вниз** ⬇️ — попередній місяць
- Мінімальна відстань swipe: 50px

#### На десктопі (Mouse):
- **Прокрутка вниз** (scroll down) — наступний місяць
- **Прокрутка вгору** (scroll up) — попередній місяць
- Працює з колесом миші

### 3. Візуальна індикація
- Горизонтальна смужка зверху календаря
- Показує, що календар можна прокручувати
- Колір: сірий напівпрозорий

## Технічні деталі

### CSS
```css
/* Білі стрілки */
.calendar-nav-btn svg {
  stroke: #ffffff;
}

/* Індикатор прокрутки */
.calendar-content::before {
  content: '';
  position: absolute;
  top: 8px;
  left: 50%;
  transform: translateX(-50%);
  width: 40px;
  height: 4px;
  background: rgba(148, 163, 184, 0.3);
  border-radius: 2px;
}

/* Дозволити вертикальну прокрутку */
.calendar-content {
  touch-action: pan-y;
  user-select: none;
}
```

### JavaScript

#### Touch Events (мобільні)
```javascript
calendarContent.addEventListener('touchstart', e => {
  touchStartY = e.touches[0].clientY
  isScrolling = false
}, { passive: true })

calendarContent.addEventListener('touchend', e => {
  if (isScrolling) return
  touchEndY = e.changedTouches[0].clientY
  handleSwipe()
}, { passive: true })

function handleSwipe() {
  const swipeDistance = touchStartY - touchEndY
  const minSwipeDistance = 50

  if (Math.abs(swipeDistance) > minSwipeDistance) {
    if (swipeDistance > 0) {
      // Swipe вгору — наступний місяць
      calendarDate.setMonth(calendarDate.getMonth() + 1)
    } else {
      // Swipe вниз — попередній місяць
      calendarDate.setMonth(calendarDate.getMonth() - 1)
    }
    renderCalendar()
  }
}
```

#### Wheel Event (десктоп)
```javascript
calendarContent.addEventListener('wheel', e => {
  e.preventDefault()
  if (Math.abs(e.deltaY) > 10) {
    if (e.deltaY > 0) {
      // Прокрутка вниз — наступний місяць
      calendarDate.setMonth(calendarDate.getMonth() + 1)
    } else {
      // Прокрутка вгору — попередній місяць
      calendarDate.setMonth(calendarDate.getMonth() - 1)
    }
    renderCalendar()
  }
}, { passive: false })
```

## Як використовувати

### На мобільному:
1. Відкрийте календар
2. Проведіть пальцем вгору або вниз по календарю
3. Календар переключиться на наступний/попередній місяць

### На десктопі:
1. Відкрийте календар
2. Наведіть курсор на календар
3. Прокрутіть колесо миші вгору або вниз
4. Календар переключиться на наступний/попередній місяць

### Альтернативно:
- Використовуйте стрілки ← → для навігації
- Клікніть на назву місяця для вибору конкретного місяця

## Переваги

### UX покращення:
✅ Інтуїтивно зрозуміла навігація
✅ Швидке переключення між місяцями
✅ Природний жест для мобільних
✅ Зручна прокрутка для десктопу
✅ Візуальна підказка (індикатор зверху)

### Технічні переваги:
✅ Passive events для кращої продуктивності
✅ Запобігання випадковим swipe (мінімальна відстань)
✅ Відрізнення scroll від swipe
✅ Підтримка всіх пристроїв

## Сумісність

### Мобільні:
- ✅ iOS Safari
- ✅ Android Chrome
- ✅ Android Firefox
- ✅ Samsung Internet

### Десктоп:
- ✅ Chrome/Edge
- ✅ Firefox
- ✅ Safari
- ✅ Opera

## Налаштування

### Мінімальна відстань swipe:
```javascript
const minSwipeDistance = 50 // пікселі
```

### Чутливість прокрутки:
```javascript
if (Math.abs(e.deltaY) > 10) // поріг чутливості
```

## Візуальні елементи

### Індикатор прокрутки:
```
┌─────────────────────────────────────┐
│            ━━━━━━                   │ ← Індикатор
│  ←   Квітень 2026   →              │
│                                     │
│  Календар...                        │
└─────────────────────────────────────┘
```

### Стрілки:
- Колір: **#ffffff** (білий)
- Розмір: 20x20px
- Товщина: 2px

## Анімації

### Swipe:
- Плавна зміна місяця
- Без додаткових анімацій (миттєво)

### Scroll:
- Миттєва зміна місяця
- Без затримок

## Доступність

### Touch:
- ♿ Мінімальна відстань 50px запобігає випадковим swipe
- ♿ Відрізнення scroll від swipe

### Mouse:
- ♿ Поріг чутливості 10px запобігає випадковим прокруткам
- ♿ Працює з будь-яким колесом миші

## Майбутні покращення

### Можливі доповнення:
- 🔄 Анімація переходу між місяцями
- 📊 Індикатор поточного місяця (dots)
- ⚡ Швидкий swipe для переходу на кілька місяців
- 🎨 Візуальний feedback при swipe

---

**Версія**: 1.4  
**Дата**: 28.04.2026  
**Статус**: ✅ Готово
