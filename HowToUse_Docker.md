# How To Use "Docker Desktop Community"

## はじめに
  Docker Desktop Communityを導入して、Webで公開されているDockerコンテナを起動するまでのメモ。

## 環境
* Windows 10 Pro Build 1903 (64bit 日本語)  
  Hyper-V有効化済み。
* Docker Desktop Community 2.1.0.1 (Docker Desktop for Windows Stable)

## 環境準備
## Docker Desktop Community のインストール
1. Docker公式サイトのダウンロードページからインストーラをダウンロード。
   https://www.docker.com/
2. インストーラを起動し、インストールを実行。
3. インストール後にDocker Desktopの設定を行う。
   Docker Desktopを起動(タスクトレイ中の鯨マークを右クリック)し、[Settings]をクリック。
   * DNSサーバの設定。
     コンテナへアクセスするために必要な設定。自環境のDNSサーバを指定。
     1. [Settings]の[Network]を選択。
     2. [DNS Server]の[Fixed]を選択。
     3. [Fixed]の値に自環境のDNSサーバのアドレスを入力。  
       (ipconfigコマンドの実行結果のうち、[デフォルトゲートウェイ]に記載されている値。例. 192.168.179.1)

   * 共有ドライブの設定。
     コンテナからPCのドライブを参照するための設定。コンテナと共有するドライブを指定。  
     1. [Settings]の[Shared Drives]を選択。  
     2. 共有するドライブを選択。

  3. リソースの設定。
    Dockerエンジンが使用するリソースの設定。PCのスペックに合わせて変更。  
    今回はディスクイメージの格納場所のみを変更。  
     1. [Settings]の[Advanced]を選択。  
     2. [Disk image location]の[browse]ボタンをクリックし、ディスクイメージの格納場所を選択。

## 使用手順
* Webで公開されているDockerコンテナをダウンロード、起動。  
  例. SonarQubeのコンテナを使用する場合。  
    コマンドプロンプトで以下のコマンドを実行。  
    docker pull sonarqube  
    docker run -d --name sonarqube -p 9000:9000 sonarqube  
    上記実行後、http://localhost:9000/ にアクセスし、SonarQubeのダッシュボードが出力されていればOK。
---