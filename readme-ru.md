# Гайд по настройке Windows на русском:
## Гайд собран по настройкам Windows 11, так что некоторые параметры могут отсутствовать или называются по другому в Windows 10.
#### 0. Установка всех доступных обновлении
Перейдите в раздел **Обновления Windows** и установите все доступные обновления.
#### 1. Отключаем автоматического обновления драйверов:
- WIN+R -> **regedit** -> **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows** -> Создаём раздел (*папку*) **WindowsUpdate** -> И в ней создаём параметр Dword32 с названием **ExcludeWUDriversInQualityUpdate** со значением **1**.
- Дальше переходим по **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\DriverSearching** находим **SearchOrderConfig** и выставляем значение **0**. 
#### 2. Установка драйверов
 1) Установите последние драйвера на чипсет, лан, вайфай & блютуз, звук, их можно взять с сайта материнской платы.
#### 3. Установка драйвера на ГПУ
   - Сначала удаляем через DDU дефолтный драйвер на ГПУ который сам установился, после чего ПК сам перезапустится.
   - Установите драйвера на ГПУ через Nvcleanstall (для nvidia) или Radeon Software Slimmer (для AMD).
___
> Инструкция по Nvcleaninstall:
1) Скачиваем последний драйвер GeForce Game Ready Driver для вашего ГПУ.
2) Запускаем Nvcleanstall.
3) Жмём на раздел Use driver files on disk и указываем путь до драйвера.
4) Отключаем все галочки и идём к 8 пункту.
    
   :warning: Если вам нужен GeForce Experience, звук по HDMI и/или USB-C порт с видеокарты, то прочтите 5-7 шаг.
5) Для звука по HDMI поставьте галочку напротив HD Audio via HDMI.
6) Для GeForce Experience поставьте галочку напротив GeForce Experience, NV Container, Telemetry, NV Backend, NodeJS.
7) Для USB-C поставьте галочку напротив USB-C driver.
   
    :warning:Если у вас ноутбук поставьте галочку напротив Optimus и USB-C!

8) Нажимаем *Next* и во вкладки **Tweaks** выбираем **Disable Installer Telemetry, Disable MPO**. 
   
   :triangular_flag_on_post:Если ранее не удаляли старый драйвер через DDU, то поставьте галочку напротив **Perform a clean installation**. 
   
   Далее нажимаем **Show Expert Tweaks**, выбираем Disable Driver Telemetry, Disable Nvidia HD Audio device sleep timer, Disable HDCP,  
    >Enable Message Signaled Interrupts 
    >>* Interrupt Policy: **Default** 
    >>* Interrupt Priority: **High**

    >Rebuild digital signature 
    >>* **Use method compatible with EasyAntiCheat**. 
    >>* **Auto accept driver unsigned warning**.

9) Нажимаем **Next** и потом **Install**, устанавливаем драйвер из окна которая появится.
10) Настроить панель (фото с настройками в репозитории)
___

>Инструкция по Radeon Software Slimmer:
1) Скачиваем последний драйвер Recommended с сайта AMD.
2) Запускаем Radeon Software Slimmer.
3) Жмём на раздел **Pre Install** и указываем путь до драйвера.
4) Указываем путь для распаковки (создаём новую папку и указываем её, папка должна быть пустая.)
5) Отключаем все пункты в Scheduled Tasks.
6) В Packages оставляем только "**AMD Display Driver; AMD Settings; AMD WVR64; Branding64**", остальное выключаем.
 
:warning:Если вам нужен звук с HDMI, то оставьте: **"HDMI Audio Driver"; "High Definition Audio Controller"**.

:warning:Если вам нужна запись ReLive то оставьте: **"DVR64"**.

7) Нажимаем **Modify Installer** и потом **Run Installer**, устанавливаем драйвер из окна которая появится.
8) Настроить панель (фото с настройками в репозитории)
___

