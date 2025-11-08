
# Лендинг 
Лендинг с базовым функционалом для отличной компании :)

## Установка
Установить зависимости проекта: `npm install`

Собрать проект: 
- Vite: `npm run build`
- Docker: `docker build -t vue-app .`

Запуск в режиме разработки: 
- Vite: `npm run dev`
- Docker: `docker-compose up vue-app-dev`

# Ссылки:

## Дизайн
https://www.figma.com/design/wlAMfFJpWzLsD3Ie5hPXym/%D0%9B%D0%B5%D0%BD%D0%B4%D0%B8%D0%BD%D0%B3-%D0%B4%D0%BB%D1%8F-%D0%A2%D0%97?node-id=1-190&t=uTwFUTL77ErAI35T-4

## На веб-приложение

Netlify: https://digital-landing.netlify.app/
 

Базовая структура CI/CD:
Стек: ESLint, Stylelint, Jest

Шаг 1) Тестирование
    npm run lint
    npm run lint:styles
    npm run test

Шаг 2) Сборка
    docker build -t vue-app .

Шаг 3) Деплой
    На Netlify деплой обновляется автоматически с ветки GitHub)


Оптимизация: 
    использование изображений в формате .webp, ленивая загрузка, использование миксин и глобальных переменных,
    асинхронная загрузка компонентов, использование v-once