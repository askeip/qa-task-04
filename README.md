# «Консольный твиттер»

На днях Илье пришли его новенькие наручные часы. Те самые,
с небольшим дисплеем, двумя кнопками и bluetooth. Обманывать шагомер и читать
СМСки Илья научился в тот же вечер. Его новая цель — выводить на экран
последние твиты на заданную тему. Чтобы подружить твиттер и часы, достаточно
сходить за списком твитов в API и вывести их на консоль. Всё остальное - дело техники!

Список твитов получаем запросом `https://api.twitter.com/1.1/search/tweets.json?q=%23urfu-testing-2016`.
В ответе вернется массив, из каждого твита возьмём только дату публикации `created_at` и текст `text`.
```json
[
    {
        "created_at": "2017-04-25T15:09:10.609Z",
        "text": "Библиотека #nock позволяет не только удобно писать тесты, но и вести разработку фронтеда, в то время, когда бекенд ещё только проектируется! #urfu-testing-2016"
    },
    {
        "created_at": "2016-04-25T15:09:10.609Z",
        "text": "Для подмены модулей раньше я использовал #mockery, а сейчас всей душой полюбил #proxyquire. #urfu-testing-2016"
    }
]
```

Текст твита выводится на консоль как есть, а вот дату Илья хочет видеть в следующем виде:
  1. Если сообщение написано сегодня, то выводим только время: `"2017-04-26T15:09:10.609Z" -> "15:09"`
  2. Вчерашние сообщения выводятся так: `"2017-04-25T15:09:10.609Z" -> "вчера в 15:09"`
  3. Более старые твиты дополняются датой: `"2017-03-25T15:09:10.609Z" -> "25 марта в 15:09"`
  4. Если сообщение написано в плошлом году, то это нужно обязательно упомянуть: `"2016-03-25T16:09:10.609Z" -> "25 марта 2016 года в 15:09"`

Форматирование даты нужно реализовать в файле `formatDate.js`. Работу с API
твиттера и консольный вывод пишем в `twitter.js`. В нашем примере на консоли
будет следующий текст:
```
вчера в 15:09
"Библиотека #nock позволяет не только удобно писать тесты, но и вести разработку фронтеда в то время, когда бекенд ещё только проектируется! #urfu-testing-2016"

5 апреля 2016 года в 15:09
"Для подмены модулей раньше я использовал #mockery, а сейчас всей душой полюбил #proxyquire. #urfu-testing-2016"
```

### Бонусное задание
Для тех смельчаков, кому работа с сетевыми запросами и подмена модулей в тесте
показались легкими, Илья придумал усложнение. Сделать из твитов бегущую строку.
Для этого нужно выводить на консоль по одному символу раз в 100ms.

### Почитать
  * [Слайды лекции про мок-объекты](https://urfu-2016.github.io/testing-slides/06-mock/#/)
  * [Как сделать запрос по сети](https://www.npmjs.com/package/request)
  * [Как подменить настоящий модуль тестовым](https://www.npmjs.com/package/proxyquire)
  * [Как подменить настоящий сетевой запрос тестовым](https://www.npmjs.com/package/nock)
  * [Как написать тестовый модуль проще](http://sinonjs.org/)
  * [Как делать операции раз в 100ms](https://learn.javascript.ru/settimeout-setinterval)
  * [Как отправить пуллреквест](https://urfu-2016.github.io/javascript-slides/01-intro/#/37)

![bands](https://cloud.githubusercontent.com/assets/1654243/25427135/14363a82-2a8b-11e7-85a3-b8b5e0c97b3a.jpg)
