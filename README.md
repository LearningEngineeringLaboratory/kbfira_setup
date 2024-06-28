# docker環境構築
1. docker公式よりPCにdockerをダウンロードして下さい  
(Windowsの場合は[Dockerのインストール方法(Windows).md](/Dockerのインストール方法(Windows).md)を参照して下さい)
1. 自分でデスクトップなどにフォルダを1つ作成してください, 名前に指定はありません  
次にVScodeを開き，その作成したフォルダをターミナルに移動して開いてください
1. このリポジトリを以下のコマンドを実行してダウンロードしてください
    ```
    git clone --recursive https://github.com/LearningEngineeringLaboratory/kbfira_setup.git
    ```
1. 続けて以下のコマンドを実行してdockerを立ち上げてください. 以下のコマンドを実行し,kbfira_setup-mainに移動・Dockerを立ち上げて下さい  
    ```  
    cd kbfira_setup
    ```
    ```
    docker-compose up -d
    ```
1. 以下のコマンドより,nginxとmysqlのコンテナが作成されたか確認して下さい
    ```
    docker ps
    ```
    以下のように表示されればOK
    | CONTAINER ID | IMAGE | COMMAND |CREATED|STATUS|PORTS|NAMES|
    |:-------|:--------|:-------|:-------|:--------|:-------|:-------:|
    |...      |kbfira_setup-main-nginx        |"/sbin/my_init"       |...|...|0.0.0.0:8081->80/tcp |nginx-container|
    |...     |mysql:latest         |"docker-entrypoint.s…"      |...|...|33060/tcp, 0.0.0.0:3308->3306/tcp|mysql-container|

1. ブラウザで以下のURLにアクセスして下さい
    http://localhost:8081/kbfira_docs/index.php/admin/m/x/app/setup
    ![URL:初期画面](img/URL_initial.png)
1. データベースの初期化を行うために,Select databese configuration:のプルダウンからkbv2-firaを選択して下さい
1. 続いて下に移動して,Begin Database Setupボタンを押して下さい※ボタンを押すと確認画面が出ますが,Yesを選択して下さい
    ![URL:setup](img/URL_setup.png)
1. 続いてその下にあるSet Initial Dataボタンを押して下さい
1. 動作確認をするために,右上の人アイコンをクリックしてSign inボタンを押し,Usernameの欄に"admin"を入力し(パスワード欄は不要),サインインを行なって下さい
1. 右上に Sign is successfulと表示されログインできれば,環境構築完了です
<br>

# ソースコードの場所  
ソースコードはこちらのフォルダ内にあります  
`kbfira_setup/nginx/kbfira_docs`

