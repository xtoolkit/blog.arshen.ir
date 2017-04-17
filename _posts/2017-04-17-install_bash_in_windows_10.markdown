---
title: نصب bash در ویندوز 10
date: 2017-04-17 15:59:00 +04:30
categories:
- wsl
tags:
- wsl
- lxss
- ubuntu
- windows_10
image:
  path: "/uploads/lxss.png"
  height: 768
  width: 1366
---

![lxss.png](/uploads/lxss.png)
با انتشار نسخه Redstone1 ویندوز 10، مایکروسافت قابلیت زیرسیستمی اوبونتو (WSL یا LXSS) را به صورت آزمایشی برای توسعه دهندگان فعال کرد.
> قبل از ارائه این نسخه، اوبونتو سیستم عامل اصلی لپ تاپم بود که به دلایل عدم پشتیبانی صحیح از کارت گرافیک و تلوزیون تصمیم به نصب این نسخه از ویندوز 10 افتادم. و بعد از 6 ماه نسخه Redstone2 منتشر شد و بهبود های خیلی خوبی در WSL انجام شد. به طوری که `%PATH%` ویندوز به `$PATH` اوبونتو اضافه شده بود. و همچنین با انجام چند تغییر ساده تونستم این کار رو برعکس هم انجام بدم. به طوری که `PHP` و `Java` در wsl نصب کردم و تو `cmd` ویندوز از اون استفاده میکنم.

در این مطلب به آموزش فعال و نصب wsl در ویندوز 10 نسخه 15063(1703) یا همان Redstone2 خواهیم پرداخت.

<!-- more -->
## در WSL چه کار هایی میتوانیم انجام دهیم؟

WSL تمامی کارها و ابزار های روزمره یک توسعه دهنده را در بر میگیرد. به طور مثال ابزار های زیر به طور کامل آزمایش شده و به طور کامل کار می کنند:

* **ابزار های هسته:** apt, sed, grep, awk, top, tmux, ssh, scp و ...
* **پوسته ها (Shells):** Bash, zsh, fish و ...
* **ابزار های توسعه:** vim, emacs, nano, git, gdb و ...
* **پلتفرم ها و زبان های برنامه نویسی:** Node.js & npm, Ruby & Gems, Java & Maven, Python & Pip, C/C++, C# & .NET Core & Nuget, Go, Rust, Haskell, Elixir/Erlang و ...
* **سیستمی و سرویس:** sshd, Apache, lighttpd, nginx, MySQL, PostgreSQL
* و کلی ابزار دیگر

## نیاز های سیستمی

* OS Build: 15063 OR 14393 (پیشنهادی 15063)
* System tyoe: x64

برای پی بردن به این اطلاعات میتوانید به مسیر `Settings → System → About` مراجعه کنید.

## نصب قدم به قدم

### قدم اول: فعال کردن حالت توسعه دهنده

برای فعال کردن حالت توسعه دهنده به مسیر `Settings → Update & Security → For Developers` مراجعه کرده و حالت **Developer Mode** را انتخاب کنید.
![wsl_step_1.png](/uploads/wsl_step_1.png)

### قدم دوم: فعال کردن WSL

برای فعال کردن WSL متن `Turn Windows features on or off` را در قسمت جستجو (Cortana) جستجو کرده و برنامه را اجرا کنید. و سپس `Windows Subsystem for Linux (Beta)` را فعال نمایید.
![wsl_step_2.png](/uploads/wsl_step_2.png)

> نظر شخصی من برای جلوگیری از مشکلات wsl این هست که بعد از تیک زدن این قسمت بعد از یک دقیقه ویندوز را یک بار Restart نمایید.

### قدم سوم: نصب WSL

تا این مرحله در حال فعال سازی قابلیت WSL بودیم. در این مرحله میخواهیم WSL را از طریق اینترنت نصب نماییم. حجم نصبی WSL حدود 300 مگابایت می باشد که از Windows Store نصب خواهد شد. بدین منظور ابتدا CMD را از طریق **Run as administrator** اجرا نمایید. دقت کنید فقط با CMD امتحان کنید نه با PowerShell! بعد از اجرا تایپ نمایید `bash` سپس پیامی برای شما به نمایش در می آید که با تایپ حرف `y` لایسنس شرکت کنونیکال و قوانین آن را قبول خواهید کرد. و بعد از قبول کردن WSL شروع به دانلود و سپس نصب خواهد داد.
![wsl_step_3.png](/uploads/wsl_step_3.png)

### قدم چهارم: ایجاد کاربر

بعد از دانلود و نصب، از شما میخواهد برای UNIX خود نام کاربری و رمز عبور تعریف کنید. دقت کنید برای استفاده از دستور `sudo` نیاز به داشتن رمز عبور خواهید بود.
![wsl_step_4.png](/uploads/wsl_step_4.png)

> چون من قبلا نصب کردم عکس قدم سوم و چهارم از اینترنت برداشتم. **همچنین پیشنهاد میکنم بعد از ایجاد کاربر حتما ویندوز را Restart نمایید.**

### قدم پنجم: بروزرسانی مخزن و بسته ها

تبریک! شما هم اکنون WSL نصب کرده و میتوانید از آن استفاده نمایید. دقت نمایید قبل از هر گونه استفاده با دستور های زیر مخزن و بسته ها را به روز رسانی کنید.

``` sh
sudo apt-get update
sudo apt-get dist-upgrade
```

## لینک ها:

### صفحه های رسمی:

* [github](https://github.com/Microsoft/BashOnWindows)
* [MSDN Documentation](https://msdn.microsoft.com/en-us/commandline/wsl/about)
* [Release Notes](https://msdn.microsoft.com/en-us/commandline/wsl/release_notes)
* [User Voice](https://wpdev.uservoice.com/forums/266908-command-prompt-console-bash-on-ubuntu-on-windo/category/161892-bash)
* [WSL Blog](https://blogs.msdn.microsoft.com/wsl)
* [Console Blog](https://blogs.msdn.microsoft.com/commandline/)

### صفحه های اجتماعی

* [StackOverflow](http://stackoverflow.com/questions/tagged/wsl)
* [AskUbuntu](http://askubuntu.com/questions/tagged/wsl)
* [Reddit](https://www.reddit.com/r/bashonubuntuonwindows/)