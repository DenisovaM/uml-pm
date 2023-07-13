
## API 


## Version 
Текущая версия `v1`

### Получение списка задач

## `` GET /tasks ``

Параметры 
| Параметр | Обязательность | Описание | Тип данных |
| ------------- | ------------- |  ------------- | ------------- |
| level | Не обязательно | Отображение задач с определённым уровнем сложности: "easy/medium/hard" | string |
| status | Не обязательно | Отображение задач с определённым статусом: "решено/не решено" | string |
| title | Не обязательно | Отображение задачи с определённым названием | string |
| limit | Не обязательно | Максимальное количество возвращаемых элементов. По умолчанию 20 | integer |

Пример запроса
`` GET "<baseurl>/v1/tasks?level=easy&status=0&title=taskname&limit=20" ``

Ответ

```bash
{
    "tasks": [
               {
                "taskID": 1,   
                "title": "Название задачи 1",
                "level": "Уровень сложности задачи",
                "status": "решено" 
               },
               {
                "taskID": 2,
                "title": "Название задачи 2",
                "level": "Уровень сложности задачи",
                "status": "не решено"
                },
              ...
              ]
}
```

| Параметр | Описание | Тип данных |
| ------------- | ------------- |  ------------- |  
| taskID | Номер задачи, отображаемый в списке задач | integer |
| title | Название задачи, отображаемое в списке задач | string |
| level | Уровень сложности задачи, отображаемый в списке задач | string |
| status | Факт того, решена ли задача пользователем. Статусы: "решено/не решено" | string |

Коды ответа

| Код | Описание |
| ------------- | ------------- |
| 200 | ОК |
| 404 | Элемент не существует |



OpenAPI 


```bash
paths:
  /tasks:
    get:
      summary: Получение списка задач
      description: Возвращает список задач, удовлетворяющих указанным параметрам.
      parameters:
        - name: level
          in: query
          description: Отображение задач с определённым уровнем сложности
          schema:
            type: string
          example: easy
        - name: status
          in: query
          description: Отображение задач с определённым статусом
          schema:
            type: string
          example: решено
        - name: title
          in: query
          description: Отображение задачи с определённым названием
          schema:
            type: string
          example: taskname
        - name: limit
          in: query
          description: Максимальное количество возвращаемых элементов
          schema:
            type: integer
            minimum: 1
            maximum: 100
            default: 20
      responses:
        '200':
          description: Successful response
          content:
            application/json:
              schema:
                type: object
                properties:
                  tasks:
                    type: array
                    items:
                      type: object
                      properties:
                        taskID:
                          type: integer
                          description: The ID of the task
                        title:
                          type: string
                          description: The title of the task
                        level:
                          type: string
                          description: The difficulty level of the task
                        status:
                          type: string
                          description: The status of the task
        '404':
          description: Элемент не существует
```


### Просмотр задачи

## `` GET /tasks/{id} ``

Пример запроса
`` GET "<baseurl>/v1/tasks/1111" ``

Ответ

```bash
{
  "taskID": 1,
  "title": "Задача 1",
  "description": "Описание условия задачи 1",
   "level": "Уровень сложности задачи",
  "examples": [
    {
      "input": "Входные данные примера 1",
      "output": "Ожидаемый результат примера 1",
       "explanation": "Объяснения"
    },
    {
      "input": "Входные данные примера 2",
      "output": "Ожидаемый результат примера 2",
       "explanation": "Объяснения"
    },
    {
      "input": "Входные данные примера 3",
      "output": "Ожидаемый результат примера 3",
       "explanation": "Объяснения"
    }
  ],
  "status": "не решено",
   "languages":[
    {
    "language": "name"
     }
     ...
   ],
   "solutionTemplate": "class Solution {...}",
   "timeRestrict": "ограничения",
   "volumeRestrict": "ограничения"
}

```

| Параметр | Описание | Тип данных |
| ------------- | ------------- |  ------------- |  
| taskID | Номер задачи, отображаемый в списке задач | int64 |
| title | Название задачи, отображаемое в списке задач | string |
| description | Описание условий задачи | string |
| level | Уровень сложности задачи, отображаемый в списке задач. Уровни сложности: "easy/medium/hard" | string |
| input | Строка с входными данными тестового кейса | string |
| output | Строка с выходными данными тестового кейса | string |
| explanation | Строка с пояснением данных тестового кейса | string |
| language | Названия возможного ЯП задачи | string |
| status | Факт того, решена ли задача пользователем/ Статусы: "решено/не решено" | string |
| solutionTemplate | Скелет кода для пользователя | string |
| timeRestrict | Ограничение по времени | string |
| volumeRestrict | Ограничение по памяти | string |


Коды ответа

| Код | Описание |
| ------------- | ------------- |
| 200 | ОК |
| 403 | Нет прав доступа |
| 404 | Элемент не существует |


OpenAPI 3.0.0
```bash
paths:
  /tasks/{id}:
    get:
      summary: Просмотр задачи
      description: Возвращает информацию о задаче по указанному идентификатору.
      parameters:
        - name: id
          in: path
          description: Идентификатор задачи
          required: true
          schema:
            type: integer
            format: int64
      responses:
        '200':
          description: Successful response
          content:
            application/json:
              schema:
                type: object
                properties:
                  taskID:
                    type: integer
                    description: The ID of the task
                  title:
                    type: string
                    description: The title of the task
                  description:
                    type: string
                    description: The description of the task
                  level:
                    type: string
                    description: The difficulty level of the task
                  examples:
                    type: array
                    items:
                      type: object
                      properties:
                        input:
                          type: string
                          description: The input data of the example
                        output:
                          type: string
                          description: The expected output of the example
                        explanation:
                          type: string
                          description: Explanation of the example
                  status:
                    type: string
                    description: The status of the task
                  languages:
                    type: array
                    items:
                      type: object
                      properties:
                        language:
                          type: string
                          description: The name of the programming language
                  solutionTemplate:
                    type: string
                    description: The solution template for the task
                  timeRestrict:
                    type: string
                    description: The time restriction for the task
                  volumeRestrict:
                    type: string
                    description: The volume restriction for the task
        '403':
          description: Access denied
        '404':
          description: Element not found
```


### Отправка попытки решения

## `` POST /tasks/{id}/attempt ``


### Просмотр попыток решения

## `` GET /tasks/{id}/attempts/{id} ``

Параметры 
| Параметр | Обязательность | Описание | Тип данных |
| ------------- | ------------- |  ------------- | ------------- |
| limit | Не обязательно | Максимальное количество возвращаемых элементов. По умолчанию 20 | integer |

Пример запроса
`` GET "<baseurl>/v1/tasks/1111/attempts/1111?limit=20" ``
