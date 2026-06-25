## 20-21.05.2026 — День 1-2. SQL основы

### Что сделал:

- Создал таблицы authors и books в SQLite
- Добавил данные через INSERT
- Написал первый JOIN

### Что понял:

- Зачем нужны связанные таблицы
- Что такое PRIMARY KEY и FOREIGN KEY
- Как JOIN соединяет таблицы

## 22.05.2026 — День off

Физиология, не лень.

## 23.05.2026 - День 3. SQL основы

### Что сделал:

- Освоил WHERE вместе с BETWEEN 
- освоил DELETE

### Что понял:

- Для чего нужна фильтрация и как правильно ее делать
- Различные условия для WHERE

### Что осталось повторить:

- ALTER TABLE
- UPDATE

## 24.05.2026 - День 4. SQL основы

- ALTER TABLE
- Агрегатные функции AVG,SUM,COUNT
- UPDATE
- JOIN  с требя таблицами

### Что понял:

- Понял зачем фильтрация с WHERE
- Что JOIN c 3 таблицами это 2 JOIN  по отдельности

## 25-26.05.2026 - День 5-6. Django + основы ORM

- Создание Django project
- Модели (таблицы)
- Миграции
- objects.create, objects.all, objects.get, objects.filter
- ForeignKey
- select_related

### Что понял:

- зачем нужен __str__
- разница между get и filter
- в каким случаях используется select_related
  

### Что не понял:

- ForeignKey - не понимаю синтаксис
- select_related - не понял как работает изнутри

## 27.05.2026 - День 7. День off

- Не успел

## 28-29.05.2026 - День 9-10. Django + основы ORM

## Что делал:

- ForeignKey
- select_related
- фильтрация через связанные объекты

### Что понял:

- ForeignKey - хранит в себе просто число в базе

###  Что не понял:

- select_related
- filter через связанные объекты


30.05.2026 — День 11. Django ORM углубление

### Что сделал:

- Добавил модель Genre в приложение books
- Добавил поле genre в модель Book с null=True, blank=True
- Присваивал жанры книгам через объект.поле = значение + save()
- Фильтровал книги по жанру через filter(genre=roman)
- Совместил select_related и filter в одной строке
- Выполнил 4 самостоятельных задания без подсказок

### Что понял:

- Разница между CASCADE и SET_NULL
- Паттерн: get → изменить → save()
- filter(genre__isnull=True) для поиска пустых полей


## 31-02.05.2026 — День 12-15. Проект Кофейня

### Что сделал:

- Создал новое приложение coffee в Django
- Спроектировал 3 модели: Category, Drink, Order
- Написал миграции
- Заполнил базу данными через ORM
- Написал все запросы самостоятельно
- Залил проект на GitHub с README

### Что понял:

- Как проектировать модели с нуля
- Категория — это строки в таблице, не поля
- select_related принимает связанную модель, не просто поле

## 03.06.2026 - День 16. DRF — первый API

### Что сделал:
- Установил DRF и подключил в INSTALLED_APPS
- Написал первый сериализатор для модели Drink
- Создал view drink_list с GET и POST
- Подключил URLs
- Проверил API в браузере

### Что понял:
- Сериализатор переводит модель в JSON и обратно
- @api_view говорит какие методы принимает функция
- request.data — это данные которые клиент прислал
- is_valid() проверяет данные перед сохранением

## 04.06.2026 - День off

## 05.06.2026 - День 17. DRF — полный CRUD

### Что сделал:
- Написал drink_detail с GET, PUT, DELETE
- Добавил правильные status codes (201, 204, 404)
- Добавил get_object_or_404 для обработки ошибок
- Написал полный CRUD для Order самостоятельно
- Протестировал все методы в браузере

### Что понял:
- PUT обновляет существующий объект — нужно передать item и data
- DELETE просто вызывает item.delete()
- Статус коды нужны чтобы клиент понял что произошло
- 404 лучше чем непонятная ошибка 500
- Паттерн CRUD одинаковый для любой модели

