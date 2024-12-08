# Лабораторная работа 5
В рамках лабораторной работы мне нужно было работать с Git.
## Задание 1 - Автоматизация проверки формата файлов при коммите
По этому заданию мне нужно было атоматизировать проверку файлов с использованием Git Hooks. 

Я зашла в папку .git/hooks и создала файл с названием pre-commit. В файле написала следующий скрипт:

```
#!/bin/bash

error=0

for file in $(git diff --cached --name-only); do
    if [[ "$file" != *.txt ]]; then
        echo "ERROR: Файл $file не имеет расширение .txt"
        error=1
        continue
    fi

    if ! grep -q '[^[:space:]]' "$file"; then
        echo "ERROR: Файл $file не содержит текста."
        error=1
    fi
done

if [ $error -eq 1 ]; then
    echo "Коммит отклонён"
    exit 1
fi

echo "Все проверки пройдены"
exit 0

```

Примеры использования:
* Файл не формата .txt
![image](https://github.com/user-attachments/assets/37fbaa2b-7be2-4691-b065-a462cdb0f760)

* Пустой файл формата .txt
![image](https://github.com/user-attachments/assets/e1c2d1f2-9c11-4ada-8cee-17174c413710)

* Файл формата .txt с тектсом
![Screenshot 2024-12-07 130107](https://github.com/user-attachments/assets/3917cad0-5f74-4b36-9ca0-4f2e740b4132)

## Задание 2
В задании 2 мне нужно было работать с Git Flow.
1. Git flow уже был установлен на моей машине
2. В корне репозитория я инициализировала Git flow и создала ветку для новой функциональности. Создала файл task_manager.py, внесла именения.
![Screenshot 2024-12-07 132902](https://github.com/user-attachments/assets/54514892-1656-4231-92ac-2e1f371de917)
3. Далее я объединила эту ветку с основной и завершила task-management
![Screenshot 2024-12-07 133254](https://github.com/user-attachments/assets/60718fe1-127d-4d3b-b343-88ef9e838100)
4. Создала релиз и обновила версию в файле version.txt
![Screenshot 2024-12-07 133523](https://github.com/user-attachments/assets/d6292763-c11b-4cae-b9a5-08d9e074f126)
5. Завершила релиз
![Screenshot 2024-12-07 134657](https://github.com/user-attachments/assets/7c50b2b4-5901-4173-8ad3-3c20f11dc045)

6. Далее я работала с hotfix. Создала hotfix-1.0.1. Внесла нужные изменения и завершила hotfix
![Screenshot 2024-12-08 185936](https://github.com/user-attachments/assets/32767f31-e7e1-4c7d-b853-45b2bf9af58a)
![Screenshot 2024-12-08 191058](https://github.com/user-attachments/assets/88d43389-026b-4779-8b47-afaad251bb01)


7. Отправила изменения на удаленный репозиторий
![Screenshot 2024-12-08 191120](https://github.com/user-attachments/assets/4ca98ab0-d2a4-4448-a77d-a27107e98635)


