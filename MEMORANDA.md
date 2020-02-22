# memoranda

## tensorflowの環境作りについて

基本的に以下の手順で作ってれば問題ないはず。

```
$ pyenv install miniconda3-latest
$ cd <working dir>
$ pyenv local miniconda3-latest
$ conda create -n <name> python=3.7 anaconda
$ pip install tensorflow
$ pip install keras
etc...
```

ところがmagentaの環境を作ろうとするとちょっと一癖あるので注意。

```
$ pyenv install miniconda3-latest
$ cd <working dir>
$ pyenv local miniconda3-latest
$ conda create -n <name> python=3.7 anaconda
```
ここまでは同じなのだが、、、

```
$ pip install tensorflow-gpu==1.15.2
$ pip install magenta
```

とインストールしないとGPUが有効なtensorflowが入らない。いきなり`pip install magenta`をやるとcpu版のtensorflowの1.15.2が入ってしまう。

あとcondaで環境を作るときには必ずpythonのバージョンを指定すること。conda毎にpythonを入れてpipを入れないと`pip install <hoge>`はシステムのpipを入れてしまうので。不安だったら`pip -V`で確認するとパスが違うこともわかるし、`pip list`で確認すると別の環境担っていることがわかる（上の例で入れば、上のtensorflowは2.0系、下は1.15系が入ってるはず）。

というかmagentaがそろそろ2.0系に対応してほしい、、、
