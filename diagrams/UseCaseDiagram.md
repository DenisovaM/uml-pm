# Use Case диаграмма

# MVP
- лента;
- выбор ЯП задачи;
- регистрация и вход в аккаунт;
- отправка писем на почту;
- профиль пользователя + редактирование профиля;
- поиск задачи;
- блог ("ретвиты" решения задачи в свой профиль);
- редактор кода + отправка решения задачи;
- рейтинг сложности задач;
- отметка о статусе решения задачи.
  
![use](https://www.plantuml.com/plantuml/svg/fPRDRfj04CVlVefLBZdP3z1352bAf4gHNCLnxmZM61M3nKBQOsAtJQjOYfHBJqtx2DID6-gllCBk6_NFWZ7BXttemR2xC_ERsM5cv6FcQvuV36mICDeur7JVzLX3liW1_yvd_9c7uXhltpmIDsA4TOJVcazvo5Ty9UxuNy9VSB0G4oXBWHZ10Fi3eZ7ITJngMiod7ZMwZ7eP_Tl_aYzKxY6ke6kCiaQwW8yVCL7Sy2MUy43u0lOhBEyauOnIuwr5t-SiTaI5tGHdzzAqOvbETvWpV12VeFP4-9J0eJG6PYd6KltSDLyxkm9xaGSVUOJh9HxYmDvuRi-oQSxm9w1FoD0S-7o-8ZwhWfmQbb-6bBpZAyTKSSkZpFUbnjxbR1xXCEQ7S1Z5gI1ndiINEA69znKFqn2WCiDxdbw-GntZWZBNlgBjNW7xWE-yWCMV6kXKlTMa6dZfLbmIL7m6FYzVxynoZ8euVi7DDH7t_1cREG-bxadVTHazrnmpq4nQQO4g3MLcbeXzb2GWALtfFmLrg4rrttBC3jKylTyU-fRhx2fMMK9nrOrn62gPoPL8nxM3c7JIrpoq5lNG4vREY9e946RYQvPMSIl6IFaQPRwkgxsstwVU_jfHK3KnIjGcq28B2Lg3jamwKsstBNrMg8pasxY30NNyEloZ-9o6iXzrUgNPWUPJbPND5EBsofEiUD1i7cKJfKAMZWmLMXXYwfOqWs7pA1qUHL7EMLcaJ8_S420jHKHU4Vh1HpTLEyxwfCQ1b6qMCNeJqPQhI5FSLbhT4tMwXQOdhM3OsWPIzWcXshq4EfQZsu516xjw9m6N7TR7aWqWqjfjMPD9fTbABIEXHRKjiweDzfXKbliUcsCyy5VX7m00 "use")


### UC Зарегистрироваться
| UC | Зарегистрироваться |
| ------------- | ------------- |
| Основные лица | Незарегистрированный пользователь |
| Цель | Регистрация в системе |
| Триггер | Решение пользователя о регистрации  |
| Результат | Успешная регистрация незарегистрированного пользователя |

| Действия актора | Отклик системы |
| ------------- | ------------- |
| 1. Нажатие кнопки "Зарегистрироваться" |   |
|   |  2. Открытие формы регистрации. Поля:<br/>- логин;<br/>- почта;<br/>- пароль;<br/>- повтор пароля.<br/>Кнопка "Зарегистрироваться"|
| 3. Заполнение полей. Нажатие кнопки "Зарегистрироваться" |   |
|  | 4. Проверка корректности данных и наличия пользоватля в БД. Если пользователь в базе есть, то выполняется Исключение 1  |
|  | 5. Если всё корректно и пользователь не зарегистрирован, то отправляется письмо со ссылкой для авторизации на почту |
| 6. Открытие письма, переход по ссылке |  |
|  | 7. Активация пользователя. Создание ЛК и перенаправление |

Исключение 1
| Действия актора | Отклик системы |
| ------------- | ------------- |
|  | 1. Если пользователь уже зарегистрирован, то вывод информации об этом  |
| 2. Исправление ошибки или переход ко входу в ЛК |   |
|  | 3. Если пользователем введены некорректные данные, то вывод информации об этом  |
| 4. Исправление ошибки. Повторное нажатие кнопки "Зарегистрироваться" |   |