#### 4. Установка нужного софта:
* Установить пакет [Visual C++ AIO](https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/)
* Установить [DirectX](https://www.microsoft.com/en-us/Download/confirmation.aspx?id=35)
* Установить [.Net Framework 4.8.1](https://dotnet.microsoft.com/en-us/download/dotnet-framework)
* Установить [7zip](https://www.7-zip.org/)
* По желанию установить [Java JDK](https://www.oracle.com/cis/java/technologies/downloads/#jdk21-windows)
___
#### 5. Проверка файлов системы
- Вставьте команду в CMD от имени Администратора: **DISM/Online/Cleanup-Image/ScanHealth**

#### 6. Настройки: 
- Удалите приложения UWP которыми не пользуетесь: Settings -> Apps -> Installed Apps.
- Настройки поиска Windows -> Найти мои файлы -> классический.
- Настройки -> Игры -> Захваты -> отключить всё.
- Настройки -> Игры -> Включите игровой режим.
- Настройки -> Конфиденциальность -> все выключено (кроме микрофона и камеры если они вам нужны).
- Настройки -> Система -> Уведомления (снять все галочки) -> Дополнительные настройки -> снять все галочки.
- Настройки -> Система -> Память -> Контроль памяти -> Отключить.
- Настройки -> Система -> Общий доступ -> ВЫКЛ.
- Настройки -> Приложения -> Общий доступ к устройствам и Архив приложений (Выкл).
- Настройки -> Центр безопасности Windows -> Настройки -> Уведомления -> Выкл.
- Настройки -> Специальные возможности -> Отключить **Визуальные эффекты** и **Эффекты прозрачности**.
- Настройки -> Система -> Дисплей -> Графика -> Изменить настройки графики по умолчанию -> Включить HAGS и оптимизацию для оконных игр.
- Настройки -> Система -> Дисплей -> Поставьте максимальную частоту обновления вашего монитора.
- Настройки -> Центр безопасности Windows -> Защита на основе репутации -> Все выключено.
- Настройки -> Центр безопасности Windows -> раздел **Управление приложениями и браузером** -> **Защита на основе репутации** -> **Параметры защиты на основе репутации** -> Отключите все пункты.
- Настройки -> Центр Обновления -> Дополнительные Параметры -> Оптимизация Доставки -> Отключить.
#### 7. Панель Управления:
- Панель управления -> Мышь -> снять флажок **Повысить точность указателя**.
- Панель управления -> Система и безопасность -> Изменить настройки UAC -> Никогда не уведомлять.
- Панель управления -> Центр Управления Сетями -> Изменение Параметров Адаптера -> ПКМ по вашего адаптера LAN/WIFI -> Свойства -> отключить всё, кроме QoS и IPv4.
- Панель управления -> Отключить брандмауэр.
- Панель управления -> План питания -> Максимальная Производительность -> Действия кнопок питания -> быстрый запуск и гибернация (ВЫКЛ).
 
>:warning:Если нет режима "Максимальная Производительность" то напишите в cmd (от имени админа): **powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61**

- Отключение гибернации в cmd (от имени админа): **powercfg /h off**

:white_medium_square:*Совет: Режим "Сон" или "Гибернация" не перезагружает систему и не очищает данные в памяти поэтому стоит их отключить.*
#### 8. Отключение Индексации
   Проводник -> Локальный Диск С -> ПКМ -> Свойства -> 
  - Снимаем галочку с "Разрешить индексировать" и Принимаем.
  
  После отключения идём обратно
  - Вкладка Сервис -> Оптимизация и Дефрагментация диска -> выключена *(делайте это вручную желательно раз в неделю)*.

#### 9. Производительность (Отключение анимации)
- Win+R -> **sysdm.cpl** -> вкладка **Дополнительно** -> раздел **Быстродействие** кнопка *Параметры* -> **Обеспечить наилучшее быстродействие** -> **Применить**

#### 10.   Службы которые можно отключить:
**DiagTrack; TrkWks; WalletService; wisvc; WpcMonSvc; SysMain; VSS; WerSvc; WSearch, lfsvc, Spooler** (Spooler -> если нет принтера).
#### 11.  Отключите результаты из интернета в поиске:
WIN+R -> regedit -> **HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Windows\Explorer** -> Создаём параметр DWORD32бит с названием **DisableSearchBoxSuggestions** и со значением **1**.
#### 12.  Отключите фоновые приложения: 
WIN+R -> gpedit.msc -> Конфигурация компьютера > Административные шаблоны > Компоненты Windows > Конфиденциальность приложений -> Разрешить приложениям Windows работать в фоновом режиме -> "Включено" и ниже установите "Force Deny".
#### 13.  Отключение Windows Copilot:
WIN+R -> gpedit.msc -> Конфигурация пользователя > Административные шаблоны > Компоненты Windows > Windows Copilot -> Отключить Windows Copilot выберите «Включено».
#### 14.  Отключите Защитник Windows (используйте все три пункта):
1) WIN+R -> regedit -> **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender** -> создайте Dword32bit с именем **DisableAntiSpyware** -> значение **1**
3) WIN+R -> gpedit.msc -> Конфигурация компьютера > Административные шаблоны > Компоненты Windows > Антивирусная программа Microsoft Defender -> Отключить антивирусную программу Mirosoft Defender -> **Включено**.
4) WIN+R -> gpedit.msc -> Конфигурация компьютера > Административные шаблоны > Компоненты Windows > Антивирусная программа Microsoft Defender > Постоянная защита -> Отключить постоянную защиту -> **Включено**.
#### 15.  Отключение MPO:
1) Быстрый способ: скачать и запустить файл [disable_mpo с сайта Nvidia](https://nvidia.custhelp.com/app/answers/detail/a_id/5157)
   
:white_check_mark:Рекомендую второй способ, вручную.

2) Вручную: WIN+R -> regedit -> **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Dwm** -> Создаём параметр DWORD32бит с названием **OverlayTestMode** и со значением **5**.
#### 16.  Отключаем Windows GameBar (WIN+G будет работать), использовать оба шага:
   **Первый шаг**:
   >Проводник -> Диск С -> Windows -> System32 -> GameBarPresenceWriter.exe -> ПКМ -> Вкладка Безопасность -> Дополнительно -> Второй пункт, где Владелец нажмите Изменить -> здесь, где пустое место надо написать имя вашего аккаунта (его можно узнать в Параметры -> Аккаунты -> сверху будет написано имя вашего локального аккаунта или почта если вы ранее вошли в аккаунт) -> После чего написали имя нажмите на Проверить Имена -> Нажмите Применить потом Готово -> нажмите Добавить -> Выберите субъект -> Опять вводите имя пользователя -> Готово -> Во вкладке Общие Разрешения поставьте галочку напротив Полный Доступ -> Применяем и выходим -> Опять заходим -> ПКМ -> Вкладка Безопасность -> Дополнительно -> Второй пункт, где Владелец нажмите Изменить -> вместо нашего имени вводим NT Service\TrustedInstaller -> нажмите на Проверить Имена -> ОК -> Применить -> ОК -> ОК -> Теперь переименуйте файл (просто добавьте в конце несколько цифр).

