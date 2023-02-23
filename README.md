# project_allegromoltov_ai
あれぐろもると楽曲風の短いクリップを自動生成するプロジェクト

## 使い方( Windows 編)

1. Git for Windows をインストールします。 ( https://gitforwindows.org/ )
1. Git の初期設定をします。 (詳しくは https://qiita.com/hollyhock0518/items/a3fee20951cd92c87ed9 等のページが参考になります)
1. 本リポジトリ (project_allegromoltov_ai) をクローンします。今回は D ドライブ直下にクローンする想定で説明します。Git Bash を開いて、次のようにコマンドを入力します。 <br>
```
$ cd /d
$ git clone git@github.com:AllegroMoltoV/project_allegromoltov_ai.git
```
1. Docker Desktop をインストールします。 (https://www.docker.com/products/docker-desktop/)
1. Windows Powershell を管理者権限で実行します。 Windows ボタンを右クリックすると簡単です。<br>
![powershell](https://user-images.githubusercontent.com/77569633/220794460-fb77715e-2f6f-4920-86fe-672723ce9ff9.png)
1. Windows Powershell で docker コマンドを入力し、docker がインストールされていることを確認します。<br>
```
PS C:\WINDOWS\system32> docker

Usage:  docker [OPTIONS] COMMAND

A self-sufficient runtime for containers

Options:
      --config string      Location of client config files (default
                           "C:\\Users\\scher\\.docker")
  -c, --context string     Name of the context to use to connect to the
                           daemon (overrides DOCKER_HOST env var and
                           default context set with "docker context use")
  -D, --debug              Enable debug mode
  -H, --host list          Daemon socket(s) to connect to
  -l, --log-level string   Set the logging level
                           ("debug"|"info"|"warn"|"error"|"fatal")
                           (default "info")
      --tls                Use TLS; implied by --tlsverify
      --tlscacert string   Trust certs signed only by this CA (default
                           "C:\\Users\\scher\\.docker\\ca.pem")
      --tlscert string     Path to TLS certificate file (default
                           "C:\\Users\\scher\\.docker\\cert.pem")
      --tlskey string      Path to TLS key file (default
                           "C:\\Users\\scher\\.docker\\key.pem")
      --tlsverify          Use TLS and verify the remote
  -v, --version            Print version information and quit
```
1. Windows Powershell で次のコマンドを入力し、 TensorFlow 公式の Docker イメージを使って Jupyter Notebook を起動します。 <br>
```
> docker run -it -p 8888:8888 -v D:/project_allegromoltov_ai:/tf tensorflow/tensorflow:latest-jupyter
```
1. Windows Powershell に表示された URL に接続します。 http://127.0.0.1:8888/?token=xxxxxxxxxxxxxxxxxxxxxx といったものです。このアドレスをコピーして、ブラウザの URL 欄に貼り付けて接続します。
1. Home フォルダーに data というフォルダーを作成し、その中に models, arrays, out, wav44100 というフォルダーを作成します。(今は手動でフォルダーを作る必要がありますが、そのうち自動で作成するようにしようと思います。)<br>
![image](https://user-images.githubusercontent.com/77569633/220796386-99439722-efd2-4673-ae88-98e9d7c53db2.png)
1. wav44100 フォルダーに サンプリングレートが 44100Hz の、 16bit WAV ファイルを格納します。(今はこの形式のファイルにのみ対応しています。)
1. /src/FFT.ipynb を開き、上から順に実行していきます。
1. /data/out に fft_out_1.wav, fft_out_2.wav, fft_out_3.wav が出力されます。チェックボックスにチェックを入れ Download ボタンを押してダウンロードしてもよいですが、 クローンした project-allegromolto-am フォルダーにある out フォルダーの中にあるのでそれを直接再生すれば OK です。
