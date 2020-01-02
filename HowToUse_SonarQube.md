# How To Use SonerQube on Docker container

## はじめに
  SonarQubeのDockerコンテナの起動と、GradleプロジェクトでSonarQubeを実行するまでのメモ。

## 環境
* Windows 10 Pro Build 1903 (64bit 日本語)
* Docker Desktop Community 2.1.0.1 (Docker Desktop for Windows Stable)
* SonarQube Community Edition Version 7.9.1 (build 27448)
* Gradle 5.4.1

## 環境準備
### Docker Desktop Communityのインストール
   割愛。

### Gradleのインストール
   割愛。

### Gradleプロジェクトの設定
  build.gradleに以下を追記。
  plugins {
    id "org.sonarqube" version "2.7"
  }

## 使用手順
1. コマンドプロンプトで以下のコマンドを実行し、SonarQubeを起動。  
   `docker pull sonarqube`  
   `docker run -d --name sonarqube -p 9000:9000 sonarqube`
2. SonarQubeのダッシュボードにアクセス。  
   http://localhost:9000/
3. SonarQubeのダッシュボードにログイン。
   (初期ID/PW: admin)
4. SonarQubeのプロジェクトを作成。
   ダッシュボード右上の＋ボタンをクリック。
   Create new projectをクリック。
   * Project key(任意の値)
   * Display name(任意の値)
   * ①Provide a token(任意の値)
   * ②Run analysis on your project
     main language: Java
     build technology: Gradle
5. Gradleプロジェクトのルートディレクトリで以下のコマンドを実行し、SonarQubeを実行。
   gradlew sonarqube -Dsonar.projectKey=%SonarQubeプロジェクトのProject key% -Dsonar.host.url=http://localhost:9000 -Dsonar.login=%SonarQubeプロジェクトのToken%

   上記実行後、SonarQubeのダッシュボードに実行結果が表示されればOK。
---