# Pictures service

###  Сервис для обработки изображений
***
    
###  Структура  
    pictures
    ├── user_images_service
        ├── config  #папка с настройками базы данных и прочего
        ├── repositories #каталог схем таблиц бд(моделей)
        ├── routers #каталог функций - роутингов 
        ├── schemas #каталог  json схем
        ├── service #каталог различных функций проверки  , jwt token и обработки изображения
        ├── static #каталог стилей javascript и изображений
        ├── Dockerfile
        ├── main.py #отправная точка приложения
        ├── requirements.txt #пакеты которые нужно установить
        └── templates #папка с фронтендом(html)
    ├── data #папка с настойкми nginx
    |   ├── nginx
    |       └──app.conf #файл с настойкми nginx
    ├── .env #файл с секретными переменными (создается при деплое sudo nano .env)
    └─  docker-compose.yml
### перед деплоем 
 0. В файле init-letsencrypt.sh в переменной domains воодим свое доменное имя example.ru www.example.ru
 1 .  В папке data/nginx после значения server_name прописываем свое доменное имя и каждом месте где стоит example.com также заменяем на свое
### comands deploy
 0. даем имя проекту 1.Выбор образа/загрузочного диска ставим Ubuntu 2. в поле логин вводим любое   имя , можно просто -admin
 
 1.  ssh-keygen -t rsa -b 2048 генерация ключа для яндекс клайуд
  попросит придумать кодовое слово - это будет ваш пароль для доступа
  и попросит повторить

 2.  cat /home/gleb/.ssh/id_rsa(у вас будет свой путь для сохранения описаный в консоли после выполнения первой команды)  скопировать ключ ssh
 3. копируем ключ из результата команды номер 2 и вставляем в поле  SSH-ключ на странице яндекс клауд
 4. Нажимаем создать bm и после отображения кликаем на наш проект (дожидаемся status -  Running)
 5. Идем в консоль своего компьютера и вводим  ssh (наш логин и пункта 0.2)@(Публичный IPv4-он отображается на странице яндексклайд нашего bm 
 )
  пример - ssh admin@84.201.179.68
 5. попросит ввести кодовое слово для этого аккаунта (вести кодовое слово из пункта 1)
 6. Если в пункте 5 все удачно - вы через консоль зашли в аккаунт яндекс клауд вашего bm 
 7. Вводим команду в консоли sudo apt get install git docker docker-compose -y  нажимаем enter
 8. Вводим команду git clone https://github.com/gleb89/pictures.git или вашу ссылку на репозиторий гит-хаб \нажимаем enter
 9. Вводим команду  cd pictures/ нажимаем enter
 10. Вводим команду  sudo nano .env
  откроется окно 
  вставить туда переменные со своими значениями(что связанно с POSTGRES пишем произвольные значения,можно оставить как есть)
  id_client_google и secret_key_google_auth это ваши ключи google auth
    POSTGRES_USER=glebhleb
    POSTGRES_PASSWORD=glebhleb2
    POSTGRES_DB=glebhleb
    id_client_google=286255588660-rgio676kjntofk12u3b1kg7ok61fkbdo.apps.googleusercontent.com
    secret_key_google_auth=fDLe97luPpQhjE0nIjEmZKkk
11. Вводим команду docker-compose sudo up -d --build нажимаем enter 
12. Переходим в браузер и проверяем работу сайта






