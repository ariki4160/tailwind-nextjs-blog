---
comments: true
date: '2016-05-22T17:05:49+09:00'
summary: 'SeleniumとBeautifulsoupを使って、サイトの検索結果画面をキャプチャーして、URLのリストを自動で取得する方法'
draft: false
slug: 'selenium-beautifulsoup'
tags: ['python', 'selenium', 'beautifulsoup']
title: Google検索して検索結果画面をキャプチャー、URLのリストを自動で作成する
---

Selenium と Beautifulsoup を使って、下記の操作を自動化します。

- Firefox で Google にて「Selenium」を検索します。
- 検索結果画面をキャプチャーします。
- 検索結果の URL のリストだけをテキストで保存します。

selenium-bs4.py

```python
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from bs4 import BeautifulSoup
from time import sleep

browser = webdriver.Firefox()

browser.get('https://www.google.co.jp/')
assert 'Google' in browser.title

# Find the search box
elem = browser.find_element_by_name('q')
elem.send_keys('seleniumhq' + Keys.RETURN)

browser.set_window_size(1280, 720)
browser.save_screenshot("google.jpg")

data = browser.page_source.encode('utf-8')
html = BeautifulSoup(data, "html.parser")

with open('list.txt', mode = 'w') as fh:
	for h3tag in html.find_all("h3"):
		for link in h3tag.find_all("a"):
			fh.writelines(link.get('href')+"\n")

sleep(3)
fh.close()
browser.quit()
```

操作方法

```bash
$ python selenium-bs4.py
```

操作の様子を動画に撮りました。QuickTime Player を使って録画したのですが、音声レベルを大きくして録画する方法がよくわからないので、声が小さくなっています。

https://youtu.be/imMXHpnZo-4

[![selenium-beautifulsoup](/static/images/post/selenium-beautifulsoup.png)](https://youtu.be/imMXHpnZo-4)
