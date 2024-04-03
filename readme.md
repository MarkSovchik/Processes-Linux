## [Процессы](https://docs.google.com/spreadsheets/d/18dh1dN-GPoJO7KMpERx2Ks3jPa31uuaJY64HMFI8kYY/edit?usp=sharing)

**1. Для чего предназначена команда at? Как её использовать?**

Команда at позволяет передавать задания демону cron для одноразового выполнения в назначенное время. Выдавая задание, команда at сохраняет в отдельном файле как его текст, так и все текущие переменные среды, чего не делает команда crontab. По умолчанию все результаты выполнения задания направляются пользователю в виде электронного сообщения.

Базовый формат команды at:
at [-f файл] [-l –d -m] время
- f файл – список заданий должен быть взят из указанного файла;
- l – вывод на экран списка заданий; аналог команды atq;
- d – удаление задания с указанным номером; аналог команды atrm (в некоторых системах заменяется опцией -r);
- m – выдача пользователю сообщения по электронной почте о завершении задания;

**2. Для чего предназначена команда batch? Как её использовать? Чем отличаются команды at и batch?**

В отличие от at, batch позволяет операционной системе самой решить, когда наступает подходящий момент для запуска задачи в то время, когда система наименее загружена.

Формат команды batch представляет собой список команд для выполнения, следующих в строках за командой. Заканчивается список нажатием комбинации клавиш Ctrl+D. Можно поместить список команд в файл и перенаправить его на стандартный ввод команды batch
Следующую команду можно вводить с терминала:

$ batch <br>
sort <file'> outfile <br>
<EOT'>

**3. Для чего предназначен демон cron?**

Команда cron (/usr/sbin/cron) запускает процесс, выполняющий команды в указанные дни и время.

**4. Как использовать команду crontab?**

crontab - поддержка файлов crontab для отдельных пользова-
телей. Используется для добавления, удаления или выведе-
ния списка таблиц, используемых для управления демоном cron.

crontab [-u пользователь ] [-l | -r | -e ]
Доступны следующие опции:

-u пользователь - указывает пользователя, чей crontab должен быть отредактирован. Если эта опция не указана, использует crontab пользователя, выполняющего команду. Обратите внимание, что su может запутать и при работе через su всегда следует использовать опцию -u для безопасности.

- l – отображает текущий файл crontab;
- r – удаляет текущий файл crontab;
- e – изменяет файл crontab редактором, указанным в переменной окружения EDITOR.

**5. Что такое сигналы?**

Сигналы – это короткие стандартные сообщения, которыми могут обмениваться процессы с помощью системы. Сообщение-сигнал не содержит никакой информации, кроме номера сигнала (для удобства вместо номера можно использовать предопределенное системой имя). Если процессу необходимо реагировать на сигнал особенным образом, он может зарегистрировать обработчик, а если обработчика нет, за него отреагирует система. Как правило, это приводит к немедленному завершению процесса, получившего сигнал. Обработчик сигнала запускается асинхронно, немедленно после получения сигнала, что бы процесс в это время не делал. Вызов подпрограммы обработки называется перехватом сигнала.

**6. Как с помощью команды kill посылать сигналы процессам?**

kill - завершить процессы или послать им сигнал. Утилита

kill посылает сигнал процессу или процессам, заданным операндами pid. Процесс, которому посылается сигнал, должен принадлежать текущему пользователю, но суперпользователь (root) может посылать сигналы любым процессам.

/usr/bin/kill -s сигнал pid... <br>
[Разрыв обтекания текста] /usr/bin/kill -l [ статус_выхода ] <br>
[Разрыв обтекания текста] /usr/bin/kill [ -сигнал ] pid ... <br>
Утилита kill посылает сигнал процессу или процессам, заданным операндами pid.

**7. Для чего предназначены команды nice и renice?**

nice - запускает программу с заданием приоритета.

Приоритет процесса определяется так называемым «значением nice», которое лежит в пределах от +20 (наименьший приоритет, процесс выполняется только тогда, когда ничто другое не занимает процессор), до -20 (наивысший приоритет).

Команда, renice, служит для изменения значения nice для уже выполняющихся процессов.

**8. Как использовать команду ps?**

Cуществует три равноправных формата задания этой команды:

ps [-опции] <br>
ps [опции] <br>
ps [-- длинное_имя_опции [-- длинное_имя_опции] ...]

**9. Для чего предназначена команда top и как ее использовать?**

top отображает состояние процессов и их активность в реальном времени.

В верхней части вывода отображается астрономическое время, время, прошедшее с момента запуска системы, число пользователей в системе, число запущенных процессов и число процессов, находящихся в разных состояниях, данные об использовании ЦПУ, памяти и свопа. <br>
Далее отображается таблица, описывающая отдельные процессы.

Графы таблицы аналогичны поля вывода команды ps.
Содержимое окна обновляется каждые 5 секунд. Список процессов может быть отсортирован по используемому времени ЦПУ (по умолчанию), по использованию памяти, по PID, по времени исполнения. Переключать режимы отобра-
жения можно с помощью команд, которые программа top воспринимает. Это следующие команды:
- <Shift'>+<N'> – сортировка по PID;
- <Shift'>+<A'> – сортировать процессы по возрасту;
- <Shift'>+<P'> – сортировать процессы по использованию
ЦПУ;
- <Shift'>+<M'> – сортировать процессы по использованию
памяти;
- <Shift'>+<T'> – сортировка по времени выполнения.

**10. Как использовать команду w?**

w - выводит информацию о работающих в данный момент на машине пользователях и об их процессах. <br>
w - [husfV] [user]

Заголовок показывает в следующем порядке: текущее время, сколько времени работает система, сколько пользователей в данный момент работают и среднее время загрузки системы за последние 1, 5 и 15 минут.