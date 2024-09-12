# Домашнее задание к занятию «Конфигурация приложений»

## Задание 1. Создать Deployment приложения и решить возникшую проблему с помощью ConfigMap. Добавить веб-страницу
- Создаем деплой и применяем его. В логах контейнера видим, что multitool не может подняться, потому что 80 порт занят nginx
  ![image](https://github.com/user-attachments/assets/2f2f9a15-b37e-464c-bc9d-7af925810500)
  ![image](https://github.com/user-attachments/assets/f5a8fab6-9246-4728-95ed-ea07f64a545c)

- Создаем configmap, остановим неверный деплой и поправим манифест
  ![image](https://github.com/user-attachments/assets/126b46bb-9899-4a90-b375-14165c822806)
  ![image](https://github.com/user-attachments/assets/93ae15ec-a892-4488-b769-b5b8deca7413)

- Применяем конфигмап и исправленный деплой
  ![image](https://github.com/user-attachments/assets/01ed672a-97a7-43fa-86d8-39bd4abed4cd)

- Правим конфиг, добавляем туда текст страницы nginx, создаем сервис для работы с вебом, применяем все и проверяем, что оно запустилось и корректно отдает результат
  ![image](https://github.com/user-attachments/assets/a610d0f5-3afa-4c9d-89ea-a1cc28e95b37)
  ![image](https://github.com/user-attachments/assets/c7d17d6e-2cb1-4209-84f7-d262008fddfa)
  ![image](https://github.com/user-attachments/assets/5523c440-ccd7-4f7a-a985-2586aa9ac848)
  ![image](https://github.com/user-attachments/assets/40c81c46-3cae-4759-be83-0a4fe533330b)

## Задание 2. Создать приложение с вашей веб-страницей, доступной по HTTPS

- Создаем деплоймент, сервис, конфигмап, сертификат с ключом и ингрес
  ![image](https://github.com/user-attachments/assets/3a8be5db-c9fb-4c40-ad9e-984ba0a15fdd)
  ![image](https://github.com/user-attachments/assets/5b621d43-f9da-4223-9a88-ee47f63135b3)
  ![image](https://github.com/user-attachments/assets/23005666-eb4f-42e4-b597-981deeb7d091)

*Ключ и сертификат конвертированы в base64 и добавлены в секрет*
  ```
root@home-ubuntu:/home/virus/8k8s# cat cert.crt | base64
LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUZCVENDQXUyZ0F3SUJBZ0lVUTRsbWdscmQ4
...

root@home-ubuntu:/home/virus/8k8s# cat key.key | base64
LS0tLS1CRUdJTiBQUklWQVRFIEtFWS0tLS0tCk1JSUpRd0lCQURBTkJna3Foa2lHOXcwQkFRRUZB
...
  ```

- Применяем все это и проверяем статус
  ![image](https://github.com/user-attachments/assets/6bb0911a-0b9a-4e6a-b176-9e7d33ffe814)
  ![image](https://github.com/user-attachments/assets/5994b915-76be-48ba-85ac-d6e9dc16bf4b)

- Добавим в /etc/hosts запись нашего хостнейма, которую использовали при генерации сертификата и проверим доступность по SSL
  ![image](https://github.com/user-attachments/assets/7527b007-cdb7-41ec-a1af-20daaa9cf746)
