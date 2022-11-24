# Example of preparing a server environment on the Windows operating system

To use IIS (Internet Information Services) as a web server, you have to set up the web.config configuration file,
so that IIS can execute Python code correctly. This file is located in your web server publish folder.
The language interpreter can be downloaded from the [python.org](https://www.python.org/downloads/) official web site.

After installing the interpreter, you should specify the HttpPlatform handler in the web.config file. This handler will pass connections to the offline Python process.

Configuration file example:

```
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="<Path-to-python>\python.exe"
                  arguments="<Path-to-server-file>\echo.py
                  stdoutLogEnabled="true"
                  stdoutLogFile="<Path-to-log-file>\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SOME_VARIABLE" value="%SOME_VAR%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

"\<Path-to-python\>" - путь к исполняемому файлу интерпритатора Python

"\<Path-to-server-file\>" - путь к исполняемому файлу сервера (например echo.py из примера к библиотеке)

"\<Path-to-log-file\>" - путь к файл логов

Также потребуется открыть соответствующий порт во внешнюю сеть, установив настройка брандмауэра (Дополнительные параметры -> Правила для входящих подключений -> Создать правило -> Тип правила = Порт, Протоколы и порт -> TCP, указать порт, Действие -> Разрешить соединение)
