# WiFiLamp-RemoteControl
(EN) Firmware for WiFi Lamp by Alex Gyver and cross-platform lamp management software
(RU) Прошивка для WiFi Lamp от Алекса Гайвера и кроссплатформенное программное обеспечение для управления лампами
	
# Возможности программного обеспечения
1. Кросплатформенное управление настройкой лампы и режимами по WiFi. 
	* управлеие лампой когда она в режиме точки доступа только под Windows и Android (SDK 23 - 30 | Android 6 - Android 11).
2. Объединение в группу и управление группой ламп в один клик.
3. Удобный интерфейс приложения ориентирован как для простых пользователей так и разработчиков.

# Действия сенсорной кнопки для этой прошивки:
	• однократный клик – включение или выключение светильника;
	• двукратный клик – следующий эффект;
	• трёхкратный клик – предыдущий эффект;
	• четырёхкратный клик – запуск воспроизведения эффеков в цикле;
	• пятикратный клик – запуск эффекта огонь (интимная обстановка);
	• шестикратный клик – запуск таймера выключения лампы через 5 минут;
	• семикратный клик – смена рабочего режима лампы: с WiFi точки доступа на WiFi клиент или наоборот;
	• удержание – увеличение или уменьшение "яркости";
	• однократный клик и удержание – увеличение или уменьшение «скорости»;
	• двукратный клик и удержание –  увеличение или уменьшение «масштаба»;
	• удержание при выключенной лампе – включает эффект «Белый Свет»;
	
------------------------------------------------------------------------------------------	
* в файле button.ino есть закомментированы альтернативы поведения которые вы можете настроить по своему вкусу.

# Последние изменения :
# Версия 3.6 | 102 эффекта ===================
( • «Чacы» и «Бeгyщaя cтpoкa» не в счет )
1. Доработан эффект «Мечта ленивого дизайнера», оптимизирован код и улучшена анимация, изменены установки по умолчанию.
2. Исправлена ошибка задержки выключения лампы после срабатывания будильника.
3. В статистику добавлены geo данные и улучшено отображение результатов, также теперь можно увидеть поддерживаемые данной прошивкой лампы на Google картах c Полной информацией по конфигураци и используемом програмном обеспечении.
* требуется обновление приложений под Android и Windows.

------------------------------------------------------------------------------------------	
* Скетч использует 578576 байт (55%) памяти устройства. Всего доступно 1044464 байт.
Глобальные переменные используют 45612 байт (55%) динамической памяти, оставляя 36308 байт для локальных переменных. Максимум: 81920 байт.


------------------------------------------------------------------------------------------

# Инструкции по установке
• Схема подключения два варианта с ESP и Wemos с распиновкой чипов находится в директории Schemes

Распакуйте содержимое архива в корневую папку на диске (не на рабочий стол, пожалуйста) и делайте всё так же, как показал Алекс Гайвер в своём видео https://youtu.be/771-Okf0dYs?t=525. Отличие от видео - матрицу подключаем к D3 и кнопку питаем от 3,3 вольта. В архиве есть файл "ПРОЧТИ МЕНЯ!!.txt. Его нужно внимательно прочитать. Для загрузки файлов из папки data в файловую систему контролера нужно установить Uploader. Видео https://esp8266-arduinoide.ru/esp8266fs/ Версию платы в "Менеджере плат" выбирайте 2.7.4. При первом запуске лампа создаст свою WiFi сеть с именем LedLamp пароль у этой сети при первом запуске будет 31415926. После подключения к сети LedLamp наберите в браузере 192.168.4.1 и зайдите на web страницу лампы. Там можно изменить имя лампы (если их несколько в сети)Перезагрузить лампу. 
Чаще всего изменяемые константы перенесены в файл ConstantsUser.h как правило этого будет достаточно, если чегото не нашли смотрите смотрите Constants.h там находятся остальные параметры (там по-русски, без проблем разберётесь) и в файле data/config.json (там можно ничего не менять, всё меняется потом с web страницы лампы). Но если хотите, чтобы лампа сразу подключилась к Вашей WiFi сети, введите в файле data/cofig.json в поля "ssid": и "password": имя и пароль Вашей WiFi сети, соответственно. Поле "ESP_mode": измените с 0 на 1. Сохраните файл на то же место и сделайте upload файловой системы. Лампа сразу подключется к Вашей сети. Остальные настройки можно сделать из приложения под Windows, Android или прямо из любого браузера перейдя по ссылке http://winecard.ltd.ua/dev/LampRemote2/index.html?ip=192.168.1.1&dev=1&timeout=200.