# dockerコマンド一覧
```
docker images #イメージ確認
docker ps (-al) #コンテナ確認(-alをつけると停止中のコンテナも表示)
docker-compose up -d #ymlファイルを用いたコンテナ作成
docker run -it (コンテナ名:ID) /bin/bash #コンテナ起動
docker exec -it (コンテナ名:ID) /bin/bash #コンテナへアクセス
docker stop ID #コンテナ停止
docker rm ID #コンテナ削除
docker logs ID #エラー時などのログ確認
docker-compose logs (コンテナ名) #docker-composeでのログ出力,コンテナ名を指定するとその箇所のみのログを出力
```
# LiveServer実装
1. VSCodeにLive Serverの拡張機能をインストール
    1. 左のナビの「拡張機能」をクリック（下図）
       
       ![image](https://github.com/LearningEngineeringLaboratory/kbfira_setup/assets/134689144/a51338a1-95bf-40fc-bbc7-b89282e2e25c)
       
    1. 「LiveServer」と検索し，インストール（インストールしたら勝手に有効になる）
       
       ![image](https://github.com/LearningEngineeringLaboratory/kbfira_setup/assets/134689144/3aebe5ae-acf4-4d42-9a43-db948241b0e3)
       
1. Google ChromeにLive Server Web Extensionをインストールし、初期設定
    1. [こちらのURL](https://chromewebstore.google.com/detail/live-server-web-extension/fiegdmejfepffgpnejdinekhfieaogmj?hl=ja&pli=1) からChromeの拡張機能「Live Server Web Extension」をインストール
    1. Chrome右上の拡張機能のアイコン（下記）→インストールした「Live Server Web Extension」（下記）の順にクリック

        ![image](https://github.com/LearningEngineeringLaboratory/kbfira_setup/assets/134689144/257ac351-0b75-4a6b-a42b-9ba17205f7ad)
    
        ![image](https://github.com/LearningEngineeringLaboratory/kbfira_setup/assets/134689144/b1ab5bb3-e1bf-4f2c-baa8-d450fc0c0e1d)
    
        - 「Actual Server Address」にローカルでのアドレス「 http://localhost:8081/ 」を入力
    
        - 「Live Server Address」にLive Serverのローカルでのアドレス「 http://127.0.0.1:5500/ 」を入力
    
        - 「Apply」をクリック。上にある「Live Reload」をオンにする。最終的に下図のようになる。
    
            <img src="https://github.com/LearningEngineeringLaboratory/kbfira_setup/assets/134689144/2ad6e82e-ac8d-479e-a9c6-348e97cd438f" width=200>


1. VSCodeのLive Serverの立ち上げ
     1. 下のバーにある「Go Live」をクリック。「Port:5500」に表示が変わったらOK！

        ![image](https://github.com/LearningEngineeringLaboratory/kbfira_setup/assets/134689144/bec4e2af-6247-4975-b2b4-0ebb706a101f)
        
        ![image](https://github.com/LearningEngineeringLaboratory/kbfira_setup/assets/134689144/195865fb-ba71-4e92-9dc7-f659395e813e)
    
        なお，以下のような画面がブラウザで自動的に開く場合があるが無視して良い．閉じても良い
    
        ![image](https://github.com/LearningEngineeringLaboratory/kbfira_setup/assets/134689144/d78b961b-0e08-4f38-ab39-892ee89b5639)

1. 動作確認
    1. 動作確認として、chromeで http://localhost:8081/kbfira_docs/index.php/ （下図の画面が出てくるはず）を見ながらファイルを編集してみる
       - VS Code上で `kbfira_setup/nginx/kbfira_docs/home/view/home.php`を編集すればよい.
       - dockerが動いていないとそもそもlocalhostが立ち上がらないので注意.
    3. VS Codeでコードを編集して保存した後,Chromeで表示しているページが自動的にリロードされ，変更が反映されていれば成功！！！！
       - 変更前

            ![image](https://github.com/LearningEngineeringLaboratory/kbfira_setup/assets/134689144/a890925b-5af9-47fc-912e-538c40cb879c)
        
        - 下のように変更すると...
        
            ![image](https://github.com/LearningEngineeringLaboratory/kbfira_setup/assets/134689144/0e7c124d-323f-4c56-ad41-c68e23066d05)
        
        - 自動的にブラウザの画面が変化！！KIt-Build Concept Map!!!!
        
            ![image](https://github.com/LearningEngineeringLaboratory/kbfira_setup/assets/134689144/902f4050-c2ea-449c-83ec-0f905b818928)

# 毎回の立ち上げ

1. Docker Desktopアプリを立ち上げ
1. VS Codeでリポジトリ（一番上のフォルダ）に移動する   
    -  確認方法
       ```
       ls
       ```
        上のコマンドを打って、以下の内容が出たらOK!
       ```
       Dockerのインストール方法(Windows).md
       img
       README.md
       mysql
       docker-compose.yml
       nginx
       ```
1. VS Codeのターミナルで以下のコマンドを打ってdockerを立ち上げ
   ```
   docker-compose up -d
   ```
   - 確認方法
     ```
     docker ps
     ```
     上のコマンドを打って、以下の内容が出たらOK!
       ```
       CONTAINER ID   IMAGE                COMMAND                   CREATED      STATUS         PORTS                               NAMES
       9b64142543ee   mysql:8.0.36         "docker-entrypoint.s…"   6 days ago   Up 6 seconds   33060/tcp, 0.0.0.0:3308->3306/tcp   mysql-container
       e135ba61d170   kbfira_setup-nginx   "/sbin/my_init"           6 days ago   Up 6 seconds   0.0.0.0:8081->80/tcp                nginx-container
       ```
1. VS CodeでLive Serverを立ち上げ

   1. 下のバーにある「Go Live」をクリック。「Port:5500」に表示が変わったらOK！

        ![image](https://github.com/LearningEngineeringLaboratory/kbfira_setup/assets/134689144/bec4e2af-6247-4975-b2b4-0ebb706a101f)
        
        ![image](https://github.com/LearningEngineeringLaboratory/kbfira_setup/assets/134689144/195865fb-ba71-4e92-9dc7-f659395e813e)

1.  http://localhost:8081/kbfira_docs/index.php/ にアクセスしてホーム画面が表示されたらOK

    ![image](https://github.com/LearningEngineeringLaboratory/kbfira_setup/assets/134689144/a890925b-5af9-47fc-912e-538c40cb879c)




