# deepstroy-doc
Здесь представлена документация по запуску приложения

### Prerequisites
Требования
1. `docker`
2. `git`
3. `node` (https://nodejs.org/dist/v18.16.1/node-v18.16.1-x64.msi)

### Как запустить локально

#### Доступ до сервисов

| Service                       | Source           |
|-------------------------------|------------------|
| deesptroy-api                 | localhost:9200   |
| deepstroy-s3                  | localhost:9212   |
| deepstroy-rabbitmq            | localhost:9214   |
| deepstroy-ui                  | localhost:5174   |

Перейдите в папку, где вы расположите репозитории для запуска проекта и склонируйте необходимые проекты
```bash
git clone https://github.com/TourmalineCore/deepstroy-api.git
```
```bash
git clone https://github.com/TourmalineCore/deepstroy-model-service.git
```
```bash
git clone https://github.com/TourmalineCore/deepstroy-ui.git
```
Далее с помощью докера запустите сервисы api и model-service
```bash
docker compose -f deepstroy-api/docker-compose.yml up --build run-api-locally
```
```bash
docker compose -f deepstroy-model-service/docker-compose.yml up --build run-api-locally
```
Для запуска ui выполните следующие команды
```bash
cd deepstroy-ui
```
```bash
npm ci
```
```bash
npm run start
```
Также необходимо выполнить некоторую настройку s3. после поднятия контейнеров, перейдите по ссылке - 
http://localhost:9212. Вы попадите на страницу авторизации в s3, далее нужно выполнить следующие шаги:
1. Введите username: deepstroy, password: deepstroy. 
2. Затем на главной странице в левом сайдбаре перейдите во вкладку "Buckets".
3. Нажмите на бакет "deepstroy", во вкладке summary.
4. Нажмите на "карандашь" рядом с полем "Access Policy". появится всплывающее окно "Change Access Policy" в выпадающем списке "Access Policy" выберите Public

Настройка проекта готова, теперь вы можете получить досутп до сервисов с помощью ui с таким адресом http://localhost:5174

