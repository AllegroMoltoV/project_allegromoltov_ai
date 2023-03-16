# project_allegromoltov_ai
あれぐろもると楽曲風の短いクリップを自動生成するプロジェクト

## 使い方 ( Windows 編 )

1. WSL2 をインストールします。 (参考: https://chigusa-web.com/blog/wsl2-win11/ )
1. Git for Windows をインストールします。 ( https://gitforwindows.org/ )
1. Git の初期設定をします。 (詳しくは https://qiita.com/hollyhock0518/items/a3fee20951cd92c87ed9 等のページが参考になります)
1. 本リポジトリ (project_allegromoltov_ai) をクローンします。今回は D ドライブ直下にクローンする想定で説明します。Git Bash を開いて、次のようにコマンドを入力します。 

      ```
      $ cd /d
      $ git clone git@github.com:AllegroMoltoV/project_allegromoltov_ai.git
      ```
  
1. Docker Desktop をインストールします。 (https://www.docker.com/products/docker-desktop/)
1. Windows Powershell を管理者権限で実行します。 Windows ボタンを右クリックすると簡単です。

      ![powershell](https://user-images.githubusercontent.com/77569633/220794460-fb77715e-2f6f-4920-86fe-672723ce9ff9.png)

1. Windows Powershell で docker コマンドを入力し、docker がインストールされていることを確認します。

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

1. Windows Powershell で次のコマンドを入力し、 TensorFlow 公式の Docker イメージを使って Jupyter Notebook を起動します。 

      ```
      > docker run -it -p 8888:8888 -v D:/project_allegromoltov_ai:/tf tensorflow/tensorflow:latest-jupyter
      ```
      cudaの設定に自信がある方は、tensorflow/tensorflow:latest-jupyter の代わりに tensorflow/tensorflow:latest-gpu-jupyter イメージを引っ張ってきてもいいと思います。
1. Windows Powershell に表示された URL に接続します。 http://127.0.0.1:8888/?token=xxxxxxxxxxxxxxxxxxxxxx といったものです。このアドレスをコピーして、ブラウザの URL 欄に貼り付けて接続します。
1. Home に data というフォルダーを作成し、その中に models, arrays, out, wav44100 というフォルダーを作成します。(今は手動でフォルダーを作る必要がありますが、そのうち自動で作成するようにしようと思います。)

      ![image](https://user-images.githubusercontent.com/77569633/220796386-99439722-efd2-4673-ae88-98e9d7c53db2.png)
      
1. エクスプローラーで D ドライブを開くと、 project_allegromoltov_ai/data/arrays フォルダーができているので、その中に必要なデータをダウンロードしてきましょう。次のリンク先の arrays フォルダー内にある clips.npy をローカルの arrays フォルダ－内にコピーします。 https://1drv.ms/u/s!AnNGKzbxk33_5i_jtm0-o5HaVgI9?e=7Si7nE
1. 手持ちの wav ファイルで試してみたい場合は、 clips.npy を削除し、 wav44100 フォルダーに サンプリングレートが 44100Hz の .wav ファイルを格納します。(今はこの形式のファイルにのみ対応しています。)
1. /src/independent.ipynb を開き、上から順に実行していきます。SHIFT+ENTERで実行できます。
1. /data/out に out_xxxxxx_0.wav, ~ out_xxxxxx_9.wav が出力されます。チェックボックスにチェックを入れ Download ボタンを押してダウンロードしてもよいですが、 ローカルの project_allegromolto_am フォルダーの、 out フォルダーの中にあるので、それを直接再生すれば OK です。

## システムの説明

![allegromoltov_ai drawio](https://user-images.githubusercontent.com/77569633/220806371-b967c477-90f8-40b5-9d50-4f3fc8f723e0.png)

## お願い

本システムで得られた出力を有料で販売する行為は固くお断りいたします。もし、何かしらの用途に使用したいということでしたら、あれぐろもるとにご相談ください。 あれぐろもるとTwitter: https://twitter.com/AllegroMoltoV
