---
title: BRA (Beautiful Realistic Asians) での学生モデルのプロンプト検証
date: '2023-04-24T02:05:19.18'
template: 'post'
draft: false
slug: 'bra-'
category: 'Web Development'
tags:
  - 'Ai-Image-Generator'
  - 'Stable Diffusion'
summary: 'BRA (Beautiful Realistic Asians) Stable Diffusionを使って、女子学生モデル画像のプロンプトの検証をしました。'
---

## 環境構築

BRA (Beautiful Realistic Asians) のインストールは、下記のサイトを参照させていただきました。

- [【AI グラビア】ChilloutMix の次は BRA が来るかも | ジコログ](https://self-development.info/%e3%80%90ai%e3%82%b0%e3%83%a9%e3%83%93%e3%82%a2%e3%80%91chilloutmix%e3%81%ae%e6%ac%a1%e3%81%afbra%e3%81%8c%e6%9d%a5%e3%82%8b%e3%81%8b%e3%82%82/)
- [組み立てた GPU 搭載 Linux マシンで機械学習の環境構築を行ってみました - きょうのかんぱぱ](https://kanpapa.com/today/2023/01/linux-gpu-pc-cuda12-pytorch.html)
- [【Stable Diffusion】 実写・リアル系の画像を生成するモデル | ぺんぎんや](https://e-penguiner.com/stable-diffusion-realistic-model/)

## 起動確認

起動コマンド

```bash
> python launch.py
Python 3.10.11 (tags/v3.10.11:7d4cc5a, Apr  5 2023, 00:38:17) [MSC v.1929 64 bit (AMD64)]
Commit hash: 22bcc7be428c94e9408f589966c2040187245d81
Installing requirements for Web UI
Launching Web UI with arguments:
No module 'xformers'. Proceeding without it.
C:\Users\Owner\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.10_qbz5n2kfra8p0\LocalCache\local-packages\Python310\site-packages\torchvision\transforms\functional_tensor.py:5: UserWarning: The torchvision.transforms.functional_tensor module is deprecated in 0.15 and will be **removed in 0.17**. Please don't rely on it. You probably just need to use APIs in torchvision.transforms.functional or in torchvision.transforms.v2.functional.
  warnings.warn(
Loading weights [6c646be990] from C:\Users\Owner\Documents\tech_work\stable-diffusion-webui\models\Stable-diffusion\braBeautifulRealistic_brav3.safetensors
Creating model from config: C:\Users\Owner\Documents\tech_work\stable-diffusion-webui\configs\v1-inference.yaml
LatentDiffusion: Running in eps-prediction mode
DiffusionWrapper has 859.52 M params.
Applying cross attention optimization (Doggettx).
Textual inversion embeddings loaded(0):
Model loaded in 9.5s (load weights from disk: 0.3s, create model: 0.5s, apply weights to model: 3.7s, apply half(): 1.8s, move model to device: 0.9s, load textual inversion embeddings: 2.2s).
Running on local URL:  http://127.0.0.1:7860

To create a public link, set `share=True` in `launch()`.
Startup time: 21.6s (import torch: 3.8s, import gradio: 3.0s, import ldm: 1.1s, other imports: 2.2s, setup codeformer: 0.1s, load scripts: 0.8s, load SD checkpoint: 9.7s, create ui: 0.7s, gradio launch: 0.1s).
```

ブラウザでの確認

http://127.0.0.1:7860/

## 女性画像生成のプロンプト

アジア人画像の生成にカスタマイズされているので、「a beautiful lady」のプロンプトで、アジア人っぽい画像が生成されます。

![a_beautiful_lady_prompt.png](/static/images/post/bra/a_beautiful_lady_prompt.png)

![a_beautiful_lady.png](/static/images/post/bra/a_beautiful_lady.png)

## 二人の女子学生画像を生成するプロンプト

二人の女子学生を生成するプロンプトのパラメータの変更によって、どのような変化が起きるかを検証しました。学生を生成するキーワードパラメータとして、university、college、institute、school での違いをみてみます。

「two girl, chatting, university」のプロンプト、「university」を付けると、一般的な女子学生のイメージを生成します。

![two_girl_chatting_university.png](/static/images/post/bra/two_girl_chatting_university.png)

「two girl, chatting, college」のプロンプト、「college」を付けると、帽子をかぶりがちです。

![two_girl_chatting_college.png](/static/images/post/bra/two_girl_chatting_college.png)

「two girl, chatting, institute」のプロンプト、「institute」を付けると、落ち着いた年齢も高めの印象になります。

![two_girl_chatting_institute.png](/static/images/post/bra/two_girl_chatting_institute.png)

「two girl, chatting, school」のプロンプト、「school」を付けると、女子高生のイメージになります。

![two_girl_chatting_school.png](/static/images/post/bra/two_girl_chatting_school.png)

## 二人の女子学生が笑う画像を生成するプロンプト

二人の女子高生を生成するプロンプトで、笑いのキーワードパラメータ違いを検証しました。笑いのキーワードパラメータとして、laughing、smiling、LOL. での違いをみてみます。

「two girl, laughing, school」のプロンプト、「laughing」を付けると、爆笑の笑いになります。

![two_girl_laughing_school.png](/static/images/post/bra/two_girl_laughing_school.png)

「two girl, smiling, school」のプロンプト、「smiling」を付けると、歯を見せ笑う感じになります。

![two_girl_smiling_school.png](/static/images/post/bra/two_girl_smiling_school.png)

「two girl, LOL., school」のプロンプト、「LOL.」を付けると、微笑む感じになりました。

![two_girl_LOL_school.png](/static/images/post/bra/two_girl_LOL_school.png)
