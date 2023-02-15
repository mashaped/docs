# How to send file by sendFileByUrl method using external storage?

Для отправки файла по ссылке, можно воспользоваться следующими сервисами для хранения отправляемых файлов:

- [Yandex disk](#001)

- [Google drive](#002)

## Отправка файл по ссылке методом sendFileByUrl с Яндекс Диск {#001}

1. Открыть Яндекс Диск и найти требуемый к отправке файл, убедиться, что выставлены права на чтения или просмотр всем, у кого есть ссылка.

2. Выделить файл для отправки, правой кнопкой мыши “Share” -> “Copy link”

    <center>![`link Yandex disk`](../assets/faq_sendFileByUrl_en.jpg)</center>

    > Cкопированная ссылка: `https://disk.yandex.ru/i/af_Sg4D76royEQ`

3. Для скачивания файла будет использоваться сторонний сервис, используем специальную ссылку:

    ```
    https://getfile.dokpub.com/yandex/get/
    ```

4. Что бы сформитровать итоговую ссылку, неоходимо соединить ссылки из п.2 и п.3 в одну строку. Итоговая ссылка примет следующий вид:

    ```
    https://getfile.dokpub.com/yandex/get/https://disk.yandex.ru/i/af_Sg4D76royEQ
    ```

5. Отправить итоговую ссылку методом sendFileByUrl.

Данный способ взят с [сайта](https://getfile.dokpub.com)


## Отправить файл по ссылке методом sendFileByUrl с Google drive {#002}

1. Открыть Google drive и найти требуемый к отправке файл.

2. Выделить файл для отправки, правой кнопкой мыши “Share” -> “Anyone with the link” -> “Viewer” ->“Copy link” -> “Done”

    <center>![`link google drive`](../assets/faq_sendFileByUrl_googleDrive_en.jpg)</center>

3. Вставьте полученную ссылку в текстовый редактор для получения id файла

    Например, скопированная ссылка:

    `https://drive.google.com/file/d/13sseEurJDYZxb-ueH2VOpVoYY4U5Kvu1/view?usp=share_link`

    Из данной ссылки выбрать и скопировать значение между d/ и /view, в данном случае ID файла будет: 13sseEurJDYZxb-ueH2VOpVoYY4U5Kvu1

4. Используйте специальную ссылку для скачивания файлов по id:

    ```
    https://drive.google.com/uc?export=download&id=
    ```

5. Поместить скопированное значение id файла из п.3. в конец ссылки. Итоговая ссылка должна принять следующий вид:

    ```
    https://drive.google.com/uc?export=download&id=13sseEurJDYZxb-ueH2VOpVoYY4U5Kvu1
    ```

6. Отправить итоговую ссылку методом sendFileByUrl.