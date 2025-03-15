This guide is an update to [Vudek's](https://osu.ppy.sh/u/Vudek) one.
# Chapter 0: Preparation
> [!NOTE]
> This section only includes installing onto a separate SSD
## 0.1 Obtaining Arch Linux ISO File
To obtain the ISO file, visit the official Arch Linux site - https://archlinux.org/download

It can be downloaded with BitTorrent

![](../photos/Pasted%20image%2020250305174126.png)

However, if you don't want to use torrents, you can download it from your country's mirror. To do this, scroll down, and find your country. For example, let's use Germany.

![](../photos/Pasted%20image%2020250305174858.png)

Pick any mirror

Then, click on the file `archlinux-{year.month.01}-x86_64.iso`

![](../photos/Pasted%20image%2020250305175035.png)

## 0.2 Making a Bootable Flash Drive
Instead of creating one with Rufus, we will do it through Ventoy.

Why?

1. **The installation won't depend on your Firmware**. You can use both UEFI and Legacy BIOS
2. **Ability to have separate ISO Files to boot from**. On a single flash drive, you can both Windows, Arch Linux and other systems. Somewhat of Swiss Army Knife :D
3. **Convinience, if your flash drive is 32+ GB**. You can use it as both a bootable device, and as a regular flash drive.
Download the Ventoy installer - https://sourceforge.net/projects/ventoy/files/v1.1.05/ventoy-1.1.05-windows.zip/download

Unarchive, open the directory and launch `Ventoy2Disk.exe`:

![](../photos/Pasted%20image%2020250305175703.png)

A window will appear, like so:

![](../photos/Pasted%20image%2020250305175736.png)

In `Device` piok your flash drive, then press `Install`

The program will make sure, that you have backed up your data:

![](../photos/Pasted%20image%2020250305175907.png)

The program will do a ~~retard~~ test, whether you are ready to format your flash drive:

![](../photos/Pasted%20image%2020250305180031.png)

You will be let known of, when the process is finished:

![](../photos/Pasted%20image%2020250305180113.png)

In your explorer, there will be 2 devices: `Ventoy` и `VENTOYEFI`

You need `Ventoy`.

![](../photos/Pasted%20image%2020250305180212.png)

Drop the Arch .iso file, reboot and boot from the flash drive.

I hope you know, how to boot from a flash drive, otherwise, this video might be for you: https://www.youtube.com/watch?v=y2kg3MOk1sY
## 0.3 Boot process
When you have booted from Ventoy, you will see the following menu:

![](../photos/Pasted%20image%2020250305151241.png)

Pick your Arch Linux ISO

![](../photos/Pasted%20image%2020250305151338.png)

Try `Boot in normal mode`. If it fails, try `Boot in grub2 mode`

After ISO initialisation, depending on your firmware, you will see either:

![boot_bios.png](../photos/boot_bios.png)
![boot_uefi.png](../photos/boot_uefi.png)

Pick the first option.
# Chapter 1: Installing
## 1.1 Preparation
After loading, you should see the following:

![Arch_start.png](../photos/Arch_start.png)

First, check your ETHERNET connection with `ping`

![ping.png](../photos/ping.png)

If the packets are being sent and received, your connection is fine.

To stop the process, press Ctrl+C

If you use WI-FI, use `iwd`
> [!NOTE]
> In this guide, I can't show the process. If you know any details, please PR this.

Otherwise, plug your phone into the pc, and use it as a hotspot.
## 1.2 Installing
After checking your Internet connection, run `archinstall`

![archinstall.png](../photos/archinstall.png)

After loading, you will see the following:

![menu.png](../photos/menu.png)
### 1.2.1 Mirrors
Skips the first 2 options, go straight to `Mirrors`

The controls are *arrow keys* and *Enter*

After opening `Mirrors`, you will see the following:

![mirror_region.png](../photos/mirror_region.png)

Pick `Mirror region`

Pick your country. To make it easier, press `/` and write your country in English, then press `Enter`

![regions.png](../photos/regions.png)

This is how it should look like (In my case, `Russia`):

![mirror_result.png](../photos/mirror_result.png)
### 1.2.2 Disk Partitioning
Then `Disk configuration`:

![partitioning.png](../photos/partitioning.png)

Pick `Partitioning`

![best-effort.png](../photos/best-effort.png)

Pick `Use a best-effort default partiotion layout`

![sel_disk.png](../photos/sel_disk.png)

I'm on a VM, so I only have 1 drive, pick the one you want to use. 

Pick a file system:

![btrfs.png](../photos/btrfs.png)

Choose `btrfs`, as a faster file system

![subvolumes.png](../photos/subvolumes.png)

Select `No`

![compression.png](../photos/compression.png)

Pick `Use compression`

This is how it should look like:

![disk_result.png](../photos/disk_result.png)
### 1.2.3 Disk Encryption
Skip `Disk encryption`, unless you want to do it.
### 1.2.4 Swap
Make sure, that `swap` is enabled:
![swap.png](../photos/swap.png)
### 1.2.5 Bootloader
In `Bootloader` pick Grub
![bootloader.png](../photos/bootloader.png)
### 1.2.6 Unified Kernel Images
Keep `Unified kernel images` as default (Disabled)
![UKI.png](../photos/UKI.png)
### 1.2.7 Hostname
You can keep it as default, or use yours. This is how it looks like, in the terminal:

`username@hostname $`

![hostname.png](../photos/hostname.png)
### 1.2.8 Root Password
Enter any, even `1`, but the stronger, the better.

![](../photos/Pasted%20image%2020250304224042.png)

Confirm password, by entering it again:

![](../photos/Pasted%20image%2020250304224929.png)
### 1.2.9 Users
Create a user

![](../photos/Pasted%20image%2020250304224509.png)

Choose `Add a user`

Enter `Username`

![](../photos/Pasted%20image%2020250304224600.png)

Then, a password:

![](../photos/Pasted%20image%2020250304224636.png)

Confirm password, by entering it again:

![](Pasted%20image%2020250304224712.png)

Give super-user (sudo) rights:

![](../photos/Pasted%20image%2020250304224757.png)

Then `Confirm and exit`

![](../photos/Pasted%20image%2020250304224823.png)

### 1.2.10 Profile (Desktop Enviroment and Drivers)
Pick `Type`

![](../photos/Pasted%20image%2020250304225055.png)

Then, choose `Desktop`

![](../photos/Pasted%20image%2020250304225127.png)

Here, we select our desktop enviroments (From now on - DE).

![](../photos/Pasted%20image%2020250304225826.png)

You can install multiple, if you want a similar UI to Windows, pick GNOME or KDE Plasma. Otherwise, you can try tiling window managers. You can choose your DE when logging in. We will be using i3-wm, because it's lightweight, even if it's unusual for beginners (You just gotta get used to it :D). If you want to pick multiple, highlight the selection and press `Tab`, it will be marked as `[x]{Enviroment}`

![](../photos/Pasted%20image%2020250304230006.png)

Then, press `Enter`. You will see the following:

![](../photos/Pasted%20image%2020250304230052.png)

In the menu `Graphics driver` we will be choosing our drivers:

![](../photos/Pasted%20image%2020250304230143.png)

If you use an Nvidia GPU, pick `Nvidia (proprietary)`, however, make sure your GPU supports the latest version. If you have a GTX 1000+, you can live without any problems... *For now*

If you use an AMD or an Intel GPU, pick the corresponding open-source driver.

In `Greeter` tab, pick an authorisation window. I suggest `sddm`

![](../photos/Pasted%20image%2020250304233040.png)

### 1.2.11 Audio Server
In `Audio`, select `pipewire`

![](../photos/Pasted%20image%2020250304233133.png)

--------------- КОНЕЦ ПЕРЕВОДА 

### 1.2.12 Kernel
Здесь мы выбираем само ядро. Вместо дефолтного ядра будем использовать `linux-zen` как ядро с оптимизациями для повышению производительность. Через `Tab` убираем выделение с дефолтного ядра `linux` и через `Tab` выделяем `linux-zen`, затем нажимаем `Enter`

![](../photos/Pasted%20image%2020250304233356.png)

### 1.2.13 Network Settings
Выбираем пункт `Use NetworkManager ...`

![](../photos/Pasted%20image%2020250304233453.png)

### 1.2.14 Additional Packages
Мы установим дополнительные пакеты. Обязательно установите `curl`, файловый менеджер, например `nemo` и браузер, например `chromium` или `firefox`

![](../photos/Pasted%20image%2020250304233814.png)

### 1.2.15 Additional Repositories
Включаем `multilib`. Не совсем обязательный этап, ибо благодаря одному скрипту как раз включит данный дополнительный репозиторий

![](../photos/Pasted%20image%2020250304233952.png)

### 1.2.16 Time Zone
Устанавливаем часовой пояс. Нажав `/` можно легче найти нужный часовой пояс. Пишите на английском (В моём случае Екатеринбург)

![](../photos/Pasted%20image%2020250304234109.png)

### 1.2.17 NTP
Пункт `Automatic time sync (NTP)` оставьте по дефолту включенным

![](../photos/Pasted%20image%2020250304234245.png)

## 1.3 Confirmation
> [!CAUTION]
> Перед тем как начать устанавливать систему, убедитесь, что вы всё верно указали. В особенности конфигурацию дисков.

Выбираем пункт `Install` и если всё хорошо, то нажимайте `Yes`

![](../photos/Pasted%20image%2020250304234621.png)

Начинается установка и осталось только ждать.

![](../photos/Pasted%20image%2020250304234654.png)

Пока идёт установка, можете поддержать меня подпиской на мои [соц. сети](https://kartavkun.github.io/site/) . 

## 1.4 Additional Settings
После установки у вас появится данное сообщение:

![](../photos/Pasted%20image%2020250304235146.png)

Выбираем `No`

Но если вы знаете, что делать, то можете нажать `Yes` и сделать свои дела (Вопрос, зачем вы читаете этот гайд тогда?)

После мы перезагружаемся:

![](../photos/Pasted%20image%2020250304235352.png)
# 2. Загрузка в установленную ОС
## 2.1 Загрузчик Grub
Мы в загрузчике GRUB. Пока у нас только наш Арч. Выбираем `Arch Linux`

![](../photos/Pasted%20image%2020250304235515.png)

## 2.2 Вход
После загрузки системы мы попадаем в окно ввода пароля и выбор пользователя:

![](../photos/Pasted%20image%2020250304235711.png)

В меню `Session` в левом верхнем углу можно выбрать рабочее окружение, в которое мы войдём. Так как мы устанавливали только `i3-wm`, у нас только `i3` и `i3 (with debug log)`. Разницы на работоспособность между ними нет.

![](../photos/Pasted%20image%2020250304235859.png)

Теперь вводим пароль от пользователя, который мы устанавливали при установке и созданию пользователя:

![](../photos/Pasted%20image%2020250305000003.png)

## 2.3 Вход в i3-wm
Мы увидем данные сообщение, где мы просто нажимаем два раза `Enter`

![](../photos/Pasted%20image%2020250305000109.png)

![](../photos/Pasted%20image%2020250305000133.png)

## 2.4 Установка стартовых настроек для i3

Нам надо запустить c помощью комбинации клавиш `Win+Enter`. ОСТОРОЖНО, ФЛЕШБЕНГ

![](../photos/Pasted%20image%2020250305001215.png)

Для установки стартовых настроек для i3-wm введите следующую команду:

```bash
curl -fsSL https://shorturl.at/MRENP | sh
```

> [!NOTE]
> Не переживайте, я сократил ссылку, чтоб не пришлось долго и скрупулёзно писать долгую ссылку для запуска скрипта из Github.
> Вот репозиторий с настройками - https://github.com/kartavkun/i3-dotfiles-minimal

После того, как вы увидите данное сообщение, перезагрузите конфиг i3 комбинацией клавиш `Win+Shift+R`

![](../photos/Pasted%20image%2020250305001645.png)

Вы увидите, что бар из низа перейдёт вверх, а также он будет куда чище:

![](Pasted%20image%2020250305001756.png)

## 2.5 Донастройка

Вы можете закрыть этот белый, ужасный терминал комбинацией клавиш `Win+Q`(Комбинация клавиш для закрытия активного окна, т.е. на который вы сфокусированы), и открыть новый терминал:

![](../photos/Pasted%20image%2020250305001947.png)

Теперь нам надо открыть конфигурационный файл i3. Для этого введите команду:
```bash
nano .config/i3/config
```

Откроется текстовый редактор `nano`, через который мы будем донастраивать i3 под ваши предпочтения

![](../photos/Pasted%20image%2020250305105904.png)

Управление осуществляется стрелками.

### 2.5.1 Установка языка и смены языка
По умолчанию стоит только английский язык. Чтоб добавить русский, вам нужно переместиться на строку: `set $layouts us` и дописать запятую, и слитно написать `ru`

![](../photos/Pasted%20image%2020250305002435.png)

По умолчанию для смены языка используется сочетание клавиш `Win+Space` (как и на Windows), но если вы хотите сменить на нужную вам комбинацию, например `Alt+Shift`, то вас нужно обратиться к строке `grp:win_space_toggle` и поменять `win_space_toggle` на `alt_shift_toggle`

![](../photos/Pasted%20image%2020250305103130.png)

Сохраняем файл конфигурации нажатием клавиш `Ctrl+O`, `Enter`

Затем перезагружаем конфиг комбинацией клавиш `Win+Shift+R`

Для выхода из `nano` нажмите `Ctrl+X`

### Заметка
> [!NOTE]
> По сути, тут чисто индивидуальщина, и если вы хотите, можете настроить, можете и не настраивать. Решайте сами. Если вы что-то хотите от себя добавить для вашей красоты, то Google/ChatGPT в помощь. Думаю не глупые, разберётесь
### 2.5.2 Фикс трея
По дефолту трей отключен, ибо универсальной настройки нет и если у тебя несколько мониторов, то это проблема та ещё, потому давай настроем:

Сначала нам нужно узнать, к какому выводу относить наш монитор(ы). Пишем команду `xrandr`:

![](../photos/Pasted%20image%2020250305103420.png)

Для этого я решил уже зайти не с виртуалки, и как вы видите, тут у меня несколько мониторов. Тут мы видим доступные разрешения дисплеев для каждого монитора и доступная для них герцовка. В моём случае это `HDMI-A-0`.

Затем заходим в наш конфиг файл и находим строку `# set $tray {your preferred output}`. Её надо раскомментировать (убрать решётку в начале строки) и заменить `{your preferred output}` на маркировку вашего вывода. В моём случае это `HDMI-A-0`

![](../photos/Pasted%20image%2020250305103918.png)

Сохраняем файл и перезагружаем конфиг. И теперь в правом верхнем углу у нас появился трей:

![](../photos/Pasted%20image%2020250305104029.png)

### 2.5.3 Настройка расположения мониторов
> [!NOTE]
>Если у вас один монитор или то, как у вас по умолчанию работают мониторы, можно этот пункт скипнуть.
>Также если у вас карта от Nvidia, вам нужно установить `nvidia-settings` командой `sudo pacman -S nvidia-settings`, открыть через терминал с `sudo`, т.е. `sudo nvidia-settings`. О том, как это настройть, сделайте кто-нибудь, я православный АМДшник :D

Вновь обращаемся к `xrandr`.

У меня три монитора, один из которых находиться справа от основного, и также повёрнут вертикально, а другой ниже основного.

Чтоб настроить как мне надо, мне надо ввести следующие команды:
`xrandr --output {монитор}(в моём случае HDMI-A-1) --right-of {монитор}(справа от) --rotate {left/right(пробуйте один из этих вариантов, если монитор расположен вертикально, чтоб найти правильное расположение)}`
`xrandr --output {другой монитор}(в моём случае DVI-D-0) --below {монитор}(под)`

Для дополнения ещё напишу команду для основного монитора:
`xrandr --output {монитор}(основной) --primary(сделать монитор основным) --rate {герцовка}(на случай, если герцовка неправильно стоит. В списке мониторов активная герцовка обозначается звёздочкой)`

Чтоб не запутаться во флагах, вот список, который нам нужен:

![](../photos/Pasted%20image%2020250305105255.png)

Теперь мы добавим эти команды в конфигурационный файл. Заходим и находим нужные строки:

![](../photos/Pasted%20image%2020250305105949.png)

Здесь мы раскомментируем строку `exec_always --no-startup-id xrandr {settings}` и меняем `{settings}` на нужные настройки. Если их несколько, то пишем следующие строки, которые будут начинаться с `exec_always --no-startup-id xrandr {ваши настройки}`.

В моём случае получилось вот так:

![](../photos/Pasted%20image%2020250305110351.png)

Сохраняем файл и перезагружаем конфиг. 

### 2.5.4 Установка обоев
Если вы хотите вместо чёрного экрана какие-нибудь обои, то для этого вам нужно установить программу `feh` 
```bash
sudo pacman -S feh
```
Затем скачать предпочтительные обои в нужном месте. Желательно, чтоб вы их сразу не удалили. Например я установлю такие обои:

![](../photos/black-white.jpg)

Используйте файловый менеджер `nemo`, который мы устанавливали до этого. Можете создать отдельную директорию, чтоб случайно из загрузок её не удалить:

![](../photos/Pasted%20image%2020250305111414.png)

Теперь просто выделяем нашу картинку и копируем её.

Затем заходим в файл конфигурации и находим строку `#exec_always --no-startup-id feh --bg-scale ...` , раскомментируем и удаляем `{set path to your background image}`, и вставляем путь к нашей картинке (ЧТОБ ВСТАВИТЬ НАЖИМАЕМ НЕ ПРОСТО Ctrl+V, А ДОБАВЛЯЕМ Shift, т.е. Ctrl+Shift+V)

Должно получиться примерно вот так:

![](../photos/Pasted%20image%2020250305111816.png)

Затем сохраняем файл и перезагружаем конфиг.

Как вы можете видеть, всё заработало

![](../photos/Pasted%20image%2020250305111906.png)
## 2.6 Горячие клавиши
Шпаргалка для новичков i3-wm:

> Win+Enter - Запуск терминала
> 
> Win+R - Запуск лаунчера приложений
> 
> Win+Q - Закрыть активное окно


> Win+ЛКМ - Изменение положения активного окна
> 
> Win+ПКМ - Изменение размеров активного окна
> 
> Win+Shift+Space - Сделать активное окно в виде "окна" и обратно
>
> Win+1, 2, 3 ... 0 - Переход на рабочий стол 1, 2, 3 ... 10
> 
> Win+Shift+1, 2, 3 ... 0 - Перенос активного окна на рабочий стол 1, 2, 3 ... 10
>
> Ctrl+Win+Right - Переход на следующий рабочий стол
> 
> Ctrl+Win+Left - Переход на предыдущий рабочий стол


> Win+Shift+R - Перезагрузка конфига (для изменений в конфигурационном файле)

# 3 Установка osu!stable
Вы можете открыть браузер, чтоб скопировать ссылку для запуска скрипта, который установит игру, вместе с драйверами и другими зависимостями. В терминал нужно вписать следующую команду:
```bash
curl -fsSL https://raw.githubusercontent.com/kartavkun/arch-osu-wine/main/setup.sh | sh
```

Установка пройдёт полностью автоматически. Если вас просят ввести пароль, вводите и ждите конца установки, пока не появится данное сообщение:

![](../photos/Pasted%20image%2020250305112824.png)

Помимо самой игры будут установлены OpenTabletDriver, настройки звука с меньшей задержкой, файлы для работы Wootility, Drunkdeer-Antler и веб-драйвера Sayo-device'а.

Готово!

# 4 Запуск osu!stable
Для запуска osu!, пропишите в терминале команду для корректного первого запуска:
```
.local/bin/osu
```
После того как у вас запуститься игра, можете выходить и отныне запускать игру через лаунчер приложений. 

## 4.1 Решение проблем
> [!NOTE]
> Если нет звука или он "пердит", то как это решить есть здесь: https://github.com/kartavkun/arch-osu-wine?tab=readme-ov-file#troubleshooting .
> 
> Если не работает OpenTabletDriver, то надо перезагрузить систему, чтоб точно всё заработало (кнопка справа сверху).
> 
> На браузерах, кроме Фаерфокса и его форках (Шарю только за Librewolf) есть проблема, что через браузер открыть файлы для карт и скинов не всегда получается, так что открывать их надо через файловый менеджер. Возможно смогу пофиксить
> 
> Остальные проблемы пока не знаю, ибо не встречал прям критичных. 
> Обо всём напишу позже.

# 5 Дополнения
## 5.1 Discord
Если вы хотите использовать Дискорд для трансляций со звуком, используйте [Vesktop](https://github.com/Vencord/Vesktop) как клиент с Венкорд, лучше поддерживается на Линукс, чем официальный клиент:
```bash
yay -S vesktop-bin
```
## 5.2 osu! trainer
Если нужно установить osu тренер (для создания дифф с ускорением, сменой AR, OD, CS, HP), надо написать следующее:
```
echo "[home_hwsnemo_packaged-wine-osu_Arch]
Server = https://download.opensuse.org/repositories/home:/hwsnemo:/packaged-wine-osu/Arch/\$arch" | sudo tee -a /etc/pacman.conf

key=$(curl -fsSL https://download.opensuse.org/repositories/home:hwsnemo:packaged-wine-osu/Arch/$(uname -m)/home_hwsnemo_packaged-wine-osu_Arch.key)
fingerprint=$(gpg --quiet --with-colons --import-options show-only --import --fingerprint <<< "${key}" | awk -F: '$1 == "fpr" { print $10 }')
sudo pacman-key --init
sudo pacman-key --add - <<< "${key}"
sudo pacman-key --lsign-key "${fingerprint}"

sudo pacman -Sy --needed home_hwsnemo_packaged-wine-osu_Arch/cosu-trainer
```

Также нужно в конфиг файле `i3` раскомментировать строку `# exec --no-startup-id osumem` (убрать решётку в начале строки), потому что без неё тренер не будет работать, ибо не сможет читать память игры и находить активную карту и сложность, которую вы хотите поменять
## 5.3 osu!lazer
```bash
yay -S osu-lazer-bin
```
## 5.4 zapret (только для жителей России)
Если вы из России, для Ютуба и Дискорда нужно установить zapret (как и на винде). Как установить и т.д. найдёте в моём репозитории - https://github.com/kartavkun/zapret-discord-youtube
