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

"\<Path-to-python\>" - path to the Python interpreter executable file

"\<Path-to-server-file\>" - path to the server executable file (for instance, echo.py from the library example)

"\<Path-to-log-file\>" - path to the log file

Besides you will have to open the relevant port to the external network by configuring the firewall settings (Advanced settings -> Inbound Rules -> Create a rule -> Rule type = Port, Protocoles and port -> TCP, specify port, Действие -> Разрешить соединение)