Рекомендуем создать на уровне папки Firmware папку Custom она записана в Git ignore в которой будет еще директории по количеству ваших ламп к примеру EVA и Adam в которых будут хранится настройки для вашей конкретной лампы это файл ConstantsUser.h вы обновляете с гита прошивку закидываете туда свой файл ConstantsUser.h и можно шиться, при обновлении прошивок будете только менять настройки для нужной лампы

Поддерживает файловые системы SPIFFS и LittleFS	(по умолчанию SPIFFS)

Тем, у кого лампа уже собрана и нет возможности (или сложно) добраться до разъёма для перепрошивки, можно прошиться по ОТА. Для этого нужно использовать WEB_Updater. В папке есть файл Readme.txt. Внимательно его прочитайте

В данной прошивке режим работы ESP_MODE 1 (с роутером) или ESP_MODE 0 (без (точка доступа)) . В любой момент его можно будет поменять, либо он сам изменится.

Обсуждение исходного и этого проэктов тут: https://community.alexgyver.ru/threads/wifi-lampa-budilnik-obsuzhdenie-proshivki-ot-gunner47.2418/page-300#post-110429

# Добавлена программа управления под Windows Lamp Remote Control • II 
# папка RemoteControlForWindows установки не требует можно запускать прямо из этой папки 
# Файл .apk для установки приложения под Android папка RemoteControlForAndroid
# Сыылка для веб приложения под браузер «Application WiFi Lamp Remote Control version • II»
	http://winecard.ltd.ua/dev/LampRemote2/index.html?ip=192.168.1.1&dev=1&timeout=200
	
------------------------------------------------------------------------------------------

Change Log	

------------------------------------------------------------------------------------------

# ПРЕДЫДУЩИЕ ВЕРСИИ • 3.XX

Версия 3.5 | 102 эффекта ===================
( • «Чacы» и «Бeгyщaя cтpoкa» не в счет )
1. Добавлена поддержка статистики в приложения под Android и Windows.
2. Добавлен эффект «Цветные кудри», масштаб ступенчатый 2 положения, скорость регулируется программно.

------------------------------------------------------------------------------------------	
* Скетч использует 578040 байт (55%) памяти устройства. Всего доступно 1044464 байт.
Глобальные переменные используют 45484 байт (55%) динамической памяти, оставляя 36436 байт для локальных переменных. Максимум: 81920 байт.


Версия 3.45 | 101 эффектов ===================
( • «Чacы» и «Бeгyщaя cтpoкa» не в счет )
1. Добавлена поддержка статистики в прошивку лампы.

------------------------------------------------------------------------------------------	
* Скетч использует 577700 байт (55%) памяти устройства. Всего доступно 1044464 байт.
Глобальные переменные используют 45472 байт (55%) динамической памяти, оставляя 36448 байт для локальных переменных. Максимум: 81920 байт.


Версия 3.4 | 101 эффектов ===================
( • «Чacы» и «Бeгyщaя cтpoкa» не в счет )
1. Для пользователей IOS добавлен отступ в UI на новых версиях IOS из за конфликта с навигационной панелью.
	* обновление не требуется, так как код в облаке.
2. Добавлен эффект «Мечта ленивого дизайнера», скорость и масштаб ступенчатые по три положения.

------------------------------------------------------------------------------------------	
* Скетч использует 577680 байт (55%) памяти устройства. Всего доступно 1044464 байт.
Глобальные переменные используют 45472 байт (55%) динамической памяти, оставляя 36448 байт для локальных переменных. Максимум: 81920 байт.


