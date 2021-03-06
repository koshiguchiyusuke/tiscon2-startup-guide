#QA一覧
***
* [mvnが正常に動作しない (mvn --versionコマンドが失敗する)](#mvnが正常に動作しない-mvn---versionコマンドが失敗する)
* [IntelliJでのプロジェクトのcloneができない](#intellijでのプロジェクトのcloneができない)
* [動作確認していると ClassCastException が出る](#動作確認していると-classcastexception-が出る)

***

## Windowsマシンで `mvn --version` コマンドが失敗する

* エラー例①<br>
![java_home is not set](image/qa_javahome.png)
* エラー例②<br>
![mvn command not found](image/qa_mvnpath.png)

JDKまたはMavenの環境変数設定が誤っている可能性があります。
JDK,Mavenをインストールしたディレクトリと環境変数が一致しているかを確認してみてください。
(環境変数に指定しているディレクトリが実際に存在しているか確認してください)

### JDKの環境変数設定
1. システム環境変数『Path』 (例) `C:\Program Files\Java\jdk1.8.0_121\bin`
1. システム環境変数『JAVA_HOME』 (例) `C:\Program Files\Java\jdk1.8.0_121`

> **【補足】**
> * ユーザー環境変数とシステム環境変数の両方に同じ変数名で値が設定されている場合、ユーザー環境変数の値が優先されてしまいます。ユーザー環境変数に『JAVA_HOME』が存在する場合、そちらは削除してください。
> * 環境変数『Path』だけはユーザー変数がシステム変数を上書きせず、両方の値が「;」で連結された設定となります。

### Mavenの環境変数設定
1.システム環境変数『Path』
　　例)C:\Program Files\apache-maven-3.2.5\bin

> **【補足】**
> * 環境構築手順に記載しているように、ダウンロードしたMavenは「C:\Program Files」に格納してください。そうした場合、Pathの変数値は上記例の通りになります。

## IntelliJでのプロジェクトのcloneができない
下記の問題である可能性があります。確認してみてください。

### URLの入力誤り
Git Repository URLに入力しているURLが正しいかを確認してください。
入力するURLは `https://github.com/[Githubのユーザ名]/tiscon2.git` です。

### 自身のGithubアカウントでのプロジェクトForkができていない
Githubにログインし、[GitHubトップページ](https://github.com/)を見てtiscon2のforkができているかを確認してください。
forkができていれば、リポジトリ一覧に「tiscon2」が表示されます。

![repositories](image/qa_github_top.png)

forkできていなかった場合は、もう一度環境構築手順に従いプロジェクトのforkを行って下さい。

### Gitインストールが完了していない
コマンドプロンプトで `git --version` と入力し、gitのバージョン情報が表示されるか確認してください。
表示されない場合、Gitのインストールに失敗しています。Gitのインストールを行ってください。

## 動作確認していると ClassCastException が出る
tiscon2が使っている別プログラムが読み込めていないかもしれません。プログラムをリフレッシュしましょう。

1. IntelliJを開いてください。
1. Shiftキーを2回カチカチッと叩くと、検索窓が表示されます。そこに「reimport all maven projects」と入力すると、そのような選択肢が出るのでそれを選択してください。![reimport all maven projects](image/qa_reimport_all_maven_projects.png)
1. IntelliJ の画面右下に「Resolving Maven Dependencies...」というようなメッセージと一緒に進行度合いを示すバーが表示されるので、それが消えるまで待ってください。
1. これでプログラムの再読込ができました。再度動作確認をしてみてください。

### 解決しない場合
スタッフに問い合わせてください。その際、

* 環境構築手順の各手順の、「インストールできたら」のステップの実行結果をスクリーンショットもしくはテキストとしてコピペして教えてください。
* 表示されたメッセージが見えるIntelliJの画面のスクリーンショットを撮影してください。
* Shiftキーを2回叩いて出てきた検索窓に「Terminal」と入力して出てきた結果を選択し、表示されたTerminalタブに 「mvn clean install」と入力してEnterしてください。その結果出てきたメッセージをすべてコピーして、テキストファイルに貼り付けて添付してください。