### Что осталось:
- ViewSets и Routers
- Аутентификация
- Permissions


## 06.06.2026 - День 18. DRF — ViewSets, Routers, @action

### Что сделал:
- Переписал все view на ViewSets (DrinkViewSet, CategoryViewSet, OrderViewSet)
- Подключил DefaultRouter — автоматические URLs
- Написал кастомный эндпоинт через @action detail=False (cheap_drinks)
- Написал кастомный эндпоинт через @action detail=True (today_orders)
- Почистил код — 60 строк стало 20

### Что понял:
- ViewSet заменяет две функции одним классом
- Router автоматически создаёт URLs — не нужно писать path вручную
- @action detail=False — для всей коллекции (/drinks/cheap_drinks/)
- @action detail=True — для одного объекта (/order/2/today_orders/)
- pk=None в сигнатуре — дефолт, реальный pk приходит из URL

### Честно — что не до конца понял:
- Разница между @api_view и @action на интуитивном уровне
- Когда именно использовать detail=True vs detail=False
- self.get_object() 


## 07.06.2026 - День 19. Вложенные сериализаторы + @action углубление

### Что сделал:
- Добавил вложенный сериализатор category в Drinkserializers
- Добавил read_only и write_only поля (category_id)
- Добавил вложенный сериализатор drink в Orderserializers
- Написал 5 кастомных @action эндпоинтов:
  - /drinks/cheap_drinks/ — напитки до 300р
  - /drinks/low_price/ — сортировка по цене
  - /drinks/most-expensive/ — самый дорогой
  - /category/1/all_drinks/ — напитки по категории
  - /order/all_orders/ — количество заказов

### Что понял:
- read_only=True — поле только для чтения, не принимает данные при POST
- write_only=True — поле только для записи, не показывается в GET
- Паттерн: category для чтения + category_id для записи
- order_by('-price') — минус означает обратный порядок
- first() — берёт первый объект из QuerySet

### Что не понял до конца:
- url_path в @action — зачем нужен и когда использовать
- Интуиция когда использовать detail=True vs detail=False

### Что повторить:
- Написать вложенный сериализатор с нуля без подсказок
- @action синтаксис полностью по памяти


## 08.06.2026 - День 20. Фильтрация и пагинация

### Что сделал:
- Установил django-filter
- Написал кастомный FilterSet с max_price, min_price, name
- Подключил кастомную пагинацию только для DrinkViewSet
- Добавил page_size_query_param — клиент сам выбирает размер

### Что понял:
- FilterSet пишется один раз и подключается в ViewSet
- lte = меньше или равно, gte = больше или равно
- icontains ищет по части слова без учёта регистра
- Кастомная пагинация для одного ViewSet vs глобальная для всех

### Что не понял до конца:
- Разница между кастомной и глобальной пагинацией на практике


## 09.06-10.06.2026 - День 21-22. Аутентификация и Permissions 

### Что прошёл
- Токен-аутентификация: установка rest_framework.authtoken
- Эндпоинт /token/ для получения токена
- Тестирование API через curl (новый навык)
- Permissions: IsAuthenticated, AllowAny, IsAdminOrReadOnly
- Глобальные vs локальные permission_classes
- Написал кастомный permission IsAdminOrReadOnly с нуля
- Создал пользователей через createsuperuser и shell

### Что понял хорошо
- Локальный permission_classes на ViewSet всегда побеждает глобальный
- has_permission возвращает только True или False — не Response
- SAFE_METHODS = GET, HEAD, OPTIONS — не меняют данные
- Разница между 401 (нет токена) и 403 (нет прав)

### Что нужно повторить
- Что такое stateless и почему из-за этого нужен токен
- Три шага установки: INSTALLED_APPS → migrate → REST_FRAMEWORK
- Разница 401 vs 403 — путаю до сих пор
- Закрепить все до уверенного уровня

