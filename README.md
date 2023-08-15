# Домашнее задание к занятию 3 «Резервное копирование»
## Задание 1

```
rsync -avPh --checksum --exclude=".*" . /tmp/backup
```

где:  

- a (или --archive): выполняет рекурсивную копию и сохраняет атрибуты файлов и директорий;
- v (или --verbose): выводит подробную информацию о процессе синхронизации;
- P (или --progress): отображает прогресс передачи файлов и позволяет возобновлять прерванные операции;
- h (или --human-readable): выводит размеры файлов в human-readable формате
- --checksum: вычисляет хэш-суммы для всех файлов и сравнивает их между источником и приемником.
- --exclude=".*": исключает все директории, начинающиеся с точки

## Задание 2