**Второй шаг**:
>WIN+R -> regedit -> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsRuntime\ActivatableClassId\Windows.Gaming.GameBar.PresenceServer.Internal.PresenceWriter ->ПКМ по папке -> Разрешения -> Добавить -> пишем имя аккаунта -> нажмите на Проверить Имена -> Дополнительно -> где Владелец нажмите Изменить -> пишем имя аккаунта -> нажмите на Проверить Имена -> Применить потом Готово -> Поставьте галочку где Полный Контроль -> Закройте -> измените ActivationType -> значение 0.
#### 17.  Удаление виджетов Windows 11 
Команда для Powershell: **winget uninstall "windows web experience pack"** 
#### 18.  Отключение "Изоляция ядра"
Во первых проверьте включена ли у вас виртуализация, потому что если она включена, вам придется отключить изоляцию ядра из **Безопасность Windows**. Если вы не используете виртуализацию то смело можете её отключить в BIOS'е. или отключить Изоляцию Ядра в Windows.
>**Безопасность Windows -> Безопасность устройства -> Изоляция ядра -> Сведения об изоляции ядра -> Целостность памяти -> Выкл**.
#### 19.  Настройка сетевого адаптера
  - Диспетчер устройств -> Ваш сетевой адаптер -> 
    -  Управление питанием -> Снять все галочки. 
    -  Отключите во вкладке Advanced -> **Energy-Efficient Ethernet; Gigabit Lite; Green Ethernet; Power Saving Mode; Всё где есть Wake on magic; Shutdown Wake-On-Lan**.

