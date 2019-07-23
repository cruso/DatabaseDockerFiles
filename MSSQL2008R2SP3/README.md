# Dockerfile для деплоя MSSQL 2008

Данный файл позволяет сформировать образ c СУБД MSSQL 2008R2 SP3 на базе windows server core.
*Образ можно запустить только на docker для window в режиме "windows container".*

## Подготовка
1. Загрузить dockerfile и start.ps1(фалй start.ps1 нужен для запуска СУБД и взят из [репозитория Microsoft](https://github.com/Microsoft/mssql-docker/tree/master/windows/mssql-server-windows))
2. Создать рядом с dockerfile следующие каталоги:
    * net35
    * mssql2008r2
    * mssql2008r2sp3
3. Скачать ISO-образ для MSSQL2008R2 и распаковать в каталог mssql2008r2
3. Скачать пакет обновлений SP3 для MSSQL2008R2(он идет одинм файлом). Поместить файл в mssql2008r2sp3 и переименовать в setup.exe
4. Скачать ISO-образ для Windows Server 2019(триальную версию). Скопировать все содержимое каталога "sxs" из образа по пути "sources\sxs" в каталог net35. Данный шаг нужен, так как прежде чем устанавливать MSSQL 2008 R2 нужно установить в контейнер .Net Framework 3.5

## Сборка
`docker build -t mssql2008r2sp3 .`

## Запуск
`docker run -p 14567:1433 -it --rm --name mssql2008  mssql2008r2sp3`

## Остановка
`docker stop mssql2008`
