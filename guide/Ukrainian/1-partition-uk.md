<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">


# Запуск Windows на Xiaomi Pad 5

Цей крок потрібен щоб ми створили розділи, де буде знаходитись Windows

### Необхідні файли

- ОС Windows 10 або вище

- ```Розблокований завантажувач``` (якщо він заблокований і ви не знаєте як його розблокувати використовуйте [цей](https://github.com/Ilya114/Port-Windows-11-Xiaomi-Pad-5/blob/main/guide/Ukrainian/unlock-bootloader-uk.md) посібник)

- [```Відновлення```](https://github.com/ArKT-7/twrp_device_xiaomi_nabu/releases/tag/mod-win)

- [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools)

> [!NOTE]
> Ви можете використовувати будь-який Android для подвійного завантаження - MIUI/Hyper OS або будь-яке іншу прошивку

> [!WARNING]
> Усі ваші дані буде видалено! Зробіть резервну копію, якщо потрібно
> НЕ ПЕРЕЗАВАНТАЖУЙТЕ ПЛАНШЕТ, якщо вважаєте, що зробили помилку, зверніться за допомогою в [Telegram-чат](https://t.me/nabuwoa)

> Не знаєте, як почати? Просто розпакуйте завантажений [```Android platform tools```](http://developer.android.com/studio/release/platform-tools), у теку (наприклад ```"C:\platform-tools"```), а потім відкрийте `cmd` або `powershell` як адміністратор і введіть:

```cmd
cd "шлях\до\platform-tools"
```
> Замініть ```"шлях\до\platform-tools"``` фактичним шляхом до папки platform tools

> [!WARNING]
> Якщо ви видалили будь-який розділ використовуючи diskpart, Windows рано или пізно відправить команду пам'яти, яка буде неправильно розпізнана, і тому пам'ять буде стерта.
> 
> Усі ваші дані будуть видалені! Зробіть резервне копіювання, якщо потрібно.
> 
> Усі команди були перевірені.
>
> НЕ ПЕРЕЗАВАНТАЖУЙТЕ ВАШ ПЛАНШЕТ якщо думаєте, що зробили помилку - зверніться в [Telegram-чат проекту](https://t.me/nabuwoa).

#### Завантажте TWRP через комп'ютер за допомогою fastboot
```cmd
fastboot boot <recovery.img>
```

##### Запустіть скрипт розмітки
> Якщо скрипт попросить запустити його ще раз, то так і зробіть

> Це необов'язково, але ви можете встановити власні розміри за допомогою цього сценарію

> Щоб встановити власні розміри, виконайте ``adb shell partition [цільовий розмір розділу з Windows у ГБ]``

> Переконайтеся, що ви не додаєте GB в кінці, лише кількість
```cmd
adb shell partition
```

### Створіть резервну копію наявного образу завантаження 

```cmd
adb shell "dd if=/dev/block/platform/soc/1d84000.ufshc/by-name/boot$(getprop ro.boot.slot_suffix) of=/tmp/normal_boot.img" && adb pull /tmp/normal_boot.img
```

#### Перевірте, чи запускається Android 
> Перезавантажте, щоб перевірити, чи працює Android. Якщо він не завантажується, зітріть усі дані та повторіть спробу. 

```cmd
adb reboot
```

## [Наступний крок: отримання root](/guide/Ukrainian/2-rootguide-uk.md)
