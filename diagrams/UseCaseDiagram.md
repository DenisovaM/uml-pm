# Use Case Диаграмма

# MVP
- лента;
- выбор ЯП задачи;
- регистрация и вход в аккаунт;
- отправка писем на почту;
- профиль пользователя + настройка профиля;
- поиск задачи;
- блог ("ретвиты" решения задачи в свой профиль);
- редактор кода + отправка задачи;
- рестинг сложности задач и отметка о статусе решения задачи.
  
![use](https://www.plantuml.com/plantuml/svg/fLNBQjj05DthAuPil8e_e8iI20qK0YbntBsGhkMXgcGqKjfb71fQI22GJLTjsZzmqne_KjU_CFD7EJEIzOusNNWqC_UUSy_SEOCFH6n7SVBUPuaWo-hPJXn6mZ8VjYU_oRbSo9cwmFUtNAgfkiHyYTy_-I1dSYCtwbgkcDnYur7T8Da4r2K0MEynMx1X4977HKmHkKD1KSx-zN-PJwkyFPp1iGK9AvkWnhrcL5Fv5oCgCFa8_0RJQyDmHEI-vVIXXEXGXTKDzcuDTC2zO3Wf0U-Gj8A-fGaVXzxhe4l8rcnyaaiS9sNKGjv4uOZxb9y5o9z8kqAoRWgq0p1d61QWckTRgrIJVKw7OplmAZtuWPm_WA-rk5A73L5JnYkNnpiP7VhX2ysgFcS7rkhFRF6kXFcEWbkZ_065qJocEwk-x8wHQgR0FIKH-kTqCgeHt4ChRa6kc-MEUE3Mik_Wc5-GTy7KhLnWiPOpatiu3aD1n-XBOdlKYe3FPaOfccek7KrApMVgPqG3yic9UU0Do8wSySaavc7GPJTrbT7gti-DbwRw5d2YSYjA1XY4Vg9PSOqH7Wf5S3Xt12lSpS9HyqtLD_RtN-RURebbvgsIrfvJTSc0oapT3EIbMZ1bLvUinVgL47l1w6CCApGeaWb8yjj-fe29zLgXcRTCnYvL5zzfBYfNebd18jf-zy_brZpD-icaNqWjCdkb9wkvIXrgw4AuwcG67XuuVkAIrUMTj7XJL5xX00F-19u0 "use")



### UC Зарегистрироваться
| UC | Зарегистрироваться |
| ------------- | ------------- |
| Основные лица | Незарегистрированный пользователь |
| Цель | Регистрация в системе |
| Триггер | Решение пользователя о регистрации  |
| Результат | Успешная регистрация незарегистрированного пользователя |

| Действия Актора | Отклик системы |
| ------------- | ------------- |
| 1. Нажатие кнопки "Зарегистрироваться" |   |
|   |  2. Открытие формы регистрации. Поля:<br/>- логин;<br/>- почта;<br/>- пароль;<br/>- повтор пароля.<br/>Кнопка "Зарегистрироваться"|
| 3. Заполнение полей. Нажатие кнопки "Зарегистрироваться" |   |
|  | 4. Проверка корректности данных и наличия пользоватля в БД. Если пользователь в базе есть, то выполняется Исключение 1  |
|  | 5. Если всё корректно и пользователь не зарегистрирован, то отправляется письмо со ссылкой для авторизации на почту |
| 6. Открытие письма, переход по ссылке |  |
|  | 7. Активация пользователя. Создание ЛК и перенаправление |

Исключение 1
| Действия Актора | Отклик системы |
| ------------- | ------------- |
|  | 1. Если пользователь уже зарегистрирован, то вывод информации об этом  |
| 2. Исправление ошибки или переход ко входу в ЛК |   |
|  | 3. Если пользователем введены некорректные данные, то вывод информации об этом  |
| 4. Исправление ошибки. Повторное нажатие кнопки "Зарегистрироваться" |   |

