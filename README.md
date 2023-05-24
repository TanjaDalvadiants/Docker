# PostgreSQL

* Необходимо подготовить приложение к тестированию на СУБД PostgreSQL с образом 12-alpine. Возьмите собранный JAR-файл db-api.jar, аналогично примеру на лекции положите рядом файл application.properties, но в строке: jdbc:mysql://... поменяйте mysql на postgresql.

* Hужно дописать остальные настройки: хост, порт, БД, имя пользователя и пароль.

* Hужно подготовить файл docker-compose.yml, в котором прописать настройки для запуска контейнера PostgreSQL. Всю информацию о его запуске вы найдёте на официальной странице образа на Docker Hub.

* Запустите сначала docker-compose up и только после того, как БД запустится, запустите целевое приложение: java -jar db-api.jar. Если нужно поменять порт запуска, по умолчанию он 9999, то добавьте в файл application.properties строку server.port=<нужный номер порта>.

* Если всё правильно, то приложение запустится и на GET http://localhost:9999/api/cards выдаст вам JSON с картами:

> [ 
   { 
      "id":1,
      "name":"Альфа-Карта Premium",
      "description":"Альфа-Карта вернёт ваши деньги",
      "imageUrl":"/alfa-card-premium.png"
   },
   { 
      "id":2,
      "name":"Alfa Travel Premium",
      "description":"Самая выгодная карта для путешествий",
      "imageUrl":"/alfa-card-travel.png"
   },
   { 
      "id":3,
      "name":"CashBack Premium",
      "description":"Заправь свою карту. Кешбэк на АЗС, в кафе и ресторанах",
      "imageUrl":"/alfa-card-cashback.png"
   }
]
В результате выполнения этой задачи вы должны положить в репозиторий следующие три файла (других файлов не должно быть):

db-api.jar,
application.properties,
docker-compose.yml.
Важно: для удаления всех данных и начала с чистого листа сделайте следующее:

docker-compose down в каталоге с файлом docker-compose.yml,
удалите каталог для хранения данных data,
запустите заново docker-compose up, после того как всё исправите.
Важно: команда docker-compose rm в каталоге с файлом docker-compose.yml удаляет сам контейнер.

