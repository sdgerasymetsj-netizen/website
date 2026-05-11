# Кастомний календар у стилі сайту 📅

## Особливості

### 🎨 Дизайн
- Темна тема у стилі сайту
- Фіолетові акценти для hover ефектів
- Помаранчевий колір для обраної дати
- Плавні анімації
- Адаптивний під мобільні пристрої

### 📱 Функціонал

#### 1. Вибір дати
- Клік на кнопку з датою відкриває кастомний календар
- Сітка 7x6 (тиждень x тижні)
- Показує дні попереднього та наступного місяця (затемнені)
- Поточний день виділений фіолетовою рамкою
- Обрана дата виділена помаранчевим фоном

#### 2. Навігація по місяцях
- Стрілки ← → для переходу між місяцями
- Клік на назву місяця відкриває вибір місяця
- Сітка 3x4 з усіма місяцями року

#### 3. Швидкі дії
- Кнопка "Сьогодні" — швидкий перехід на поточну дату
- Кнопка "Скасувати" — закрити без змін

## Структура

### HTML
```html
<div id="customCalendarModal" class="custom-calendar-modal">
  <div class="calendar-content">
    <!-- Шапка з навігацією -->
    <div class="calendar-header">
      <button class="calendar-nav-btn" id="calPrevMonth">←</button>
      <div class="calendar-month-year">Квітень 2026</div>
      <button class="calendar-nav-btn" id="calNextMonth">→</button>
    </div>
    
    <!-- Дні тижня -->
    <div class="calendar-weekdays">
      <div>Пн</div><div>Вт</div>...
    </div>
    
    <!-- Сітка днів -->
    <div class="calendar-days" id="calendarDays"></div>
    
    <!-- Вибір місяця -->
    <div class="month-picker" id="monthPicker">
      <div class="month-option">Січень</div>...
    </div>
    
    <!-- Футер з кнопками -->
    <div class="calendar-footer">
      <button class="calendar-btn cancel">Скасувати</button>
      <button class="calendar-btn today">Сьогодні</button>
    </div>
  </div>
</div>
```

### CSS класи

#### Модальне вікно
- `.custom-calendar-modal` — оверлей
- `.calendar-content` — контейнер календаря

#### Шапка
- `.calendar-header` — шапка з навігацією
- `.calendar-nav-btn` — стрілки навігації
- `.calendar-month-year` — назва місяця (клікабельна)

#### Сітка днів
- `.calendar-weekdays` — дні тижня
- `.calendar-days` — сітка днів
- `.calendar-day` — окремий день
- `.calendar-day.today` — поточний день
- `.calendar-day.selected` — обрана дата
- `.calendar-day.other-month` — дні іншого місяця

#### Вибір місяця
- `.month-picker` — сітка місяців
- `.month-option` — окремий місяць
- `.month-option.selected` — обраний місяць

#### Футер
- `.calendar-footer` — футер з кнопками
- `.calendar-btn` — кнопка
- `.calendar-btn.cancel` — кнопка скасування
- `.calendar-btn.today` — кнопка "Сьогодні"

### JavaScript функції

#### `openCustomCalendar(showMonthPicker)`
Відкриває календар
- `showMonthPicker` — якщо true, відкриває вибір місяця

#### `renderCalendar()`
Рендерить календар
- Генерує сітку днів
- Додає класи для поточного дня та обраної дати
- Додає обробники кліків

#### Змінні
- `calendarDate` — дата для відображення в календарі
- `calendarMode` — режим ('days' або 'months')

## Кольорова схема

### Фони
- Модальне вікно: `rgba(2, 6, 23, 0.9)` + blur
- Контент: `var(--bg-card)` (темний)
- Дні: `rgba(255, 255, 255, 0.03)`

### Акценти
- Hover: фіолетовий (`var(--accent-lilac-hover)`)
- Поточний день: фіолетова рамка
- Обрана дата: помаранчевий фон (`var(--accent)`)
- Кнопка "Сьогодні": фіолетовий фон

### Текст
- Основний: `var(--text-primary)` (світлий)
- Вторинний: `var(--text-secondary)` (сірий)
- Інші місяці: opacity 0.4

## Анімації

### Hover ефекти
- Дні: scale(1.05) + фіолетовий фон
- Кнопки: translateY(-2px)
- Місяці: фіолетовий фон

### Transitions
- Всі елементи: `transition: all 0.3s ease`

## Адаптивність

### Мобільні (< 768px)
- Календар займає більшу частину екрану
- Зручні розміри для touch-подій
- Мінімальний розмір кнопок 36x36px

### Десктоп
- Центрування календаря
- Максимальна ширина 350px
- Більші відступи

## Використання

### Відкрити календар
```javascript
// Клік на дату
currentDateBtn.addEventListener('click', () => {
  openCustomCalendar()
})

// Клік на місяць
currentMonthBtn.addEventListener('click', () => {
  openCustomCalendar(true) // Відкрити з вибором місяця
})
```

### Обрати дату
```javascript
// Клік на день
dayEl.addEventListener('click', function() {
  const day = parseInt(this.dataset.day)
  const month = parseInt(this.dataset.month)
  
  selectedDate = new Date(year, month, day)
  updateDateDisplay()
  renderBookingGrid(selectedDate)
  
  // Закрити календар
  customCalendarModal.style.display = 'none'
})
```

## Переваги

✅ Повністю кастомний дизайн
✅ Відповідає стилю сайту
✅ Плавні анімації
✅ Інтуїтивно зрозумілий
✅ Адаптивний
✅ Швидкий вибір дати
✅ Вибір місяця
✅ Кнопка "Сьогодні"
✅ Підтримка клавіатури (ESC для закриття)

## Порівняння з нативним

| Функція | Нативний | Кастомний |
|---------|----------|-----------|
| Дизайн | Системний | Під стиль сайту ✅ |
| Анімації | Немає | Плавні ✅ |
| Вибір місяця | Окреме поле | Інтегровано ✅ |
| Мобільний UX | Стандартний | Оптимізований ✅ |
| Кастомізація | Обмежена | Повна ✅ |
