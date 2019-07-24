# Деплой MSSQL 2017

## Запуск
`docker run -d -p 1433:1433 --rm --name mssql2017 -e sa_password=only4Change -e ACCEPT_EULA=Y microsoft/mssql-server-windows-developer`

## Остановка
`docker stop mssql2017`
