NXT Fitout Technical Services — сайт одним файлом + Firebase
============================================================

ЧТО ВНУТРИ
index.html       весь сайт (6 страниц: главная, портфолио, о нас, контакты,
                 конфиденциальность, условия; 3 языка EN/RU/AR; подвал)
firestore.rules  правила безопасности базы данных
assets/images    сюда фото и логотипы
assets/video     сюда видео

ПУБЛИКАЦИЯ
Загрузите папку целиком в GitHub Pages (или любой хостинг). Это обычный
статический сайт: ничего запускать и собирать не нужно.

ПОДКЛЮЧЕНИЕ FIREBASE (один раз)
1. console.firebase.google.com -> Add project.
2. Build -> Authentication -> Get started -> Sign-in method -> Google -> Enable.
3. Authentication -> Settings -> Authorized domains -> Add domain:
   адрес вашего сайта (например ваш-логин.github.io).
4. Build -> Firestore Database -> Create database.
5. Firestore -> Rules -> вставьте содержимое firestore.rules -> Publish.
6. Project settings (шестерёнка) -> Your apps -> Web (</>) -> Register app.
   Скопируйте объект firebaseConfig.
7. Откройте index.html, найдите блок "YOUR SETTINGS" (внизу файла) и вставьте
   значения в поле firebase: apiKey, authDomain, projectId, ...
Готово: вход через Google и сохранение заявок включатся сами.

ГДЕ ВИДЕТЬ ЗАЯВКИ И КЛИЕНТОВ
Firebase Console -> Firestore Database:
  requests  — заявки (имя, телефон, текст, email, статус, язык, время)
  users     — клиенты, вошедшие через Google (поле status)
Статус у всех "business" (показывается как «Бизнесмен»). Чтобы изменить статус
конкретному клиенту, поменяйте поле status в его документе users/<uid>.
Название статуса на сайте: в index.html ключ "auth.status" (EN/RU/AR).

ОКОШКО В ПРАВОМ УГЛУ (необязательно)
Вход работает через кнопку «Продолжить через Google». Чтобы ещё появлялось
маленькое окошко Google в правом верхнем углу, вставьте в googleClientId
"Web client ID": Firebase Console -> Authentication -> Sign-in method ->
Google -> Web SDK configuration.

ИНСТАГРАМ И НОМЕР
В том же блоке "YOUR SETTINGS": instagram и whatsapp.

ЛОГОТИПЫ, ФОТО, ВИДЕО
  assets/images/logo-black.png  (шапка и главная)
  assets/images/logo-white.png  (подвал)
  assets/images/case-1.jpg ... case-6.jpg   (фото проектов)
  assets/video/case-2.mp4, case-5.mp4       (видео-проекты)
  assets/video/promo.mp4 и assets/images/video-poster.jpg  (рекламное видео)

ПЕРЕД ЗАПУСКОМ ПРОВЕРЬТЕ
- Описания услуг и этапы работы — общие, поправьте под реальные.
- Политика конфиденциальности и условия — типовой шаблон, покажите юристу.
- Пока Firebase не заполнен, сайт работает в демо-режиме: кнопок входа нет,
  форма открывает WhatsApp.
