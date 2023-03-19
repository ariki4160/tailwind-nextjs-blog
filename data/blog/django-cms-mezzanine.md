---
title: DjangoベースのCMS「Mzzanine」のインストールと検証
date: 2018-11-21T17:33:47+09:00
draft: false
tags: ['python', 'django', 'mezzanine']
summary: 'DjangoベースのCMS「Mzzanine」をWindows10のconda環境にインストールと検証をする'
slug: 'django-cms-mezzanine'
comments: true
---

## Windows10 の conda 環境で python3.6 の仮想環境を作成

```bash
> conda create -n mezzanine-env python=3.6
> activate mezzanine-env
```

Mac、Linux の場合は

```bash
> source activate mezzanine-env
```

## 仮想環境内で、Mzzanine のインストール

```bash
(mezzanine-env) C:\some_folder > pip install mezzanine
(mezzanine-env) C:\some_folder > cd mezzanine
(mezzanine-env) C:\some_folder\mezzanine > mezzanine-project myproject
(mezzanine-env) C:\some_folder\mezzanine > cd myproject
(mezzanine-env) C:\some_folder\mezzanine\myproject > python manage.py createdb
A site record is required.
Please enter the domain and optional port in the format 'domain:port'.
For example 'localhost:8000' or 'www.example.com'.
Hit enter to use the default (127.0.0.1:8000):

Creating default site record: 127.0.0.1:8000 ...
Creating default account ...

Username (leave blank to use 'ariki'):
Email address:
Password:
Password (again):
Superuser created successfully.
Installed 2 object(s) from 1 fixture(s)

Would you like to install some initial demo pages?
Eg: About us, Contact form, Gallery. (yes/no): y
Please enter either 'yes' or 'no': yes

Creating demo pages: About us, Contact form, Gallery ...

Installed 16 object(s) from 3 fixture(s)

(mezzanine) C:\some_folder\mezzanine\myproject>python manage.py runserver
                .....
            _d^^^^^^^^^b_
         .d''           ``b.
       .p'                `q.
      .d'                   `b.
     .d'                     `b.   * Mezzanine 4.3.1
     ::                       ::   * Django 1.11.16
    ::    M E Z Z A N I N E    ::  * Python 3.6.7
     ::                       ::   * SQLite 3.21.0
     `p.                     .q'   * Windows 10
      `p.                   .q'
       `b.                 .d'
         `q..          ..p'
            ^q........p^
                ''''

Performing system checks...

System check identified no issues (0 silenced).
November 21, 2018 - 08:06:45
Django version 1.11.16, using settings 'myproject.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
```

## 管理画面へアクセス

http://127.0.0.1:8000/admin/

settings.py の編集　日本語化、タイムゾーンの設定を日本に

```bash
# Local time zone for this installation. Choices can be found here:
# http://en.wikipedia.org/wiki/List_of_tz_zones_by_name
# although not all choices may be available on all operating systems.
# On Unix systems, a value of None will cause Django to use the same
# timezone as the operating system.
# If running in a Windows environment this must be set to the same as your
# system time zone.
# TIME_ZONE: 'UTC'
TIME_ZONE: 'Asia/Tokyo'

# If you set this to True, Django will use timezone-aware datetimes.
USE_TZ: True

# Language code for this installation. All choices can be found here:
# http://www.i18nguy.com/unicode/language-identifiers.html
# LANGUAGE_CODE: "en"
LANGUAGE_CODE: "ja"

# Supported languages
LANGUAGES: (
    ('ja', _('Japanese')),
)
```

## mezzanine-themes のインストール

https://github.com/thecodinghouse/mezzanine-themes
