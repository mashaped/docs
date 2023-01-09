# Example of unrolling a server in a Docker container on Yandex Cloud

>В данном примере сервер пишет полученные сообщения в журнал и выводит их в консоль виртуальной машины

Перед началом работы необходимо:

1. [Cоздать учетную запись в Яндекс](#yandexAccount)
2. [Сгенерировать SSH ключ](#keySSH)

Варианты запуска python webhook server:

* [Cоздание сервера с использованием Yandex и docker-compose файла](#yandexDocker-compose)
* [Cоздание сервера с использованием docker](#docker)
* [Cоздание сервера с использованием docker-compose файла](#docker-compose)

---
## 1. Cоздать учетную запись в Яндекс {#yandexAccount}

* Необходимо создать яндекс аккаунт [Яндекс](https://passport.yandex.ru/registration)
* Войти в [Yandex cloud](https://auth.cloud.yandex.ru) с помощью ранее сознаного аккаунта.

    >Выйдет предложение создать первое облако, соглашаемся и создаем.

* Для работы с сервисами Яндекс необходимо произвести __создание платежного аккаунта__. 

    >Необходимо привязать карту, будет списание и возврат небольшой суммы.

    **Внимание!** При регистрации вы должны указывать карту той страны, резидентом которой вы 	являетесь. 
    
    >Подробно можно прочитать [здесь](https://cloud.yandex.ru/docs/billing/operations/create-new-account).

* По завершению регистрации ваш аккаунт должен иметь статус <span style="color:green"> __Active__</span>. 

    >Подробно о пробном периоде и гранте можно прочитать [здесь](https://cloud.yandex.ru/docs/getting-started/usage-grant).

---

## 2. Сгенерировать SSH ключ {#keySSH}

Для создания ключа можно воспользоваться программами [PuTTY](https://www.putty.org) или [OpenSSH](https://www.openssh.com), мы будем использовать документацию [Яндекса](https://cloud.yandex.ru/docs/compute/operations/vm-connect/ssh)
	
Пример для  Linux/MacOS:

* В темрминале выполнить команду 
    ```
    ssh-keygen -t ed25519
    ```

* Укажите путь до папки в которую необходимо сохранить ключ и название ключа. 

    >Для нашего примера: /Users/GreenAPI/ssh/yc_rsa

* введите фразу (фактически пароль) для генерации ключа

* в папке будут созданы два файла: 

    yc_rsa.pub - публичная чаcть ключа

    yc_rsa - приватная чаcть ключа

---

## Cоздание сервера с использованием Yandex и docker-compose файла {#yandexDocker-compose}


1.  Создание виртуальной машины

    >Все сервиры -> инфраструктура и сеть -> Compute Cloud


2.  Настройка виртуальной машины

    >Укажите имя, описание, [зону доступности](https://cloud.yandex.ru/docs/overview/concepts/geo-scope).

    * В пункте **Выбор образа загрузочного диска** выберете раздел **Container Solution** -> настроить -> Docker-compose,
    необходимо вставить код из файла [docker-compose.yml](https://github.com/green-api/whatsapp-api-webhook-server-python/blob/master/docker-compose.yml)

        >Далее происходит настройка мощности вашей виртуальной машины, значения выбираются в зависимости от ваших потребностей, но для примера работы сервера достаточно минимальных настроек.

        **Внимание!** Значение поля [__прерываемая__](https://cloud.yandex.ru/docs/compute/concepts/preemptible-vm) значит, что при перезапуске машины адрес сервера будет меняться.

    * Создате сервисный аккаунт
    >Для управления машиной из командной строки необходима роль [editor](https://cloud.yandex.ru/docs/iam/concepts/access-control/roles).

    * Укажите логин для пользователя виртуальной машины.

    * Откройте фаил yc_rsa.pub и скопируте содержимое в поле SSH ключ.


3.  Доступ к виртуальной машине

    * Для получения доступа к виртуальной машине необходимо ввести команду в терминале компьютера
        
        >ssh [-i identity_file] [user@]host[:port]
        >
        >identity_file - путь до приватной части SSH ключа
        >
        >user - имя пользователя (логин - указывали в настройках)
        >
        >host - внешний адрес хоста находится в свойствах вашей виртуальной машины
        
        Для нашего примера команда будет иметь следующий вид:
        >ssh -i /Users/GreenAPI/ssh/yc_rsa green-api@84.252.137.226

    * После ввода команды может выйти сообщение "Подлинность хоста не может быть установлена, продолжаем" (yes), введите пароль (фраза, которую использовали при создании [SSH ключа](#keySSH)) командная строка изменится green-api@webhook-server:~$ (вы вошли на виртуальную машину).


4. Запуск контейнера

    При использовании данного метода виртуальная машина сама скачает все необходимые файлы и запустит контейнер.

    >Для просмотра вебхуков вам необходимо настроить ваш инстанас в консоле [кабинета Green-Api](https://console.green-api.com/instanceList/)  на работу с сервером, указать внешний ip адрес машины и порт.

    >Адрес отправки уведомлений (URL) | http://158.160.6.161:8080 (пример)


5. Просмотр полученных сообщений

    * Просмотреть запущенные контейнеры 
        ```
        docker ps
        ```

    * Посмотреть логи запущеного контейнера
        
        >docker logs [OPTIONS] CONTAINER - показать лог контейнера
        >
        >CONTAINER - id или имя запущенного контейнера
        >
        >OPTIONS - -f, --follow - опция непрерывного отслеживания вывода лога 
        >
        >(Ctrl + C - выход из режима)
        
        Для нашего примера строка будет выглядить так:
        
        >docker logs --follow webhookserver
        
---

## Cоздание сервера с использованием docker {#docker}


1.  Создание виртуальной машины

    >Все сервиры -> инфраструктура и сеть -> Compute Cloud


2.  Настройка виртуальной машины

    >Укажите имя, описание, [зону доступности](https://cloud.yandex.ru/docs/overview/concepts/geo-scope).

    * В пункте **Выбор образа загрузочного диска** выберете раздел **Операционные системы** -> Ubuntu

        >В нашем примере мы будем запускать виртуальную машину с использованием OS Ubuntu

    * В пункте **Диски и файловые хранилища** укажите размер диска 10 Гб.

        >Далее происходит настройка мощности вашей виртуальной машины, значения выбираются в зависимости от ваших потребностей, но для примера работы сервера достаточно минимальных настроек.

        **Внимание!** Значение поля [__прерываемая__](https://cloud.yandex.ru/docs/compute/concepts/preemptible-vm) значит, что при перезапуске машины адрес сервера будет меняться.

    * Создате сервисный аккаунт
    >Для управления машиной из командной строки необходима роль [editor](https://cloud.yandex.ru/docs/iam/concepts/access-control/roles).

    * Укажите логин для пользователя виртуальной машины.

    * Откройте фаил yc_rsa.pub и скопируте содержимое в поле SSH ключ.


3.  Доступ к виртуальной машине

    * Для получения доступа к виртуальной машине необходимо ввести команду в терминале компьютера
        
        >ssh [-i identity_file] [user@]host[:port]
        >
        >identity_file - путь до приватной части SSH ключа
        >
        >user - имя пользователя (логин - указывали в настройках)
        >
        >host - внешний адрес хоста находится в свойствах вашей виртуальной машины
        
        Для нашего примера команда будет иметь следующий вид:
        >ssh -i /Users/GreenAPI/ssh/yc_rsa green-api@84.252.137.226
        
    * После ввода команды может выйти сообщение "Подлинность хоста не может быть установлена, продолжаем" (yes), введите пароль (фраза, которую использовали при создании [SSH ключа](#keySSH)) командная строка изменится green-api@webhook-server:~$ (вы вошли на виртуальную машину).


4. Запуск контейнера

    При использовании данного метода виртуальная машина не скачает и не установит [docker](https://docs.docker.com/engine/install/ubuntu/), все необходимо сделать вручную.

    >Для просмотра вебхуков вам необходимо настроить ваш инстанас в консоле [кабинета Green-Api](https://console.green-api.com/instanceList/)  на работу с сервером, указать внешний ip адрес машины и порт.

    >Адрес отправки уведомлений (URL) | http://158.160.6.161:8080 (пример)

    * Введите следующие команды в терминале виртуальной машины:
        ```
        sudo apt-get update
        ```
        ```
        sudo apt-get install \
            ca-certificates \
            curl \
            gnupg \
            lsb-release
        ```
        ```
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
        ```
        ```
        echo \
        "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
        $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
        ```
        ```
        sudo apt-get update
        ```
        ```
        sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin 
        ```

    * Необходимо войти в docker под своей учетной записью.

        >Для получения [образа](https://hub.docker.com/r/greenapi/whatsapp-api-webhook-server-python) с сайта [Docker Hub](https://hub.docker.com)
        у вас должна быть учетная запись.

        ```
        sudo docker login 
        ```
        ```
        sudo docker pull greenapi/whatsapp-api-webhook-server-python
        ```

    * Запуск контейнера в фоне:
        ```
        sudo docker run --publish 8080:80 -itd greenapi/whatsapp-api-webhook-server-python
        ```


5. Просмотр полученных сообщений

    * Просмотреть запущенные контейнеры 
        ```
        sudo docker ps
        ```
    * Посмотреть логи запущеного контейнера

        >sudo docker logs [OPTIONS] CONTAINER - показать лог контейнера
        >
        >CONTAINER - id или имя запущенного контейнера
        >
        >OPTIONS - -f, --follow - опция непрерывного отслеживания вывода лога 
        >
        >(Ctrl + C - выход из режима)
        
        Для нашего примера строка будет выглядить так:
        
        >sudo docker logs --follow 29a6012fb262

---

## Cоздание сервера с использованием docker-compose файла {#docker-compose}


1.  Создание виртуальной машины

    >Все сервиры -> инфраструктура и сеть -> Compute Cloud


2.  Настройка виртуальной машины

    >Укажите имя, описание, [зону доступности](https://cloud.yandex.ru/docs/overview/concepts/geo-scope).

    * В пункте **Выбор образа загрузочного диска** выберете раздел **Операционные системы** -> Ubuntu

        >В нашем примере мы будем запускать виртуальную машину с использованием OS Ubuntu

    * В пункте **Диски и файловые хранилища** укажите размер диска 10 Гб.

        >Далее происходит настройка мощности вашей виртуальной машины, значения выбираются в зависимости от ваших потребностей, но для примера работы сервера достаточно минимальных настроек.

        **Внимание!** Значение поля [__прерываемая__](https://cloud.yandex.ru/docs/compute/concepts/preemptible-vm) значит, что при перезапуске машины адрес сервера будет меняться.

    * Создате сервисный аккаунт
    >Для управления машиной из командной строки необходима роль [editor](https://cloud.yandex.ru/docs/iam/concepts/access-control/roles).

    * Укажите логин для пользователя виртуальной машины.

    * Откройте фаил yc_rsa.pub и скопируте содержимое в поле SSH ключ.

3. Доступ к виртуальной машине

    * Для получения доступа к виртуальной машине необходимо ввести команду в терминале компьютера
        
        >ssh [-i identity_file] [user@]host[:port]
        >
        >identity_file - путь до приватной части SSH ключа
        >
        >user - имя пользователя (логин - указывали в настройках)
        >
        >host - внешний адрес хоста находится в свойствах вашей виртуальной машины
        
        Для нашего примера команда будет иметь следующий вид:
        >ssh -i /Users/GreenAPI/ssh/yc_rsa green-api@84.252.137.226

    * После ввода команды может выйти сообщение "Подлинность хоста не может быть установлена, продолжаем" (yes), введите пароль (фраза, которую использовали при создании [SSH ключа](#keySSH)) командная строка изменится green-api@webhook-server:~$ (вы вошли на виртуальную машину).


4. Запуск контейнера

    При использовании данного метода виртуальная машина не скачает и не установит [docker](https://docs.docker.com/engine/install/ubuntu/), все необходимо сделать вручную.

    >Для просмотра вебхуков вам необходимо настроить ваш инстанас в консоле [кабинета Green-Api](https://console.green-api.com/instanceList/)  на работу с сервером, указать внешний ip адрес машины и порт.

    >Адрес отправки уведомлений (URL) | http://158.160.6.161:8080 (пример)

    * Введите следующие команды в терминале виртуальной машины:
        ```
        sudo apt-get update
        ```
        ```
        sudo apt-get install \
            ca-certificates \
            curl \
            gnupg \
            lsb-release
        ```
        ```
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
        ```
        ```
        echo \
        "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
        $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
        ```
        ```
        sudo apt-get update
        ```
        ```
        sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin 
        ```
        ```
        sudo apt install docker-compose
        ```
        Получение docker-compose файла
        ```
        wget https://raw.githubusercontent.com/green-api/whatsapp-api-webhook-server-python/master/docker-compose.yml
        ```
        ```
        sudo docker-compose build
        ```

    * Запуск контейнера в фоне:
        ```
        sudo docker-compose up -d --force-recreate
        ```


5. Просмотр полученных сообщений

    * Просмотреть запущенные контейнеры 
        ```
        sudo docker ps
        ```
    * Посмотреть логи запущеного контейнера

        >sudo docker logs [OPTIONS] CONTAINER - показать лог контейнера
        >
        >CONTAINER - id или имя запущенного контейнера
        >
        >OPTIONS - -f, --follow - опция непрерывного отслеживания вывода лога 
        >
        >(Ctrl + C - выход из режима)
        
        Для нашего примера строка будет выглядить так:
        
        >sudo docker logs --follow 29a6012fb262
