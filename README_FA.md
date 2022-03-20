## anbox-dinit
یک پروژه برای استفاده از anbox همراه با dinit

## اینها چیستند؟
این پرونده ها، پرونده هایی برای اجرا کردن anbox در یک سیستم عامل با dinit هستند.
## anbox چیست؟
یک پروژه برای اجرا کردن برنامه های اندرویدی در دیگر سیستم عامل های بر پایه لینوکس (مانند گنو/لینوکس) است. برای اطلاعات بیشتر به تارنمای این پروژه به نشانی https://anbox.io مراجعه کنید.
## چگونه می‌توان این پرونده ها را نصب کرد؟
### قدم اول: نصب کردن ماژول های binder و ashmem
برای اینکار چندین روش وجود دارد:
#### روش اول: استفاده کردن از بسته linux-zen
نصب کردن این بسته با دستور زیر:
'sudo pacman -S linux-zen'
#### روش دوم: کامپایل کردن کرنل لینوکس از کد منبع همراه با ashmem و binder
اگر می‌توانید اینکار را انجام دهید، حتما می‌دانید چطور انجامش دهید.
### قدم دوم: فعال کردن ماژول binder
درصورتی که مرحله قبل را به درستی طی کرده باشید، ماژول های ashmem و binder، به طور پیش‌فرض فعال شدند. فقط لازم است که binder را برای anbox آماده کنیم. برای اینکار پارامتر های زیر را در راه انداز سامانه (بوت‌لودر) تنظیم کنید.
`binder.devices=binder,hwbinder,vndbinder,anbox-binder,anbox-hwbinder,anbox-vndbinder`
### قدم سوم: سوار کردن سامانه پرونده binder (binderfs)
با این دستور شاخه موردنیاز رو بسازید: 'sudo mkdir /dev/binderfs'

با این دستور binderfs را موقتا سوار کنید:'sudo mount -t binder binder /dev/binderfs'

در صورت موفقیت آمیز بودن اینکار، binderfs را در پرونده '/etc/fstab/' تنظیم کنید تا همیشه در هنگام راه اندازی سامانه (بوت)، سوار شود:
‍‍````
binder                         /dev/binderfs binder   nofail  0      0
````
### قدم چهارم: نصب کردن anbox
با دستورات زیر بسته anbox-nosystemd-git را نصب کنید:
````
cd ~
git clone https://github.com/Luciogi/artix_pkg.git
cd artix_pkg/anbox-nosystemd-git
sudo pacman -S --needed base-devel
makepkg -si
````
حال anbox-dinit را نصب کنید:
````
cd ~
git clone https://gitlab.com/mobin2008/anbox-dinit.git
cd anbox-dinit
makepkg -si
````
### قدم پنجم: فعال کردن دیمن ها و خدمات (سرویس ها)
با دستور زیر anbox-container-manager را فعال کنید:
````
sudo dinitctl start anbox-container-manager # برای بارگذاری در همین جلسه کنونی
sudo dinitctl enable anbox-container-manager # برای بارگذاری در مراحل بوت
````
با دستور زیر anbox-session-manager را فعال کنید **بروزرسانی: نیازی ندارد، دیگر استفاده نشود**
````
sudo dinitctl start anbox-session-manager # برای بارگذاری در همین جلسه کنونی
sudo dinitctl enable anbox-session-manager # برای بارگذاری در مراحل بوت
````
### قدم ششم: از anbox استفاده کنید
کار تمام است، حال شما می‌توانید از anbox استفاده کنید.
## مجوز:
حق تکثیر (ح) ۱۴۰۰ مبین آیدین فر
نگارش سوم پروانه عمومی همگانی گنو (GPLv3)
برای اطلاعات بیشتر، پرونده LICENSE را ببینید
## نماگرفت‌‌ها