### Что сделал
- Написал permissions.py с кастомным IsAdminOrReadOnly
- Настроил TokenAuthentication в settings.py
- Подключил obtain_auth_token в urls.py
- Протестировал API через curl впервые
- Создал двух пользователей: MRX (админ) и barista (обычный)
- Проверил разницу прав на реальных запросах

## 11.06.2026 - День off

## 12-13.06.2026 - День 24-25. CSS основы + DRF расширение (Review)

### Что сделал (CSS):
- Создал структуру frontend проекта: index.html + style.css
- Освоил CSS reset (* { margin: 0; padding: 0; box-sizing: border-box })
- Сделал навбар на Flexbox (display: flex, justify-content: space-between, align-items: center)
- Стилизовал карточки напитков через CSS Grid (grid-template-columns: repeat(3, 1fr), gap)
- Подключил CORS (django-cors-headers) — установка, settings.py, middleware
- Написал первый fetch() к своему Django API
- Вывел реальные данные категорий (Смузи, Чай, Кофе) из БД в консоль через forEach

### Что не понял (CSS):
- Пока копирую CSS код, не пишу сам — синтаксис свойств не запоминается
- box-sizing: border-box — что именно делает, не уловил до конца
- Общая логика "какое свойство для чего" — пока не интуитивно

### Что сделал (DRF — новая модель Review):
- Создал модель Review: drink (FK→Drink, CASCADE), author (FK→User, SET_NULL), text, rating, created_at
- Написал миграцию
- Создал Reviewserializers с вложенным drink (read_only) + drink_id (write_only) + author (StringRelatedField)
- Создал ReviewViewSet с permission_classes = [IsAuthenticatedOrReadOnly]
- Освоил новый метод perform_create — автозапись author из request.user
- Зарегистрировал ReviewViewSet в DefaultRouter
- Протестировал через curl: GET без токена (200), POST без токена (401), POST с токеном (201)
- Самостоятельно нашёл и исправил ошибку FOREIGN KEY constraint failed (несуществующий drink_id)

### Что понял (DRF):
- perform_create — место где сервер добавляет данные которые клиент не отправлял
- IsAuthenticatedOrReadOnly: GET — все, POST/PUT/DELETE — любой залогиненный (не только админ)
- StringRelatedField — показывает строковое представление связанного объекта
- FOREIGN KEY constraint failed — ссылка на несуществующий id в другой таблице

### Повторение DRF по памяти (с утра):
- permissions.py (IsAdminOrReadOnly) — написал почти полностью с первой попытки
- urls.py (obtain_auth_token) — мелкие синтаксические ошибки, исправил сам
- settings.py REST_FRAMEWORK — несколько попыток с опечатками, итоговый вариант правильный

### Что повторить:
- Синтаксис JavaScript (.then(), forEach, стрелочные функции) — копировал, не до конца понимает
- settings.py REST_FRAMEWORK по памяти — ещё нестабильно


## 14-15.06.2026 - День 26-27. CSS закрепление + DRF расширение

### Что сделал (CSS):
- Написал style.css по памяти (с гуглом)
- Заменил статичные карточки на динамические через fetch
- Подключили реальные напитки из /coffee/drinks/ — карточки создаются из данных API
- Нашёл и исправил баг с пагинацией (page_query_param → page_size_query_param)

### Что понял (CSS):
- padding — внутренний отступ, margin — внешний
- display: flex + justify-content + align-items — стандартный паттерн для навбара
- display: grid + repeat(3, 1fr) + gap — сетка карточек
- CSS reset обнуляет дефолтные стили браузера

### Что не понял / повторить (CSS):
- Не могу пока что писать импровизируя
- fetch и остальное

### Что сделал (DRF):
- Добавил @action для ReviewViewSet с фильтрацией отзывов
- Создал новую модель Promotion
- Написал миграцию
- Создал Promotionserializers c вложенным drinks (read_only) и drinks_ids (write_only) + PrimaryKeyRealtedField
- Создал PromotionViewSet с правами [IsAdminOrReadOnly] и perfom_create

