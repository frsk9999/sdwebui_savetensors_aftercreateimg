# sdwebui_savetensors_aftercreateimg
Modification script to save tensors with LoRA/Lycoris etc. applied as checkpoints when creating images with txt2img etc. in sdwebui (to temporarily replace them).

How to use
1. rename stable-diffusion-webui\modules\processing.py to processing.py.bk etc.
2. put processing.py from this repository in stable-diffusion-webui\modules
3. Run stable-diffusion-webui
4. write a prompt using lora/lycoris etc. in txt2img (or paste a nice prompt you made beforehand)
5. generate an image (sampling steps is 1)
6. create a file named stable-diffusion-webui\test_model.safetensors and put it under stable-diffusion-webui\models\checkpoints etc.
7. replace the processing.py file with the one you backed up in step 1
8. delete stable-diffusion-webui\modules\\_\_pycache\_\_\processing.cpython-310.pyc
9. restart stable-diffusion-webui

----
Reason for making this

It's a pretty rough job, but when I adapted what was created as lycoris with decimal points as lora (I applied multiple times), I got something pretty good, so I tried using supermerger to fix it as checkpoint, but I couldn't reproduce it ...
I tried to fix it as a checkpoint using supermerger, but I couldn't reproduce it... Then, I thought that if I save the tensor that was created when the image was created before and after the image was created, I could create the same checkpoint. I tried this and found a working file, so I published it.
Well, I don't know if anyone will use it.

The resulting file is a bit broken, but it will be okay if you merge it with other normal models...maybe.

----
日本語で

sdwebuiでtxt2imgなどで画像を作成する際に、LoRA/Lycorisなどが適用されたテンソルをチェックポイントとして保存するために修正をしたスクリプト（一時的に置き換えるもの）。

使い方
1. stable-diffusion-webui\modules\processing.pyをprocessing.py.bkなどに名称を変更する
2. このリポジトリのprocessing.pyをstable-diffusion-webui\modules\に置く
3. stable-diffusion-webuiを実行する
4. txt2imgでlora/lycorisなどを使ったプロンプトを書く(あるいは事前に作っておいた、いいなと思うプロンプトを張り付ける)
5. 画像を生成する(sampling stepsは1でOK)
6. stable-diffusion-webui\test_model.safetensorsというファイルが出来上がるので、stable-diffusion-webui\models\checkpoints配下などに置く
7. 1でバックアップを取っておいたprocessing.pyに置き換え直す
8. stable-diffusion-webui\modules\\_\_pycache\_\_\processing.cpython-310.pycを削除する
9. stable-diffusion-webuiを再起動する


保存部分についてはsupermergerのコード(savemodel部分)を参考にしました。

----
作った理由

かなりの荒業ですが、lycorisとして作られたものをloraとして小数点以下で適応させたときに(複数適用したところ)結構よいものができていたのでcheckpointとして固定化させようとしてsupermerger使ってみたものの再現できず…
それなら画像を作るときに作り上げられたテンソルを画像生成前後で保存すればそのままのcheckpointができるんじゃないか？という仮定をして試してみたところ一応は動くファイルができたので公開してみました。
まぁ使う人はいないかもだけど。

出来上がったファイルは少し壊れているけど他の正常なモデルとマージすれば大丈夫だから…多分。
