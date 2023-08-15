# Домашнее задание к занятию 3 «Резервное копирование»
## Задание 1

```
rsync /home -avPh --checksum --exclude=".*" . /tmp/backup
```

где:  

- /home - домашняя директория
- a (или --archive): выполняет рекурсивную копию и сохраняет атрибуты файлов и директорий;
- v (или --verbose): выводит подробную информацию о процессе синхронизации;
- P (или --progress): отображает прогресс передачи файлов и позволяет возобновлять прерванные операции;
- h (или --human-readable): выводит размеры файлов в human-readable формате
- --checksum: вычисляет хэш-суммы для всех файлов и сравнивает их между источником и приемником.
- --exclude=".*": исключает все директории, начинающиеся с точки

![rsync](https://github.com/OhotinDY/sflt-03/blob/main/rsync.png)
![tmp](https://github.com/OhotinDY/sflt-03/blob/main/tmp.png)

## Задание 2
### Скрипт backup.sh

```
#!/bin/bash

# Путь к домашней директории
source_dir="/home"

# Путь к директории резервной копии
backup_dir="/tmp/backup"

# Выполнение rsync для создания зеркальной копии
rsync -avPh --checksum "$source_dir" "$backup_dir"

# Проверка кода возврата rsync и запись сообщения в журнал
if [ $? -eq 0 ]; then
   logger "Резервная копия создана"
else
   logger "Ошибка при создании резервной копии"
fi
```
### Пропишем строку в планировщик (crontab -e)

```
22 10 * * * /home/backup.sh
```

![log](https://github.com/OhotinDY/sflt-03/blob/main/log.png)
