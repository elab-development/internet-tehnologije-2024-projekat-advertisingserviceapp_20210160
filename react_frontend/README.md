# Service Booking Platform

## О пројекту

Service Booking Platform је модерна веб апликација за резервацију услуга направљена у Laravel и React технологијама. Платформа омогућава ефикасно повезивање пружалаца услуга са крајњим корисницима кроз интуитиван и резидонзиван интерфејс.

## Кључне карактеристике

- **Сигурна аутентификација** - Laravel Passport са JWT токенима
- **Интегрисани календар** - напредно управљање терминима
- **Систем оцена и коментара** - транспарентна репутација пружалаца
- **Напредна претрага и филтрирање** - брзо проналажење услуга
- **RESTful API** - потпуно одвојена frontend-backend архитектура
- **CSV извоз података** - могућност преузимања листи
- **Responsive дизајн** - оптимизован за све уређаје

## Технологије

### Backend
- **Laravel 11** - PHP framework
- **MySQL** - релациона база података
- **Laravel Passport** - OAuth2 аутентификација
- **Eloquent ORM** - објектно-релациони мапинг

### Frontend
- **React 18** - JavaScript библиотека
- **Axios** - HTTP клијент
- **React Router** - навигација
- **Tailwind CSS** - стилизација

## Архитектура

```
Frontend (React) ← Axios → Backend (Laravel API) ← Eloquent → MySQL
```

## Инсталација и покретање

### Предуслови
- PHP 8.1 или новији
- Composer
- Node.js и NPM
- MySQL база података

### Кораци за инсталацију

1. **Клонирај репозиторијум**
```bash
git clone https://github.com/elab-development/internet-tehnologije-2024-projekat-advertisingserviceapp_20210160.git
cd service-booking-platform
```

2. **Инсталирај PHP зависимости**
```bash
composer install
```

3. **Инсталирај frontend зависимости**
```bash
npm install
```

4. **Подеси окружење**
```bash
cp .env.example .env
php artisan key:generate
```

5. **Подеси базу података у `.env` фајлу**
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=service_booking
DB_USERNAME=root
DB_PASSWORD=
```

6. **Покрени миграције и сидер**
```bash
php artisan migrate --seed
```

7. **Инсталирај Passport**
```bash
php artisan passport:install
```

8. **Покрени development сервер**
```bash
# Backend сервер
php artisan serve

# Frontend сервер (у другом терминалу)
npm run dev
```

Апликација ће бити доступна на:
- Frontend: `http://localhost:3000`
- Backend API: `http://localhost:8000`

## Корисничке улоге

### Customer (Корисник услуга)
- Преглед и претрага услуга
- Резервација термина
- Оцењивање и коментарисање услуга
- Преглед историје резервација

### Freelancer (Самoстални радник)
- Креирање и управљање услугама
- Дефинисање расположивих термина
- Управљање резервацијама
- Праћење репутације

### Company (Услужно предузеће)
- Све функционалности Freelancer улоге
- Верификовани профил
- Колективна репутација
- Могућност ангажовања више радника

## API документација

### Јавни endpoints (без аутентификације)
- `POST /api/register` - Регистрација корисника
- `POST /api/login` - Пријава корисника
- `GET /api/services` - Листа услуга
- `GET /api/providers` - Листа пружалаца
- `GET /api/appointments` - Листа резервација

### Заштићени endpoints (захтевају аутентификацију)
- `GET /api/user` - Профил корисника
- `POST /api/appointment` - Креирање резервације
- `POST /api/service` - Креирање услуге (за пружаоце)
- `POST /api/reviews` - Креирање рецензије

### Пример API позива
```javascript
// Пријава корисника
const response = await axios.post('/api/login', {
  email: 'customer@example.com',
  password: 'password'
});

// Добијање листе услуга
const services = await axios.get('/api/services');
```

## Тест налози

За тестирање апликације, користите следеће тест налоге:

- **Customer**: customer@example.com / password
- **Freelancer**: freelancer@example.com / password
- **Company**: company@example.com / password

## Структура базе података

Апликација користи следеће главне табеле:
- **users** - Корисници система (сви типови)
- **services** - Услуге пружалаца
- **appointments** - Резервације термина
- **time_slots** - Расположиви термини
- **reviews** - Оцене и коментари

## Сигурносне карактеристике

- Хеширање лозинки (bcrypt алгоритaм)
- Заштита од SQL инјекције (Eloquent ORM)
- CSRF заштита
- OAuth2 аутентификација (Laravel Passport)
- Валидација улазних података

## Развојне команде

```bash
# Генерисање новог контролера
php artisan make:controller ServiceController --api

# Креирање миграције
php artisan make:migration create_services_table

# Покретање тестова
php artisan test

# Ресет базе података
php artisan migrate:refresh --seed
```

## Аутори

- **Мина Николић** (2021/0049)
- **Никола Несторовић** (2021/0160)

**Ментор**: Петар Луковац

## Лиценца

Овај пројекат је развијен као семинарски рад за предмет Веб програмирање на Факултету организационих наука, Универзитет у Београду.

## Подршка

За питања и подршку, контактирајте нас преко GitHub Issues на репозиторијуму пројекта.