Версия 3.3 | 100 эффектов ===================
( • «Чacы» и «Бeгyщaя cтpoкa» не в счет )
1. Исправлена ошибка в файловой системе LittleFS, bugfix от sergeym11.
2. Добавлен эффект «Планета Земля», это первый эффект подобного типа
	использует подгрузку бинарного файла изображения из файловой системы
	скорость постоянная, масштаб ступенчатый два вида земного шара.
* необходимо загрузить папку «bin» с содержимым в файловую систему лампы
  файловую систему после прошивки обновлять не обязательно, нужно только загрузить директорию «bin» с файлами и заменить файл effects4.json
3. Исправлены мелкие ошибки в приложениях и web интерфейсе.

[!] по умолчанию отключен эффект «Часы» кому нужно, можно включить в файле UserConstants.h
	раскоментируйте USE_TIME_EFFECT и в файл effects4.json добавьте строчку
	{"n":"Чacы","v":[1,245,1,100,1]},) перед эффектом «Бeгyщaя cтpoкa»

------------------------------------------------------------------------------------------	
* Скетч использует 576300 байт (55%) памяти устройства. Всего доступно 1044464 байт.
Глобальные переменные используют 45432 байт (55%) динамической памяти, оставляя 36488 байт для локальных переменных. Максимум: 81920 байт.

Версия 3.2 | 101 эффектов ===================
1. Добавлен новый эффект «Фейерверк» (регулировки ступенчатые)
	• скорость: 3 (показывать закат (условно – вечерело), подсвечивать небо, без подсветки) 
	• масштаб:  4 условных феерверка ( вся гамма, Сакура, День Незалежності, Фризантемы).
	• по умолчанию смена феерверка происходит автоматически
* этот эффект использует новую фичу SOFT_DELAY – програмное управления FPS.
------------------------------------------------------------------------------------------	
* Скетч использует 576040 байт (55%) памяти устройства. Всего доступно 1044464 байт.
Глобальные переменные используют 42804 байт (52%) динамической памяти, оставляя 39116 байт для локальных переменных. Максимум: 81920 байт.

 Версия 3.1 | 100 эффектов ===================
1. Добавлена фича: показ IP лампы при удачном подключении к роутеру (холодный старт или рестарт | отключается коментированием SHOW_IP_TO_START).
2. Оптимизирован код управления эффектами.
3. Добавлена возможность по желанию использовать эффект «Часы» | отключается коментированием USE_TIME_EFFECT
	* не забудьте убрать из effects4.json строчку {"n":"Чacы","v":[1,245,1,100,1]},
4. Исправлена ошибка с бегунком скорости на «Бегущей строке» (скорость регулировалась наоборот).
5. Исправлена ошибка с установкой любимого эффекта в настройках лампы.
	* требуется обновление приложений под Android и Windows (новые версии в архиве).
6. Доработан код управления эффектами, можно располагать эффекты в любом порядке в списке за исключением 6 последних.
7. Добавлена новая фича: возможность програмного управления FPS для эффектов.
------------------------------------------------------------------------------------------	
* Скетч использует 574404 байт (54%) памяти устройства. Всего доступно 1044464 байт.
Глобальные переменные используют 42800 байт (52%) динамической памяти, оставляя 39120 байт для локальных переменных. Максимум: 81920 байт.


Версия 3.05 | 100 эффектов ===================

1. Исправлена ошибка с инициализацией будильника.
	* если даже существует корректный alarm_config.json всеравно нужно зайти в настройки лампы и и нажать кнопку Сохранить настройки, чтобы данные будильника прописались в Eeprom.
------------------------------------------------------------------------------------------	
* Скетч использует 574164 байт (54%) памяти устройства. Всего доступно 1044464 байт.
Глобальные переменные используют 42792 байт (52%) динамической памяти, оставляя 39128 байт для локальных переменных. Максимум: 81920 байт.

Версия 3.0 | 100 эффектов ===================

------------------------------------------------------------------------------------------
	* поскольку исходники писались разными людьми код был приведен к одному стилю,
	(на сколько хватило терпения) 
	изменений очень много, поэтому сменил резко номер версии и создал новый репозиторий.

