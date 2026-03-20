# Инструкция для OpenClaw: исправление сайта ta1chotel.ru

Проект: `1c-hotel-training-landing`
Файлы: `index.html`, `robots.txt`, `sitemap.xml`, `llms.txt`
Домен: `ta1chotel.ru` (CNAME уже настроен)

---

## ЗАДАЧА 1: Исправить URL во всех файлах

Везде заменить `https://byivus.github.io/1c-hotel-training-landing/` на `https://ta1chotel.ru/`.

### 1.1 index.html — заменить 3 вхождения:

**Строка 10 — canonical:**
```html
<!-- БЫЛО -->
<link rel="canonical" href="https://byivus.github.io/1c-hotel-training-landing/" />
<!-- СТАЛО -->
<link rel="canonical" href="https://ta1chotel.ru/" />
```

**Строка 14 — og:url:**
```html
<!-- БЫЛО -->
<meta property="og:url" content="https://byivus.github.io/1c-hotel-training-landing/" />
<!-- СТАЛО -->
<meta property="og:url" content="https://ta1chotel.ru/" />
```

**Строка 32 — Schema.org Course url:**
```html
<!-- БЫЛО -->
"url": "https://byivus.github.io/1c-hotel-training-landing/",
<!-- СТАЛО -->
"url": "https://ta1chotel.ru/",
```

### 1.2 sitemap.xml — полная замена файла:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://ta1chotel.ru/</loc>
    <lastmod>2026-03-20</lastmod>
    <changefreq>monthly</changefreq>
    <priority>1.0</priority>
  </url>
</urlset>
```

### 1.3 robots.txt — полная замена файла:

```
User-agent: *
Allow: /

User-agent: GPTBot
Allow: /

User-agent: ChatGPT-User
Allow: /

User-agent: Google-Extended
Allow: /

User-agent: PerplexityBot
Allow: /

User-agent: ClaudeBot
Allow: /

User-agent: YandexBot
Allow: /

User-agent: Amazonbot
Allow: /

Host: ta1chotel.ru
Sitemap: https://ta1chotel.ru/sitemap.xml
```

---

## ЗАДАЧА 2: Переписать llms.txt

Полная замена файла `llms.txt`:

```markdown
# Обучение 1С:Отель — TASolution

> Онлайн-курс обучения работе в программе 1С:Отель ред. 9 (тонкий клиент) для сотрудников службы приёма и размещения отелей. 3 дня по 2 часа — итого 6 часов практики. Провайдер — TASolution (ООО «ТРИП-АДВАНС»), специализированная компания по автоматизации отелей на базе 1С.

## О курсе

Формат: онлайн, дистанционно
Длительность: 3 дня по 2 часа (итого 6 часов)
Уровень: начинающий
Язык: русский
Целевая аудитория: администраторы ресепшена, старшие администраторы, руководители службы приёма, новые сотрудники отеля

## Программа

День 1 — Введение и бронирование (2 часа, 7 тем): запуск программы, алгоритм ввода гостя, варианты создания брони, создание контрагента и договора, работа с бронированием, оплата по брони, отчёты бронирования.

День 2 — Размещение (2 часа, 8 тем): журнал фронт-офис, алгоритм размещения, карточка гостя, переселение, продление, фолио, начисление услуг и оплата, выселение, работа с деньгами, закрытие кассовой смены, создание услуг, выгрузка Контур ФМС.

День 3 — Служба номерного фонда и отчёты (2 часа, 5 тем): список номеров, питание, бронь ресурсов, взаиморасчёты с контрагентами, отчёты, рассылка из 1С:Отель.

## Компания

ООО «ТРИП-АДВАНС» (бренд: TASolution / Tripadvance)
ИНН: 2301105561
Регион: Краснодарский край, Анапа
Специализация: автоматизация отелей на базе 1С (1С:Отель, 1С:СПА, 1С:Фитнес, 1С:Общепит)

