# snn-voice-recognition

```shell
pip install -r requirements.txt  -f https://download.pytorch.org/whl/torch_stable.html
jupyter lab --ip=0.0.0.0 --allow-root --NotebookApp.token='' --NotebookApp.password=''
```

# vpcc

```shell
ssh __vpcc
qsub -I -q GPU-S
module load singularity
singularity exec --nv tensorflow-notebook.sif /bin/bash
jupyter lab
```

bash コマンドを使いたい場合、以下コマンドをセルで実行する。
terminal は!ls は何故かエラーになる

```shell
%%bash
ls
```

## kaldi のインストール

1. `ln -fs /usr/bin/python2.7`を kaldi/tools/extras/env.sh に追記
2. `kaldi/tools/`にて必要なものをビルド

   ```shell
   # 使える論理CPUコアの数を確認
   fgrep 'processor' /proc/cpuinfo | wc -l
   # 12コア使ってmake それでも結構時間かかる
   make -j 12
   ```

3. `kaldi/src/`にて必要なものをビルド

   ```shell
   ./configure --shared
   make depend -j 12
   ```
