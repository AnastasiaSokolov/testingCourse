# Установка JMeter 
- [Учебник JMeter](https://coderlessons.com/tutorials/kachestvo-programmnogo-obespecheniia/uchebnik-jmeter/2-zagruzka-i-ustanovka#:~:text=%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0%20JMeter%20%D1%87%D1%80%D0%B5%D0%B7%D0%B2%D1%8B%D1%87%D0%B0%D0%B9%D0%BD%D0%BE%20%D0%BF%D1%80%D0%BE%D1%81%D1%82%D0%B0%20%D0%B8,%D0%9F%D1%80%D0%BE%D1%81%D1%82%D0%BE%20%D1%80%D0%B0%D1%81%D0%BF%D0%B0%D0%BA%D1%83%D0%B9%D1%82%D0%B5%20%D0%B8%20%D0%B2%D1%81%D0%B5%20%D0%B3%D0%BE%D1%82%D0%BE%D0%B2%D0%BE!)
- [Как создать нагрузочный тест с помощью Apache Jmeter](https://habr.com/ru/post/165159/)

### Windows
1. Проверить, установлен ли пакет java на компьютере <code>пуск > параметры > приложение</code>. Если не установлен, то перейти на сайт [Java](https://www.oracle.com/java/technologies/downloads/#java8-windows) и установить пакет.
2. Перейти на сайт [JMeter](https://jmeter.apache.org/download_jmeter.cgi) и скачать архив *apache.jmeter-0.0..zip*(для windows)
3. Разархивировать файл zip в каталог где будет лежать JMeter. Готово! JMeter установлен!
   
#### Описание каталогов
- **/bin** - содержит файл сценария JMeter для запуска JMeter
- **/docs** - файлы документации JMeter
- **/extras** - дополнительные файлы, связанные с ant
- **/lib/** - содержит необходимую библиотеку Java для JMeter
- **/lib/ext** - содержит основные файлы jar для JMeter и протоколы
- **/lib/junit** - библиотека Junit, используемая для JMeter
- **/printable_docs** - JMeter Руководство пользователя
  
#### Запуск JMeter
3 режима запуска JMeter:
1. **GUI Mode** (в режиме графического интерфейса)   
    *bin/ApacheJMeter.jar*
    *bin/JMeter.bat*
2. **Режим сервера** (в режиме без графического интерфейса)  
    Режим сервера используется для распределенного тестирования.  
    *Открыть Командную строку > Перенести файл bin/jmeter-server.bat*
4. **Режим командной строки**  
    JMeter в режиме графического интерфейса потребляет много компьютерной памяти. Для сохранения ресурса JMeter можно запустить без графического интерфейса.  
    *В командной строке ввести <code>$jmeter -n -t testPlan.jmx - l log.jtl -H 127.0.0.1 -P 8000</code>*
    
### Linux
- Установка JMeter на Linux аналогично как и на Windows
- Запуск JMeter:
   - сценария jmeter — запустить файл JMeter (в режиме GUI по умолчанию)
   - скрипта jmeter-server — запустить файл JMeter в режиме сервера (вызывает скрипт JMeter с соответствующими параметрами)
   - jmeter.sh — очень простой скрипт JMeter без опций JVM.
   - mirror-server.sh — запуск зеркальный сервер JMeter в режиме без графического интерфейса
   - shutdown.sh — запуск клиента Shutdown, чтобы корректно остановить экземпляр без графического интерфейса
   - stoptest.sh — запуск клиента выключения, чтобы внезапно остановить экземпляр без графического интерфейса

### Установка JMeter Plugins Manager
JMeter Plugins Manager - помогает устанавливать плагины вручную.  

1. Скачать файл [plugins-manager.jar](https://jmeter-plugins.org/install/Install/)
2. Поместить файл *..\lib\ext\plugins-manager.jar*

### Дополнительные плагины
Открыть JMeter Plugins Manager *options > Plugins Manager*  
Установить следующие плагины [подробнее](https://www.blazemeter.com/blog/top-ten-jmeter-plugins):
- Custom Thread Groups
- Flexible File Writer
- PerfMon Servers Performance Monitoring
-  Custom JMeter Functions
- 3 Basic Graphs
- JSON Plugins
- Throughput Shaping Timer
- Dummy Sampler
- Distribution/Percentile Graphs 
- BlazeMeter step-by-step Debugger
- KPI vs KPI graphs
- 5 Additional Graphs 

# Работа в JMeter

#### JMeter элементы [подробнее](https://coderlessons.com/tutorials/kachestvo-programmnogo-obespecheniia/uchebnik-jmeter/3-ssylka-na-elementy)
- **Thead Group** (Группа потоков) - это коллекция потоков. Каждый поток представляет одного пользователя, использующего тестируемое приложение. По сути, каждый поток имитирует один запрос реального пользователя к серверу.  
Элементы управления для группы потоков позволяют вам установить количество потоков для каждой группы.  
Например, если вы установите количество потоков равным 100; JMeter создаст и смоделирует 100 запросов пользователей к тестируемому серверу.
- **Samples** (Пробоотборники) - пользовательский запрос может быть FTP-запросом, HTTP-запросом, JDBC-запросом и т.д.
   - HTTP-запрос - этот сэмплер позволяет отправлять HTTP / HTTPS-запрос на веб-сервер.
- **Listener** (Слушатели) - показывает результаты выполнения тестов.
   - Слушатели результатов графика отображают время ответа сервера на графике
   - View Result Tree показывает результаты запроса пользователя в базовом формате
   - Таблица Result показать сводку результатов теста в формате таблицы
   - Журнал показывает сводку результатов теста в текстовом файле
- **Config Element** (Элементы конфигурации) - установить значения по умолчанию и переменные для последующего использования сэмплерами.
   - HTTP-запрос по умолчанию - этот элемент позволяет  установить значения по умолчанию, которые используют контроллеры HTTP-запросов.
   - Login Config Element (Элемент конфигурации входа) - используется для имитации входа одного пользователя.Подходит только для параметров входа в систему (имя пользователя и пароль)
   - CSV Data Config - Используется для имитации входа нескольких пользователей. Подходит для большого количества параметров.

#### JMeter GUI [подробнее](https://coderlessons.com/tutorials/kachestvo-programmnogo-obespecheniia/uchebnik-jmeter/4-jmeter-gui)
- **Test plan** - место где добавляются элементы, необходимые для теста JMeter.
- **WorkBench** - место для временного хранения тестовых элементов.  
  
**Добавление элемента**
1. Кликнуть правой кнопкой мыши по *пдану тестирования*
2. Выбрать новый элемент из списка **add**
  
**Создание файла JMX**
1. Правой кнопкой мыши по элементу > Выбрать Save Selecrtion As... (сохранить выделенное как)
Элементы тестирования JMeter и план тестирования хранятся в формате * .JMX . JMX расшифровывается как Java Management Extensions.
  
**Запуск файла JMX**
1. Правой кнопкой мыщи по элементу > выбрать Merge
2. Выберите файл Elements ( name.jmx. ) в каталоге. Этот элемент будет добавлен в текущий план тестирования.
  
**Настройка элементов**
1. Выбрать элемент в дерефе на левой панели
2. Ввести параметры конфигурации на правой панели
  
**Сохранение плана тестирования**  
Перед запуском необходимо сохранить план тестирования.  
*Файл > Сохранить план тестирования как > диалоговое окно > Ввести имя файла плана тестирования > нажать Сохранить*
- Сохранение плана тестирования - план тестирования состоит из одного или нескольких элементов.
- Сохранение элемента - элемент является основным компонентом JMeter и сохраняется только один элемент.
  
**Создание комбинированного плана тестирования**
Можно объединить один или нескольуо планов тестирования, чтобы создать комбинированный план тестирования.  
*Правой кнопкой мыщи по элементу > выбрать Merge > Выбрать файл > Open*
  
**Запуск план тестирования**
Чтобы запустить один или несколько планов тестирования, выберать « Пуск» (Ctrl + R) в пункте меню « Выполнить».  
Когда JMeter работает, в правом конце строки меню отображается маленький зеленый прямоугольник.  
![image](https://user-images.githubusercontent.com/34191733/160431235-e7a96a5e-3829-42c8-8c28-dc23c1b05a2d.png)  
Цифры слева от зеленого поля — количество активных потоков / общее количество потоков.  
Чтобы остановить тест, нажать кнопку Стоп или используйте короткую клавишу Ctrl + ‘.’

#### Тестирование производительности
1. Перед тестированием производительности целевого веб-приложения необходимо определить какая цель тестирования
   - Нормальная нагрузка - среднее количество пользователей, посещающих сайт
   - Heavy Load - максимальное количество пользователей, посещающих сайт
2. Добавить группу тем *Add > Threads (Users) > Thread Group*  
   Свойства потока:
   - Number of Threads (users) Количество потоков - количество пользователей, подключающихся к целевому сайту.
   - Ramp-Up Period (in seconds) Период разгона - количество времени для выполнения тестирования. (как долго откладывать перед запуском следующего пользователя.)
   - Loop Coount Количество циклов
3. Добавление элементов
   - HTTP-запрос по умолчанию *Add > Config Element > HTTP Request Defaults*  
      В панели управления элемента добавить имя веб-сайта.
   - HTTP-запрос *Add > Sampler > HTTP Request*   
      В панели управления элемента добавить path
4. Добавление элемента с  результатами теста
   - *Add > Listener > Graph Results*
   - *Add > Listener > View Results Tree*
   - *Add > Listener > Summary Report*
5. Выполнить тест и получить результаты
**Graph Results**  
Результаты теста на графике в режиме реального времени.  
Внизу рисунка есть следующая статистика, представленная в цветах:
- Черный - общее количество отправленных текущих образцов
- Синий - текущее среднее всех отправленных образцов.
- Красный - текущее стандартное отклонение.
- Зеленый - пропускная способность, которая представляет количество запросов в минуту, обработанных сервером  
**Пропускная способность** является наиболее важным параметром. Он представляет способность сервера справляться с большой нагрузкой. Чем выше пропускная способность, тем выше производительность сервера.
**Отклонение** отображается красным цветом - чем меньше отклонение, тем лучше.

#### Timer [подробнее](https://coderlessons.com/tutorials/kachestvo-programmnogo-obespecheniia/uchebnik-jmeter/6-taimery#1)
По умолчанию JMeter отправляет запрос без пауз между запросами. В этом случае JMeter может перегружать тестовый сервер, делая слишком много запросов за короткое время.   
Таймеры позволяют JMeter задерживать между каждым запросом, который делает поток. Таймер может решить проблему перегрузки сервера .
- Constant Timer - постоянный таймер задерживает каждый пользовательский запрос на одинаковое количество времени.  
- Gaussian Random Time - задерживает каждый пользовательский запрос на случайное количество времени.
- Uniform Random Timer - задерживает каждый пользовательский запрос на случайное количество времени.
- BeanShell Timer - может быть использован для генерации времени задержки между каждым запросом пользователя.
- JSR223 Timer - можно использовать для генерации задержки между каждым запросом пользователя с использованием языка сценариев JSR223.
   
**Пример, Constant Timer**
 1. Добавить Thread Group
 2. Добавить элементы Jmeter
   - Добавить HTTP-запрос по умолчанию]
   - Добавить HTTP-запрос
 3. Добавить Constant Timer
   - Настройка задержки потока в миллисекундах Thread Delay (in milliseconds)
 4. Добавить результаты просмотра в таблицу *Add > Listener > View Result in Table*
 5. Запустить тест
 6. Проанализировать результаты теста 
 
#### Assertion [подробнее](https://coderlessons.com/tutorials/kachestvo-programmnogo-obespecheniia/uchebnik-jmeter/7-utverzhdeniia)
- Response Assertion - позволяет добавлять строки шаблона для сравнения с различными полями ответа сервера.
- Duration Assertion - проверяет, что каждый ответ сервера был получен в течение определенного периода времени. Любой ответ, который занимает больше времени, чем указанное количество миллисекунд (указанное пользователем), помечается как отказавший ответ.
- Size Assertion - проверка размера проверяет, что каждый ответ сервера содержит ожидаемое количество байтов. Можно указать, что размер будет равен, больше, меньше или не равен заданному количеству байтов.HTML Assertion - 
- XML Assertion - проверка, что данные ответа состоит из формально правильного документа XML.
- HTML Assertion - позволяет пользователю проверять синтаксис HTML данных ответа. Это означает, что данные ответа должны соответствовать синтаксису HTML.
  
 **Пример, Response Assertion - status code**
 1. Добавить Thread Group
 2. Добавить элементы Jmeter
   - Добавить HTTP-запрос по умолчанию]
   - Добавить HTTP-запрос
 3. Добавить Response Assertion
   ![image](https://user-images.githubusercontent.com/34191733/160453185-d99779c3-8caa-4dcc-a678-9c109c1bfbcf.png)
4. Добавить результаты утверждения *Add > Listener > Assertion Results*
5. Запустить тест
6. Результат теста отобразится на панели результатов утверждения. 

#### Logic Controller [подробнее](https://coderlessons.com/tutorials/kachestvo-programmnogo-obespecheniia/uchebnik-jmeter/8-kontrollery)
Логические контроллеры позволяют определять порядок обработки запроса в потоке. Это позволяет вам контролировать «когда» отправить запрос пользователя на веб-сервер.  
Логические контроллеры определяют  порядок  выполнения запроса пользователя. 
- Recording Controller - JMeter может записывать шаги тестирования, контроллер записи является заполнителем для хранения этих шагов записи.
- Simple Controller -  это просто контейнер для запроса пользователя.
- Loop Controller - заставляет пользовательский запрос выполняться указанное количество раз или выполняться вечно.
- Random Controller - заставляет все пользовательские запросы выполняться в случайном порядке в каждом периоде цикла.
- Module Controller - общая идея заключается в том, что веб-приложения состоят из небольших функциональных блоков (т. Е. Входа в систему, создания учетной записи, выхода из системы …). Эта функциональность может храниться в Simple Controller как «модули». Контроллер модуля выберет, какой модуль должен работать.
- Interleave Controller - запускает и запускает один из пользовательских запросов в каждом цикле потока.
- Runtime Controller - контролирует, как долго его дочерним элементам разрешено работать.
- Transaction Controller - измеряет общее время, необходимое для завершения выполнения теста
- Switch Controller - предназначен для использования внешнего плана тестирования. Этот контроллер позволяет использовать несколько планов тестирования в JMeter.
  
**Пример, Loop Controlleroller**
 1. Добавить Thread Group
   - Настроить  Loop Count группы потоков на 2
 3. Добавить элементы Jmeter
   - Добавить HTTP-запрос по умолчанию
   - Добавить Loop Controller
      - Добавить значение 50 в поле Loop Count. (JMeter отправит всего 2 * 50 = 100 HTTP-запросов.)
      - Кликнуть правой кнопкой мыши Loop Controller, *Add -> Sampler -> HTTP request*
4. Добавить результаты просмотра в таблицу *Add > Listener > View Result in Table*
5. Запустить тест
6. Проанализировать результаты теста 

#### Processor [подробнее](https://coderlessons.com/tutorials/kachestvo-programmnogo-obespecheniia/uchebnik-jmeter/9-protsessor)
Процессор используется для изменения сэмплеров в их области.
- Pre-процессор - выполняет некоторое действие  перед  выполнением запроса сэмплера.
- Post-процессор - выполняет некоторое действие после выполнения запроса сэмплера.

#### Распределенное тестирование [подробнее](https://coderlessons.com/tutorials/kachestvo-programmnogo-obespecheniia/uchebnik-jmeter/10-raspredelennoe-testirovanie)
Распределенное тестирование — это вид тестирования, в котором для проведения стресс-тестирования используются несколько систем . Распределенное тестирование применяется для тестирования веб-сайтов и серверных приложений, когда они работают с несколькими клиентами одновременно.
![image](https://user-images.githubusercontent.com/34191733/160461407-7f06fd09-b024-499d-bc8b-f81b8dc7a1a8.png)
- Master : система, работающая с JMeter GUI, управляющая каждым ведомым.
- Подчиненный : система, использующая JMeter-сервер, получает команду от мастера и отправляет запрос на тестируемый сервер.
- Цель : тестируемый веб-сервер, получить запрос от подчиненных.