## Ссылки

- [Главная страница курса](https://ta1chotel.ru/)
- [Записаться на обучение](https://tasolution.ru/training-1c-hotel)
- [Сайт компании TASolution](https://tasolution.ru)

## Контакты

Телефон: +7 (861) 213-23-13
Email: acc@tripadvance.ru
```

---

## ЗАДАЧА 3: Исправить Schema.org в index.html

### 3.1 Исправить duration в CourseInstance (строки 44-61)

В каждом `CourseInstance` заменить `"duration": "PT6H"` на `"duration": "PT2H"`.

### 3.2 Добавить Schema.org Organization

Вставить ПЕРЕД закрывающим тегом `</head>` новый блок `<script type="application/ld+json">`:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "TASolution",
  "alternateName": ["Tripadvance", "ТРИП-АДВАНС"],
  "url": "https://tasolution.ru",
  "telephone": "+78612132313",
  "email": "acc@tripadvance.ru",
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "Анапа",
    "addressRegion": "Краснодарский край",
    "addressCountry": "RU"
  },
  "taxID": "2301105561",
  "description": "Специализированная компания по автоматизации отелей на базе 1С. Внедрение и сопровождение 1С:Отель, 1С:СПА, 1С:Фитнес, 1С:Общепит."
}
</script>
```

### 3.3 Добавить Schema.org FAQPage

Вставить ПЕРЕД закрывающим тегом `</head>` ещё один блок:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Сколько длится обучение 1С:Отель?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Курс длится 3 дня по 2 часа — итого 6 часов онлайн-практики. Каждый день — законченный блок: бронирование, размещение, отчёты."
      }
    },
    {
      "@type": "Question",
      "name": "Кому подходит курс 1С:Отель?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Курс рассчитан на администраторов ресепшена, старших администраторов, руководителей службы приёма и новых сотрудников отеля, которые работают или будут работать в 1С:Отель ред. 9."
      }
    },
    {
      "@type": "Question",
      "name": "В каком формате проходит обучение?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Обучение проходит онлайн — дистанционно, без командировок. Вы подключаетесь с рабочего места и работаете в реальной системе 1С:Отель под руководством сертифицированного специалиста."
      }
    },
    {
      "@type": "Question",
      "name": "Что входит в программу курса?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Полный цикл фронт-офиса: бронирование, создание контрагентов, размещение гостей, начисление услуг, оплата, выселение, работа с кассой, служба номерного фонда, отчёты и выгрузка в Контур ФМС."
      }
    },
    {
      "@type": "Question",
      "name": "Нужна ли установленная 1С:Отель для обучения?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Нет. Мы предоставляем доступ к учебной базе 1С:Отель. Вам нужен только компьютер с интернетом."
      }
    },
    {
      "@type": "Question",
      "name": "Выдаётся ли сертификат после обучения?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Да, по завершении курса выдаётся сертификат от TASolution о прохождении обучения по программе 1С:Отель."
      }
    }
  ]
}
</script>
```

---

## ЗАДАЧА 4: Обновить meta-теги в index.html

### 4.1 Улучшить title (строка 6)

```html
<!-- БЫЛО -->
<title>Обучение 1С:Отель — TASolution / Tripadvance</title>
<!-- СТАЛО -->
<title>Обучение 1С:Отель — онлайн-курс для администраторов | TASolution</title>
```

### 4.2 Улучшить description (строка 7)

```html
<!-- БЫЛО -->
<meta name="description" content="Онлайн-обучение 1С:Отель для сотрудников службы приёма и размещения. 3 дня × 2 часа = 6 часов. Полный цикл от бронирования до выселения. TASolution — специалисты по 1С:Отель." />
<!-- СТАЛО -->
<meta name="description" content="Онлайн-обучение 1С:Отель ред. 9 для сотрудников фронт-офиса. 3 дня × 2 часа = 6 часов практики. Полный цикл от бронирования до выселения. Сертификат. TASolution — автоматизация отелей на 1С." />
```

### 4.3 Расширить keywords (строка 8)

```html
<!-- БЫЛО -->
<meta name="keywords" content="обучение 1С Отель, курс 1С Отель, онлайн обучение гостиница, 1С Отель ред 9, фронт-офис, бронирование, размещение гостей, TASolution, Tripadvance" />
<!-- СТАЛО -->
<meta name="keywords" content="обучение 1С Отель, курс 1С Отель, 1С Отель ред 9, онлайн обучение гостиница, фронт-офис обучение, бронирование 1С, размещение гостей, TASolution, Tripadvance, автоматизация отеля, обучение администраторов отеля, курсы гостиничный бизнес" />
```

### 4.4 Добавить после строки 10 (после canonical):

```html
<link rel="alternate" hreflang="ru" href="https://ta1chotel.ru/" />
<link rel="icon" href="/favicon.ico" type="image/x-icon" />
```

### 4.5 Добавить og:image и og:site_name (после строки 17)

```html
<meta property="og:image" content="https://ta1chotel.ru/og-image.jpg" />
<meta property="og:site_name" content="TASolution — обучение 1С:Отель" />
```

### 4.6 Обновить twitter:card (строка 21)

```html
<!-- БЫЛО -->
<meta name="twitter:card" content="summary" />
<!-- СТАЛО -->
<meta name="twitter:card" content="summary_large_image" />
```

### 4.7 Добавить twitter:image (после строки 23)

```html
<meta name="twitter:image" content="https://ta1chotel.ru/og-image.jpg" />
```

---

## ЗАДАЧА 5: Улучшить H2-заголовки в index.html

### 5.1 Секция "О курсе" (строка 628)

```html
<!-- БЫЛО -->
<h2 class="section__title">Всё, что нужно для работы во фронт-офисе</h2>
<!-- СТАЛО -->
<h2 class="section__title">Онлайн-курс 1С:Отель — всё для работы фронт-офиса</h2>
```

### 5.2 Секция "Программа" (строка 661)

```html
<!-- БЫЛО -->
<h2 class="section__title">Что вы изучите</h2>
<!-- СТАЛО -->
<h2 class="section__title">Программа обучения 1С:Отель: 3 дня практики</h2>
```

### 5.3 Секция "Преимущества" (строка 786)

```html
<!-- БЫЛО -->
<h2 class="section__title">Наши преимущества</h2>
<!-- СТАЛО -->
<h2 class="section__title">Почему выбирают обучение 1С:Отель от TASolution</h2>
```

---

## ЗАДАЧА 6: Добавить FAQ-секцию на страницу

Вставить ПЕРЕД секцией CTA (перед строкой `<!-- ─── CTA / CONTACTS ─── -->`, строка 821) новую секцию:

```html
<!-- ─── FAQ ─── -->
<section class="section section--gray" id="faq">
  <div class="container">
    <div class="section__tag">FAQ</div>
    <h2 class="section__title">Частые вопросы об обучении 1С:Отель</h2>
    <p class="section__lead">Ответы на вопросы, которые чаще всего задают перед обучением.</p>
    <div class="faq__list">
      <details class="faq__item">
        <summary class="faq__question">Сколько длится обучение 1С:Отель?</summary>
        <p class="faq__answer">Курс длится 3 дня по 2 часа — итого 6 часов онлайн-практики. Каждый день — законченный блок: бронирование, размещение, отчёты.</p>
      </details>
      <details class="faq__item">
        <summary class="faq__question">Нужна ли установленная 1С:Отель для обучения?</summary>
        <p class="faq__answer">Нет. Мы предоставляем доступ к учебной базе 1С:Отель. Вам нужен только компьютер с интернетом.</p>
      </details>
      <details class="faq__item">
        <summary class="faq__question">Выдаётся ли сертификат?</summary>
        <p class="faq__answer">Да, по завершении курса выдаётся сертификат от TASolution о прохождении обучения по программе 1С:Отель.</p>
      </details>
      <details class="faq__item">
        <summary class="faq__question">Можно ли обучить несколько сотрудников одновременно?</summary>
        <p class="faq__answer">Да, формат позволяет подключить до 5–10 сотрудников на одну сессию. Стоимость зависит от количества участников.</p>
      </details>
      <details class="faq__item">
        <summary class="faq__question">Какую редакцию 1С:Отель используете?</summary>
        <p class="faq__answer">Обучение проходит на 1С:Отель редакции 9, тонкий клиент — актуальная версия программы.</p>
      </details>
      <details class="faq__item">
        <summary class="faq__question">Что такое 1С:Отель?</summary>
        <p class="faq__answer">1С:Отель — специализированная программа автоматизации гостиничного бизнеса на платформе 1С:Предприятие. Поддерживает полный цикл работы фронт-офиса: от бронирования номеров и регистрации гостей до выставления счетов, работы с кассой и формирования отчётности.</p>
      </details>
    </div>
  </div>
