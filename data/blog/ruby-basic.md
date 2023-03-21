---
comments: true
date: '2016-05-29T08:12:38+09:00'
summary: '「Rubyプログラミング入門 — はじめてのプログラミング、はじめてのRuby」を読んで、Rubyの基本的な項目を忘れないように備忘録'
draft: false
slug: 'ruby-basic'
tags: ['ruby']
title: Rubyの基本的な項目の備忘録
---

Ruby の基本的なことが、よくわかっていない点があったので、図書館で[「Ruby プログラミング入門 —はじめてのプログラミング、はじめての Ruby」](https://amzn.to/3lrVjCP)を借りて読んでみました。重要な点を忘れないように記録しておきます。

puts メソッド　引数として指定したオブジェクトを改行付きで表示

```ruby
$ irb
irb(main):001:0> puts "Hello World","Welcome to Ruby"
Hello World
Welcome to Ruby
=> nil
```

p メソッド　引数として指定したオブジェクトを読みやすい形式で表示

```ruby
irb(main):002:0> p "Hello World","Welcome to Ruby"
"Hello World"
"Welcome to Ruby"
=> ["Hello World", "Welcome to Ruby"]
```

superclass メソッド　オブジェクトがどのスーパークラスに属しているかを調べる

```ruby
irb(main):003:0> 2016.class
=> Fixnum
irb(main):004:0> 2016.class.superclass
=> Integer
irb(main):005:0> 2016.class.superclass.superclass
=> Numeric
irb(main):006:0> 2016.class.superclass.superclass.superclass
=> Object
irb(main):007:0> 2016.class.superclass.superclass.superclass.superclass
=> BasicObject
irb(main):008:0> 2016.class.superclass.superclass.superclass.superclass.superclass
=> nil
irb(main):009:0>
```

メソッドの種類

- インスタンスメソッド
- 関数的メソッド
- クラスメソッド

インスタンスメソッド　操作対象となるオブジェクト.メソッド（引数）

```ruby
irb(main):003:0> 2016.class
=> Fixnum
```

関数的メソッド　メソッド（引数）

```ruby
irb(main):001:0> puts "Hello World","Welcome to Ruby"
Hello World
Welcome to Ruby
=> nil
```

クラスメソッド　クラス.メソッド（引数）

```ruby
irb(main):010:0> Time.now
=> 2016-05-29 08:38:04 +0900
```

ローカル変数とグローバル変数

```ruby
$ irb
irb(main):001:0> character = "ruby"
=> "ruby"
irb(main):002:0> $character = "python"
=> "python"
irb(main):003:0> irb
irb#1(main):001:0> p character
NameError: undefined local variable or method `character' for main:Object
from (irb#1):3
irb#1(main):002:0> p $character
"python"
=> "python"
irb#1(main):003:0> $character = "java"
=> "java"
irb#1(main):004:0> character = "perl"
=> "perl"
irb#1(main):005:0> fg 0
=> #<IRB::Irb: @context=#<IRB::Context:0x007feee28ec528>, @signal_status=:IN_EVAL, @scanner=#<RubyLex:0x007feee30f19a8>>
irb(main):004:0> p character
"ruby"
=> "ruby"
irb(main):005:0> p $character
"java"
=> "java"
irb(main):006:0>
```