### Что понял (DRF):
- IsAdminOrReadOnly — GET для всех, изменения только для is_staff=True
- filterset_fields — простая фильтрация без кастомного FilterSet
- many=True в сериализаторе — когда передаёшь список объектов
- @action detail=False — для всей коллекции, не для одного объекта
  

### Что не понял / повторить (DRF):
- ManyToMany — интуиция есть, но синтаксис не уверен
- perform_create для ManyToMany — почему сначала save(), потом set()
- PrimaryKeyRelatedField — зачем нужен

  ## 18.06.2026 - День 28. CSS адаптивность + DRF (Favorites)

### Что сделал (CSS):
- Добавил media query для .drinks-grid: 3 колонки (десктоп) → 2 (планшет, ≤1024px) → 1 (телефон, ≤768px)
- Добавил адаптивность для .navbar — уменьшил padding и font-size h1 на узких экранах
- Проверил все breakpoints через DevTools responsive mode

### Что понял (CSS):
- @media (max-width: Npx) — стили применяются только когда ширина экрана ≤ N
- Обычные стили — база для десктопа, media query её переопределяет на маленьких экранах
- Можно использовать несколько breakpoints для разных размеров (телефон/планшет/десктоп)

### Что сделал (DRF — модель Favorite):
- Создал модель Favorite: user (FK→User, CASCADE), drink (FK→Drink, CASCADE), added_at (DateTimeField, auto_now_add)
- Написал миграцию
- Создал Favoriteserializer с вложенным drink (read_only) + drink_id (write_only), без поля user
- Создал FavoriteViewSet с permission_classes = [IsAuthenticated]
- Освоил новый метод get_queryset — фильтрует список по request.user
- Зарегистрировал FavoriteViewSet в DefaultRouter
- Протестировал через curl: добавил Латте в избранное (barista), проверил что MRX видит пустой список

### Что понял (DRF):
- get_queryset переопределяет queryset динамически — фильтрует данные ДО сериализации
- Без get_queryset все пользователи видели бы избранное друг друга — утечка приватных данных
- perform_create + get_queryset — стандартная пара для данных привязанных к пользователю
- DateTimeField vs DateField — DateTime хранит время, важно для сортировки "недавнее"

### Утреннее повторение DRF:
- permissions.py (IsAdminOrReadOnly) — написал почти с первой попытки
- settings.py REST_FRAMEWORK — написал ИДЕАЛЬНО с первой попытки, без единой ошибки (прогресс!)

### Что повторить:
- Синтаксис get_queryset — закрепить написанием с нуля в следующий раз
- unique_together — новая концепция упомянутая мимоходом, не разбирали глубоко

## 19-20.06.2026 - День 29-30. SearchFilter + OrderingFilter + вложенные роутеры

### Что сделал (CSS закрепление):
- Написал media queries по памяти (768px и 1024px)
- Написал CSS reset, body, navbar с Flexbox по памяти

### Что сделал (DRF):
- Добавил SearchFilter в DrinkViewSet — поиск по name и category__name через ?search=
- Добавил OrderingFilter в DrinkViewSet — сортировка через ?ordering=price и ?ordering=-price
- Установил drf-nested-routers
- Настроил вложенный роутер: /coffee/drinks/5/reviews/
- Обновил get_queryset в ReviewViewSet — работает для обоих эндпоинтов

### Что понял (DRF):
- SearchFilter ищет по нескольким полям одновременно через один параметр ?search=
- OrderingFilter: ?ordering=price — по возрастанию, ?ordering=-price — по убыванию (минус = обратный порядок)
- Вложенный роутер даёт более логичную структуру URL — /drinks/5/reviews/ показывает отзывы конкретного напитка
- get_queryset с .get('drink_pk') — работает в обоих случаях: с вложенным URL и без

### Что не понял / повторить:
- Синтаксис NestedDefaultRouter — писал с подсказкой
- Как именно kwargs передаёт drink_pk из URL в get_queryset