#### 20.  Переключение видеокарты в режиме MSI
Скачайте [MSI utility v3](https://www.mediafire.com/file/ewpy1p0rr132thk/MSI_util_v3.zip/file) и запустите приложение от имени администратора -> найдите вашу видеокарту и поставьте галочку в поле "**msi**", после чего нажмите "**Применить**".
#### 21.  Отключение PowerThrottling 
:warning:Использовать только для настольных ПК!

>WIN+R -> regedit -> **Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerThrottling** -> **PowerThrottlingOff** -> **1** .
#### 22.  Отключите ненужные устройства в Диспетчере устройств.
Диспетчер устройств -> Отключить: **Microsoft GS Wavetable Synth; Composite Bus Enumerator; Microsoft Hyper-V Virtualization; Microsoft Virtual Drive Enumerator; NDIS Virtual Network; Remote Desktop Device; UMBus Root Bus Enumerator**.
#### 23.  Автоматический перезапуск приложений при запуске системы
Настройки -> Учетные записи -> Параметры входа -> Отключите переключатель "Автоматически сохранять мои перезапускаемые приложения и перезапускать их, когда я снова вхожу в систему".

:white_medium_square:Совет: Windows 11 может сохранять и перезапускать определенные приложения при перезагрузке компьютера и входе в систему. Однако если вы хотите повысить скорость работы компьютера, лучше отключить эту функцию.
#### 24.  Отключите Teredo (функция ipv6 вызывающую задержку):
- WIN+R -> CMD -> netsh interface teredo set state disabled
(CMD для включения: netsh interface teredo set state default )
#### 25.  Как отключить значок уведомления в системном трее:
- WIN+R -> gpedit.msc -> User Configuration > Administrative Templates > Start Menu and Taskbar -> Remove Notifications and Action Center -> Enabled -> Применить/OK
#### 26.  Отключение Wi-Fi Sense
:triangular_flag_on_post: *Wi-Fi Sense* - это инструмент для Windows, предназначенный для сбора данных о публичных точках доступа Wi-Fi, например в кофейнях или общественных зданиях. Он собирал полезные данные о точке доступа, такие как скорость и уровень сигнала, и загружал их в базу данных
- WIN+R -> **regedit** -> **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WcmSvc\wifinetworkmanager\config** -> **AutoConnectAllowedOEM** -> **0**.
#### 27. Установите нужные вам программы.
#### 28. Отключить ненужные приложения из автозапуска.
#### 29. Очистка системы:
- WIN+R -> **%temp%** -> Удалить всё.
- WIN+R -> **temp** -> Удалить всё.
- WIN+R -> **prefetch** -> Удалить всё.
- WIN+R -> **cmd** -> ipconfig /flushdns
#### 30.  Дополнительный софт:
- Активация Windows навсегда (команда для Powershell): irm https://massgrave.dev/get | iex
- Windows Defender Removal: https://github.com/ionuttbara/windows-defender-remover
- Remove Edge: https://github.com/ShadowWhisperer/Remove-MS-Edge
- AllInOne ToolBox: https://github.com/ChrisTitusTech/winutil
- O&O ShutUp10++: https://www.oo-software.com/en/shutup10
- DISM++: https://github.com/Chuyu-Team/Dism-Multi-language/releases
- Autoruns: https://learn.microsoft.com/en-us/sysinternals/downloads/autoruns
- DeviceCleanup: https://www.majorgeeks.com/files/details/device_cleanup_tool.html
- explorerpatcher для настройки/кастомизации Windows 11 :warning:Внимание, могут возникнуть проблемы (краш, синий экран) https://github.com/valinet/ExplorerPatcher