1. Изменен принцип вызова эффектов и упрощен код.
2. Упорядочено назначение файлов в прошивке, Gif Data вынесена в отдельный файл, исправлены мелкие ошибки и наверное добавлены новые.
3. Почищен код и приведен к одному стилю.
4. Список эффектов для сторонних приложений убран из прошивки и подгружается прямо из файловой системы, что позволило освободить память и уменьшить размер скетча. 
5. Исправлена ошибка загрузки списка эффектов когда лампа находится в режиме точки доступа 
	* требуется обновление программ под Windows и Android.
6. Упрощена web страница настроек лампы (остались только настройки подключения, чтобы не дублировать код) все остальное можно настроить непосредственно с прилагаемых приложений.
7. Исправлена ошибка с интервалом смены эффектов в режиме цикл.
8. Добавлен новый эффект (три в одном) «Строб, Хаос, Дифузия» (регулировки ступенчатые скорость: 3, масштаб: 4).
9. Обновлена документация.

------------------------------------------------------------------------------------------	
* Скетч использует 573664 байт (54%) памяти устройства. Всего доступно 1044464 байт.
Глобальные переменные используют 42780 байт (52%) динамической памяти, оставляя 39140 байт для локальных переменных. Максимум: 81920 байт.

------------------------------------------------------------------------------------------

# ПРЕДЫДУЩИЕ ВЕРСИИ • 2.XX


Версия 2.3 | 99 эффектов ===================

1. Исправлена ошибка в эффекте «Плазменная лампа».
2. Добавлена анимация показывающая состояние лампы ESP Mode
	а) зеленая – подключение к роутеру
	б) синяя – лампа в режиме точки доступа
	в) красный глаз терминатора – не получено время, синий – отключено обращение к ntp
3. Добавлено три новых эффекта
	«Цветок Лотоса»   (цвет выбирается масштабом | < 10% автосмена цвета)  
	«Новогодняя Елка» (три в одном выбирается масштабом)   
	«Побочный Эффект» (два в одном выбирается масштабом) 
------------------------------------------------------------------------------------------	
* Скетч использует 593144 байт (56%) памяти устройства. Всего доступно 1044464 байт.
Глобальные переменные используют 46768 байт (57%) динамической памяти, оставляя 35152 байт для локальных переменных. Максимум: 81920 байт.

------------------------------------------------------------------------------------------

Версия 2.2 | 96 эффектов

1. Исправлена ошибка в эффекте «Свеча».
2. Добавлен новый эффект «Spectrum»
	8 фиксированных установок (масштаб) четные с размытием
	(вспышка при изменении масштаба: зеленая – с размытием, оранжевая – без)
	0, 1: медленное изменение цвета
	2, 3: быстрое изменение цвета
	4, 5: скачкообразное изменение цвета
	6, 7: изменение диапазона спектра.
3. Добавлена новая фича: «Тест матрицы»
	а) индикация первого и последнего светодиода (соответственно красный / зеленый)
	для проверки правильности подключения, а центр желтая точка
	б) последовательная смена основных цветов RED, GREEN, BLUE
	в) плавный градиент на весь спектр
	тест вызывается из приложений на вкладке информации о лампе нажатием на item MATRIX.
------------------------------------------------------------------------------------------	
* Скетч использует 584108 байт (55%) памяти устройства. Всего доступно 1044464 байт.
Глобальные переменные используют 45872 байт (55%) динамической памяти, оставляя 36048 байт для локальных переменных. Максимум: 81920 байт.


приложения WiFi Lamp Remote Control version • II 
1. Добавлено управление тестом матрицы.
2. Поправлен баг с выключением питания лампы после выхода из цикла.	
3. Добавлены кнопки управления тонкой настройкой скорости и масштаба
   приложение под Android SDK 23 - 30 | Android 6 - Android 11
   компилировалось под SDK 31 (были жалобы что не устанавливается приложение на Android 11)
   в эмуляторе работает под Android 11, на живом девайсе Android 10.
   

	
Версия 2.1 | 95 эффектов

