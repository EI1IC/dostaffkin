# dostaffkin

Приложение для расчёта стоимости доставки, оформления заявки и отслеживания отправлений.

## Что делает
- принимает адреса «откуда»/«куда» и рисует маршрут на Яндекс.Карте
- рассчитывает цену и время по размеру груза и скорости доставки
- отправляет заявку на внешний API
- получает статус по номеру отправления

## Маршруты
- `/` — главная
- `/order` — заказ (форма маршрута + данные клиента)
- `/track` — трекинг (номер отправления)

## Ключевая логика
- `src/app/pages/order/order.ts`: работа с `ymaps` (геокод, MultiRoute), формы Angular Reactive Forms, расчет `total` и `duration`, отправка через `DeliveryApi`.
- `src/app/pages/track/track.ts`: валидация номера и запрос статуса.
- `src/app/services/delivery-api.ts`: API:
  - `POST https://testologia.ru/delivery/create`
  - `GET  https://testologia.ru/delivery/info?id=`

## Технологический стек
- Angular 21 (Standalone Components)
- TypeScript 5.9
- RxJS 7
- @angular/forms, @angular/router, @angular/common
- ngx-toastr для уведомлений
- Yandex Maps API (`ymaps`) для карты/расчёта маршрута
- Vitest, jsdom (dev)

## Установка и запуск
```bash
npm ci
npm run start
```
- сборка: `npm run build`
- тесты: `npm run test`

## Примечания
- требуется доступ в интернет (API + Яндекс-карта)
- геолокация браузера используется для автозаполнения адреса отправки