### Утреннее повторение:
- REST_FRAMEWORK — написал правильно с первой попытки ✅
- IsAdminOrReadOnly — почти без ошибок ✅


## 21.06.2026 - день off
- Усталость

## 22.06.2026 - день off
- болел



## 23.06.2026 - День 33. CSS закрепление + pytest + модель Ingredients

### Что сделал (CSS закрепление):
- Написал .card, .navbar, .drinks-grid по памяти (с гуглом на некоторые свойства)
- Объяснил разницу flex/grid/media queries своими словами

### Что сделал (pytest):
- Установил pytest + pytest-django
- Настроил pytest.ini
- Написал 5 базовых тестов:
  - GET /coffee/category/ → 200
  - GET /coffee/drinks/ → 200
  - GET /coffee/order/ без токена → 401
  - POST /coffee/category/ с токеном админа → 201
  - POST /coffee/category/ с токеном обычного юзера → 403
- Нашёл реальный баг: CategoryViewSet имел AllowAny — любой мог создавать категории
- Исправил баг: поменял на IsAdminOrReadOnly

### Что сделал (DRF — модель Ingredients):
- Создал модель Ingredients: name, is_allergen, extra_price, drinks (ManyToMany)
- Написал миграцию
- Создал Ingredientsserializer с вложенным drinks (read_only, many=True) + drinks_ids (write_only)
- Создал IngredientsViewSet с perform_create (pop/save/set паттерн)
- Зарегистрировал в urls.py
- Протестировал через curl — создал "Карамельный сироп" привязанный к двум напиткам
- Написал 2 теста для Ingredients — все 7 тестов зелёные

### Что понял:
- pytest находит баги которые руками не замечаешь — тест на CategoryViewSet нашёл реальную дыру в безопасности
- @pytest.mark.django_db — разрешает работу с БД в тестах
- client.credentials() — устанавливает токен для всех запросов клиента
- assert — проверяет условие, тест падает если False

### Что не понял / повторить:
- perform_create для ManyToMany — пишу с подсматриванием, логику понимаю
- Синтаксис PrimaryKeyRelatedField — нужно ещё закрепить
- Синтаксис pytest не до конца понятен — @pytest.mark.django_db, client.credentials(), структура тестов в целом

### Утреннее повторение:
- IsAdminOrReadOnly ✅
- REST_FRAMEWORK ✅
- perform_create + get_queryset — написал с подсказкой


## 25.06.2026 - День 34. Рефакторинг Order → Order + OrderItem

### Что сделал:
- Переписал модель Order: убрал ForeignKey на Drink, добавил TextChoices (PENDING/PREPARING/READY/COMPLETED) и created_at
- Создал промежуточную модель OrderItem: order (FK, related_name='items'), drink (FK), quantity
- Переписал OrderItemserializers и Orderserializers с вложенными items
- Написал perform_create с циклом: pop → save → for item: create
- Удалил db.sqlite3 и миграции, пересоздал базу чисто
- Зарегистрировал все модели в admin.py
- Протестировал через curl — заказ с двумя напитками создался корректно
- Написал 2 новых теста: POST с токеном (201) и без токена (401) — 9/9 зелёных

### Что понял:
- TextChoices хранит короткий код в БД ('PD'), показывает читаемое значение ('Pending')
- related_name='items' даёт удобный доступ order.items.all() вместо order.orderitem_set.all()
- ManyToMany нельзя сохранить до создания объекта — нужен id, поэтому сначала save(), потом create() в цикле
- admin.site.register() — регистрация модели в админке

### Что было сложно:
- Структура данных для теста (items_data со списком словарей)
- Понять почему perform_create не может сохранить OrderItem до save()

### Что не понял / повторить:
- TextChoices vs IntegerChoices — понял разницу, но синтаксис ещё не уверенный
- validated_data.pop() — зачем именно pop а не просто get
- Структура вложенных данных в pytest — писал с подсказкой

