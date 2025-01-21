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
8. delete stable-diffusion-webui\modules\__pycache__\processing.cpython-310.pyc
9. restart stable-diffusion-webui

----
日本語で
sdwebuiでtxt2imgなどで画像を作成する際に、LoRA/Lycorisなどが適用されたテンソルをチェックポイントとして保存するための修正したスクリプト（一時的に置き換えるもの）。

使い方
1. stable-diffusion-webui\modules\processing.pyをprocessing.py.bkなどに名称を変更する
2. このリポジトリのprocessing.pyをstable-diffusion-webui\modules\に置く
3. stable-diffusion-webuiを実行する
4. txt2imgでlora/lycorisなどを使ったプロンプトを書く(あるいは事前に作っておいた、いいなと思うプロンプトを張り付ける)
5. 画像を生成する(sampling stepsは1でOK)
6. stable-diffusion-webui\test_model.safetensorsというファイルが出来上がるので、stable-diffusion-webui\models\checkpoints配下などに置く
7. 1でバックアップを取っておいたprocessing.pyに置き換え直す
8. stable-diffusion-webui\modules\__pycache__\processing.cpython-310.pycを削除する
9. stable-diffusion-webuiを再起動する


保存部分についてはsupermergerのコード(savemodel部分)を参考にしました。