</section>
```

Также добавить в навигацию (строка 583, после ссылки "Преимущества"):

```html
<li><a href="#faq">FAQ</a></li>
```

---

## ЗАДАЧА 7: Добавить CSS для FAQ

Вставить ПЕРЕД комментарием `/* ─── CTA SECTION ─── */` (строка 448) в блоке `<style>`:

```css
/* ─── FAQ ─── */
.faq__list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}
.faq__item {
  border: 1px solid var(--gray-200);
  border-radius: var(--radius);
  background: var(--white);
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0,0,0,.04);
}
.faq__question {
  padding: 20px 24px;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  user-select: none;
  list-style: none;
  display: flex;
  align-items: center;
  justify-content: space-between;
  transition: background var(--transition);
}
.faq__question:hover { background: var(--gray-100); }
.faq__question::after {
  content: '+';
  font-size: 20px;
  font-weight: 400;
  color: var(--blue);
  flex-shrink: 0;
  margin-left: 16px;
  transition: transform var(--transition);
}
details[open] .faq__question { background: var(--blue-light); }
details[open] .faq__question::after {
  content: '−';
}
.faq__question::-webkit-details-marker { display: none; }
.faq__answer {
  padding: 0 24px 20px;
  font-size: 15px;
  color: var(--gray-600);
  line-height: 1.65;
}
```

---

## ЗАДАЧА 8: Исправить footer — год

Строка 870:

```html
<!-- БЫЛО -->
<span>© 2024 ООО «ТРИП-АДВАНС». Все права защищены.</span>
<!-- СТАЛО -->
<span>© 2024–2026 ООО «ТРИП-АДВАНС». Все права защищены.</span>
```

---

## ЗАДАЧА 9: Исправить мобильное меню — показать CTA

В CSS (строка 165), блок `@media (max-width: 720px)` — убрать `.nav__cta` из скрытия:

```css
/* БЫЛО */
.nav__links, .nav__cta { display: none; }