1. Дописаны новые фукции для заливки градиентом gradientHorizontal | gradientVertical 
они менее производительны но работают на всех видах ламп.
2. У эффектов «Свеча» и «Реки Ботсваны» теперь есть возможность использования альтернативных градиентов параметр ALT_GRADIENT = true, находится в файле new_effect.ino 
(на лампах на базе ленты с вертикальной ориентацией ALT_GRADIENT = true в противном случае градиенты будут неправильно отображаться), для остальных лаип не так важно, выбирайте на свое усмотрение, по умолчанию ALT_GRADIENT = false (градиент более плавный и производительный),
3. Добавлена новая фича: индикация уровней яркости, скорости, масштаба при регулировке кнопкой на лампе, активируется раскоментированием #define PROPERTIES_LEVEL_INDICATOR в файле ConstantsUser.h
по умолчанию активна.
4. Поправлены мелкие баги. (в часности нужно перезалить файл data/effects4.json)


Версия 2.0 | 95 эффектов

1. Изменен формат JSON файлов эффектов (уменьшен их размер, что позволило более надежно загружать список эфектов
плюс сделан задел на будущее для добавления в прошивку большего количества эффектов 
с текущим алгоритмом с матрицей 16x16 прошивка работала с 105 эффектами)
для программы от Котейка требуется доработка с его стороны.
2. Добавлена функция выключения лампы с задержкой 5 мин (6 нажатий, независимо от того включена или выключена лампа)
3. Добавлена поддержка групового управления лампами (может корректно работать с разным количеством эффектов)
	управление осуществляется как из приложения так и непосредственно на самих лампах
	работает в дуплексном режиме (тоесть можно управлять с любой лампы, Master & Slave меняется автоматически)
	заложена поддержка до 8 ламп, проверял на трех,
	список ламп в групе сохраняется в файловой системе,
	поддерживаемые синхронные режимы (Power, следующий эффект, предыдуущий эффект, яркость, скорость, масштаб, дефолтные значения, эффекты в цикле  )
4. Для совместимости прошивки с приложением от Котейки добавлен свой режим управления циклом 
	(показать все по порядку, или случайный эффект)
5. Добавлен эффект «Песочные Часы»
6. Действия сенсорной кнопки для этой прошивки:
1)	однократный клик – включение или выключение светильника;
2)	двукратный клик – следующий эффект;
3)	трёхкратный клик – предыдущий эффект;
4)	четырёхкратный клик – запуск воспроизведения эффеков в цикле;
5)	пятикратный клик – запуск эффекта огонь (интимная обстановка);
6)	шестикратный клик – запуск таймера выключения лампы через 5 минут;
7)	семикратный клик – смена рабочего режима лампы: с WiFi точки доступа на WiFi клиент или наоборот;
8)	удержание – увеличение или уменьшение "яркости";
9)	однократный клик и удержание – увеличение или уменьшение "скорости".
10)	двукратный клик и удержание –  увеличение или уменьшение "масштаба".
в файле button.ino есть закомментированы альтернативы поведения которые вы можете настроить по своему вкусу.

!!! для поддержки всего функционала нужно использовать и приложения версии 2.XX


Приложения (относится к приложениям под Android, Windows и Browzer IOS)
WiFi Lamp Remote Control version • 2
http://winecard.ltd.ua/dev/LampRemote2/index.html?ip=192.168.1.1&dev=1&timeout=200

1. Изменен формат JSON файлов эффектов (более компактный формат, и разбит на четыре файла по 30 эффектов в каждом)
	на текущий момент последний практически пустой, новые эффеты лучше добавлять туда перед часами
2. Добавлена поддержка сохранения найденых ламп, чтобы каждый раз не сканировать без надобности и индикация активной лампы в списке.
3. Улучшена поддержка обработки ошибок и показа уведомлений.
4. Мелкие изменения в дизайне и разные вкусности.
5. Для ленивых и підсліпкуватих (UA) добавлен QR код для подключения к лампе в режиме точки доступа.
6. Добавлена поддержка управления группой
	1. автоматическая активация UI если в списке больше одной лампы
	2. создание группы в один клик и отправка соответствующего списка всем лампам в группе (запоминание состояния)
	3. поддерживается индикация чтобы было понятно в каком режиме находятся лампы 
	( при обьединении в группу лампы загораются фиолетовым (Magenta) цветом, при сбросе все лампы загораются разными цветами)
	( при включени режима цикл On/Off соответственно оранжевым/синим )
 
