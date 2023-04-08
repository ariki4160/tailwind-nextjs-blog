---
title: StreamlitをUbuntu 22.04.1 LTSの環境で構築
date: '2023-04-09T18:05:19.18'
template: 'post'
draft: false
slug: 'Streamlit-environment-building'
category: 'Web Development'
tags:
  - 'Python'
  - 'WSL2'
  - 'Ubuntu'
summary: 'StreamlitをUbuntu 22.04.1 LTSの環境で構築した記録です。python3.10-venvのインストールには、Universeのリポジトリ　Universeを使えるように設定する必要があります。'
---

Streamlit を Ubuntu 22.04.1 LTS の環境で構築した記録です。

- [Streamlit • The fastest way to build and share data apps](https://streamlit.io/)

## 環境の確認

WSL のバージョン

```bash
PS C:\Users\Owner> wsl -l -v
  NAME      STATE           VERSION
* Ubuntu    Running         2
```

Python の確認

```bash
$ python3 -V
Python 3.10.6
```

## venv の環境用意

Streamlit 用の Python の仮想環境を用意します。

```python
$ python3 -m venv streamlit-chatgpt
The virtual environment was not created successfully because ensurepip is not
available.  On Debian/Ubuntu systems, you need to install the python3-venv
package using the following command.

    apt install python3.10-venv

You may need to use sudo with that command.  After installing the python3-venv
package, recreate your virtual environment.

Failing command: ['/home/ariki/src/site/py-streamlit-chatgpt/streamlit-chatgpt/bin/python3', '-Im', 'ensurepip', '--upgrade', '--default-pip']
```

python3.10-venv 　のインストールが必要です。

```bash
$ sudo apt install python3.10-venv
[sudo] password for ariki:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package python3.10-venv is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python3.10-venv' has no installation candidate
```

## リポジトリの設定

Universe のリポジトリに、python3.10-venv があるようです。Universe（Ubuntu のリポジトリ）を使えるように設定します。

```bash
$ sudo add-apt-repository universe
Adding component(s) 'universe' to all repositories.
Press [ENTER] to continue or Ctrl-c to cancel.
Get:1 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Hit:2 http://archive.ubuntu.com/ubuntu jammy InRelease
Get:3 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]
Get:4 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages [728 kB]
Get:5 http://archive.ubuntu.com/ubuntu jammy-backports InRelease [108 kB]
Get:6 http://archive.ubuntu.com/ubuntu jammy/universe amd64 Packages [14.1 MB]
Get:7 http://security.ubuntu.com/ubuntu jammy-security/main Translation-en [147 kB]
Get:8 http://security.ubuntu.com/ubuntu jammy-security/main amd64 c-n-f Metadata [9020 B]
Get:9 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages [701 kB]
Get:10 http://security.ubuntu.com/ubuntu jammy-security/restricted Translation-en [109 kB]
Get:11 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 c-n-f Metadata [576 B]
Get:12 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 Packages [716 kB]
Get:13 http://security.ubuntu.com/ubuntu jammy-security/universe Translation-en [118 kB]
Get:14 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 c-n-f Metadata [14.2 kB]
Get:15 http://security.ubuntu.com/ubuntu jammy-security/multiverse amd64 Packages [19.4 kB]
Get:16 http://security.ubuntu.com/ubuntu jammy-security/multiverse Translation-en [4068 B]
Get:17 http://security.ubuntu.com/ubuntu jammy-security/multiverse amd64 c-n-f Metadata [228 B]
Get:18 http://archive.ubuntu.com/ubuntu jammy/universe Translation-en [5652 kB]
Get:19 http://archive.ubuntu.com/ubuntu jammy/universe amd64 c-n-f Metadata [286 kB]
Get:20 http://archive.ubuntu.com/ubuntu jammy/multiverse amd64 Packages [217 kB]
Get:21 http://archive.ubuntu.com/ubuntu jammy/multiverse Translation-en [112 kB]
Get:22 http://archive.ubuntu.com/ubuntu jammy/multiverse amd64 c-n-f Metadata [8372 B]
Get:23 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages [990 kB]
Get:24 http://archive.ubuntu.com/ubuntu jammy-updates/main Translation-en [210 kB]
Get:25 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 c-n-f Metadata [13.9 kB]
Get:26 http://archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages [744 kB]
Get:27 http://archive.ubuntu.com/ubuntu jammy-updates/restricted Translation-en [115 kB]
Get:28 http://archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 c-n-f Metadata [576 B]
Get:29 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages [899 kB]
Get:30 http://archive.ubuntu.com/ubuntu jammy-updates/universe Translation-en [180 kB]
Get:31 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 c-n-f Metadata [18.6 kB]
Get:32 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 Packages [24.1 kB]
Get:33 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse Translation-en [6312 B]
Get:34 http://archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 c-n-f Metadata [444 B]
Get:35 http://archive.ubuntu.com/ubuntu jammy-backports/main amd64 Packages [40.6 kB]
Get:36 http://archive.ubuntu.com/ubuntu jammy-backports/main Translation-en [9800 B]
Get:37 http://archive.ubuntu.com/ubuntu jammy-backports/main amd64 c-n-f Metadata [388 B]
Get:38 http://archive.ubuntu.com/ubuntu jammy-backports/restricted amd64 c-n-f Metadata [116 B]
Get:39 http://archive.ubuntu.com/ubuntu jammy-backports/universe amd64 Packages [20.3 kB]
Get:40 http://archive.ubuntu.com/ubuntu jammy-backports/universe Translation-en [14.4 kB]
Get:41 http://archive.ubuntu.com/ubuntu jammy-backports/universe amd64 c-n-f Metadata [480 B]
Get:42 http://archive.ubuntu.com/ubuntu jammy-backports/multiverse amd64 c-n-f Metadata [116 B]
Fetched 26.6 MB in 9s (2885 kB/s)
Reading package lists... Done
```

apt update を行っておきます。

```bash
$ sudo apt update
Hit:1 http://security.ubuntu.com/ubuntu jammy-security InRelease
Hit:2 http://archive.ubuntu.com/ubuntu jammy InRelease
Hit:3 http://archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:4 http://archive.ubuntu.com/ubuntu jammy-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
53 packages can be upgraded. Run 'apt list --upgradable' to see them.
Preparing to unpack .../3-python3.10-minimal_3.10.6-1~22.04.2ubuntu1_amd64.deb ...
Unpacking python3.10-minimal (3.10.6-1~22.04.2ubuntu1) over (3.10.6-1~22.04.2) ...
Preparing to unpack .../4-libpython3.10-minimal_3.10.6-1~22.04.2ubuntu1_amd64.deb ...
Unpacking libpython3.10-minimal:amd64 (3.10.6-1~22.04.2ubuntu1) over (3.10.6-1~22.04.2) ...
Selecting previously unselected package python3-lib2to3.
Preparing to unpack .../5-python3-lib2to3_3.10.6-1~22.04_all.deb ...
Unpacking python3-lib2to3 (3.10.6-1~22.04) ...
Selecting previously unselected package python3-distutils.
Preparing to unpack .../6-python3-distutils_3.10.6-1~22.04_all.deb ...
Unpacking python3-distutils (3.10.6-1~22.04) ...
Selecting previously unselected package python3-pip-whl.
Preparing to unpack .../7-python3-pip-whl_22.0.2+dfsg-1ubuntu0.2_all.deb ...
Unpacking python3-pip-whl (22.0.2+dfsg-1ubuntu0.2) ...
Selecting previously unselected package python3-setuptools-whl.
Preparing to unpack .../8-python3-setuptools-whl_59.6.0-1.2ubuntu0.22.04.1_all.deb ...
Unpacking python3-setuptools-whl (59.6.0-1.2ubuntu0.22.04.1) ...
Selecting previously unselected package python3.10-venv.
Preparing to unpack .../9-python3.10-venv_3.10.6-1~22.04.2ubuntu1_amd64.deb ...
Unpacking python3.10-venv (3.10.6-1~22.04.2ubuntu1) ...
Setting up python3-setuptools-whl (59.6.0-1.2ubuntu0.22.04.1) ...
Setting up python3-pip-whl (22.0.2+dfsg-1ubuntu0.2) ...
Setting up libpython3.10-minimal:amd64 (3.10.6-1~22.04.2ubuntu1) ...
Setting up python3-lib2to3 (3.10.6-1~22.04) ...
Setting up python3-distutils (3.10.6-1~22.04) ...
Setting up python3.10-minimal (3.10.6-1~22.04.2ubuntu1) ...
Setting up libpython3.10-stdlib:amd64 (3.10.6-1~22.04.2ubuntu1) ...
Setting up libpython3.10:amd64 (3.10.6-1~22.04.2ubuntu1) ...
Setting up python3.10 (3.10.6-1~22.04.2ubuntu1) ...
Setting up python3.10-venv (3.10.6-1~22.04.2ubuntu1) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
/sbin/ldconfig.real: /usr/lib/wsl/lib/libcuda.so.1 is not a symbolic link
```

## 再度 venv の環境用意

Python の仮想環境が作成できるようになりました。Streamlit 用の仮想環境を作成します。

```bash
$ python3 -m venv streamlit-chatgpt
```

仮想環境をアクティブにします。Streamlit 用の Python の仮想環境に入ります。

```bash
$ source streamlit-chatgpt/bin/activate
(streamlit-chatgpt) $
```

仮想環境に入れました。