/* СТАЛО */
.nav__links { display: none; }
.nav__cta { display: none; }
```

И обновить `.nav.open .nav__cta` (строка 177):

```css
.nav.open .nav__cta {
  display: inline-block;
  margin: 4px 20px 16px;
  text-align: center;
  width: calc(100% - 40px);
}
```

Также в `nav.open .nav__links` (строка 168) добавить показ CTA после ссылок. Вставить CTA-кнопку внутрь `.nav__links` в HTML (перед `</ul>`, строка 584):

```html
<li class="nav__cta-mobile">
  <a href="https://tasolution.ru/training-1c-hotel" class="nav__cta" target="_blank" rel="noopener">Записаться</a>
</li>
```

И CSS для мобильного CTA:

```css
.nav__cta-mobile { display: none; }
@media (max-width: 720px) {
  .nav__cta-mobile { display: block; }
  .nav__cta-mobile .nav__cta {
    display: block;
    text-align: center;
    width: 100%;
  }
}
```

---

## ЗАДАЧА 10: Добавить accessibility (a11y)

### 10.1 Аккордеон программы — добавить ARIA-атрибуты

Для каждого `.day__header` добавить атрибуты:

```html
<div class="day__header" role="button" tabindex="0" aria-expanded="true">
```

(Для закрытых дней `aria-expanded="false"`)

### 10.2 В JS-секцию добавить клавиатурную навигацию

Добавить после блока аккордеона (строка ~893):

```javascript
// Keyboard support for accordion
document.querySelectorAll('.day__header').forEach(header => {
  header.addEventListener('keydown', e => {
    if (e.key === 'Enter' || e.key === ' ') {
      e.preventDefault();
      header.click();
    }
  });
});
```

### 10.3 Обновить JS аккордеона — переключать aria-expanded

Заменить текущий обработчик аккордеона (строки 888-893):

```javascript
// Accordion
document.querySelectorAll('.day__header').forEach(header => {
  header.addEventListener('click', () => {
    const day = header.closest('.day');
    day.classList.toggle('open');
    const isOpen = day.classList.contains('open');
    header.setAttribute('aria-expanded', isOpen);
  });
});
```

---

## ЗАДАЧА 11: Создать og-image.jpg

Нужно создать изображение 1200×630 px для соцсетей:
- Фон: синий градиент (#1a3a8f → #1a56db)
- Текст: "Обучение 1С:Отель" (крупно), "3 дня × 2 часа | Онлайн" (мельче)
- Логотип TASolution
- Сохранить как `og-image.jpg` в корень проекта

**Это нужно сделать вручную** (или через Canva/Figma) — OpenClaw не генерирует изображения.

---

## ЗАДАЧА 12: Создать favicon.ico

Нужен favicon 32×32 px:
- Буква "T" или "1С" на синем фоне (#1a56db)
- Сохранить как `favicon.ico` в корень проекта

**Это нужно сделать вручную** — через realfavicongenerator.net или Figma.

---

## ЗАДАЧА 13: Создать 404.html

Создать файл `404.html` в корне проекта (GitHub Pages подхватит автоматически):

```html
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Страница не найдена — TASolution</title>
  <meta name="robots" content="noindex" />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet" />
  <style>
    body {
      font-family: 'Inter', sans-serif;
      display: flex;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      margin: 0;
      background: #f8f9fa;
      color: #212529;
      text-align: center;
      padding: 20px;
    }
    h1 { font-size: 72px; color: #1a56db; margin: 0; }
    p { font-size: 18px; color: #6c757d; margin: 12px 0 32px; }
    a {
      display: inline-block;
      background: #1a56db;
      color: #fff;
      padding: 14px 28px;
      border-radius: 10px;
      text-decoration: none;
      font-weight: 600;
      transition: background .2s;
    }
    a:hover { background: #1341b0; }
  </style>
</head>
<body>
  <div>
    <h1>404</h1>
    <p>Страница не найдена. Возможно, она была перемещена или удалена.</p>
    <a href="/">На главную</a>
  </div>
</body>
</html>
```

---

## ПОРЯДОК ВЫПОЛНЕНИЯ

1. **Задачи 1-3** — критические, делать первыми (URL, llms.txt, Schema.org)
2. **Задачи 4-5** — мета-теги и заголовки
3. **Задачи 6-7** — FAQ секция + CSS
4. **Задача 8** — footer год
5. **Задачи 9-10** — мобильное меню и a11y
6. **Задачи 11-12** — графика (вручную)
7. **Задача 13** — страница 404

После всех правок — сделать `git commit` и `git push`, проверить https://ta1chotel.ru/.
Затем проверить Schema.org через https://search.google.com/test/rich-results.
