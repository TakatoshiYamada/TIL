# 5th June 2023

- [5th June 2023](#5th-june-2023)
  - [Linux](#linux)
    - [aptでapache2-utilsの2.2.22-1ubuntu1.11をインストールしたい](#aptでapache2-utilsの2222-1ubuntu111をインストールしたい)
    - [パッケージが見つかりませんって出たね](#パッケージが見つかりませんって出たね)
    - [dpkgのリストからインストールするべきパッケージを判断したい](#dpkgのリストからインストールするべきパッケージを判断したい)
    - [apt-get install apache2ならエラー起きないのかな？まだ試してないけど](#apt-get-install-apache2ならエラー起きないのかなまだ試してないけど)
    - [dpkg -lの内容をインストールしようとしても失敗する。依存関係があるからかも？](#dpkg--lの内容をインストールしようとしても失敗する依存関係があるからかも)
    - [apatch2-utils単体だとapt-get installできない？](#apatch2-utils単体だとapt-get-installできない)
    - [tar.gzになってるモジュールをインストールする方法ってある？](#targzになってるモジュールをインストールする方法ってある)
    - [whereis でフルパスって出せる？](#whereis-でフルパスって出せる)
    - [tarで解凍したhttpd-2.2.29をどこに置くかわからなくて。現開発環境ではどこにあるのか調べたくなった](#tarで解凍したhttpd-2229をどこに置くかわからなくて現開発環境ではどこにあるのか調べたくなった)
    - [vsftpdってなに](#vsftpdってなに)
    - [PREFIX/bin/apachectl startってINSTALLにある。なんだろう](#prefixbinapachectl-startってinstallにあるなんだろう)
    - [makeできない。apt-getもデータベースに存在するが利用できないという](#makeできないapt-getもデータベースに存在するが利用できないという)
    - [build essentialはパッケージが見つかりませんときた](#build-essentialはパッケージが見つかりませんときた)
    - [sudo apt-get updateって安全なの？railsのbundle updateでハマったことがあるから不安](#sudo-apt-get-updateって安全なのrailsのbundle-updateでハマったことがあるから不安)
    - [sudo apt-get updateは無視とエラーと取得に失敗しましたばかりでる](#sudo-apt-get-updateは無視とエラーと取得に失敗しましたばかりでる)
    - [他のサーバからbuild-essentialだけをコピーしちゃダメなの？](#他のサーバからbuild-essentialだけをコピーしちゃダメなの)
    - [dpkgでbuildessential入れた方がいいかな](#dpkgでbuildessential入れた方がいいかな)
    - [sudo apt-get install build-essentialでパッケージが見つかりませんって出る](#sudo-apt-get-install-build-essentialでパッケージが見つかりませんって出る)
    - [やっぱダメっぽい。ネットワークかなあ](#やっぱダメっぽいネットワークかなあ)
    - [/usrディレクトリってバイナリの展開先だからscpでコピーするようなものじゃないと思うけど、どう思う？](#usrディレクトリってバイナリの展開先だからscpでコピーするようなものじゃないと思うけどどう思う)
    - [makeをするのに何をaptすればいい？](#makeをするのに何をaptすればいい)
    - [Ubuntuのリポジトリが切り替わった問題ってある？持ってる知識まででいいから](#ubuntuのリポジトリが切り替わった問題ってある持ってる知識まででいいから)
    - [3.13.0-32-genericなんだよね、今のUbuntu](#3130-32-genericなんだよね今のubuntu)
    - [MySQLのtarを解凍したけど、どうすれはいいかわからない](#mysqlのtarを解凍したけどどうすれはいいかわからない)

## Linux

### aptでapache2-utilsの2.2.22-1ubuntu1.11をインストールしたい

特定のバージョンのパッケージをインストールするには、以下のコマンドを使用します：

```bash
sudo apt-get install apache2-utils=2.2.22-1ubuntu1.11
```

ただし、このコマンドが正常に動作するためには、そのバージョンのパッケージが利用可能である必要があります。もし指定したバージョンがリポジトリに存在しない場合、エラーメッセージが表示されるでしょう。

また、セキュリティや互換性の問題から、特定のバージョンに固執せず、可能な限り最新の安定版を使用することをお勧めします。

### パッケージが見つかりませんって出たね

そのエラーメッセージは、指定されたバージョンのパッケージがリポジトリに存在しないことを示しています。以下は問題を解決するためのいくつかの提案です：

パッケージリストの更新: sudo apt-get update を実行し、パッケージリストを最新の状態に更新します。

バージョン番号の確認: 指定されたバージョンが正しいか確認します。間違ったバージョン番号が指定されていると、このエラーが発生します。

適切なリポジトリの追加: パッケージが含まれているリポジトリがシステムに追加されているか確認します。そのパッケージが含まれているリポジトリがシステムに追加されていない場合、パッケージが見つからないというエラーが発生します。

特定のバージョンが必要で、それがリポジトリに存在しない場合、そのパッケージの公式ウェブサイトや信頼性の高いソースから.debファイルをダウンロードし、dpkg -i コマンドでインストールすることを検討することもできます。ただし、この方法はセキュリティリスクを伴う可能性があり、注意が必要です。

### dpkgのリストからインストールするべきパッケージを判断したい

dpkg コマンドを使用してシステム上のすべてのパッケージのリストを取得することができます。そのため、インストールしたいパッケージが既にシステムに存在するかどうかを確認できます。これを行うには、次のコマンドを実行します：

```bash
dpkg -l
```

このコマンドは、システム上のすべてのパッケージのリストを表示します。また、特定のパッケージについて検索することも可能です。例えば apache2-utils の場合、次のように実行します：

```bash
dpkg -l | grep apache2-utils
```

これにより、apache2-utils パッケージに関連する情報が表示されます。パッケージ名の隣にある情報は、そのパッケージのインストール状態とバージョンを示します。

あなたが特定のバージョンのパッケージをインストールする必要があるかどうかは、システムの要件やそのパッケージがどのように使用されるかによるため、注意深く判断してください。

### apt-get install apache2ならエラー起きないのかな？まだ試してないけど

sudo apt-get install apache2 というコマンドは、通常Apache HTTPサーバ（バージョン2）をインストールします。このコマンドが成功するかどうかは、あなたのシステムとその設定に依存しますが、通常は成功します。

ただし、以下のような事前確認と事後手順が推奨されます：

パッケージリストの更新：まず、パッケージリストを更新します。これにより、最新のパッケージが利用可能になります。コマンドは sudo apt-get update です。

Apache2のインストール：次に、Apacheをインストールします。コマンドは sudo apt-get install apache2 です。

サービスの確認：インストールが成功したら、Apacheサービスが正常に動作していることを確認します。これは systemctl status apache2 または sudo service apache2 status というコマンドで確認できます。

ブラウザからの確認：Apacheが正常に動作していれば、ブラウザから<http://localhost> (またはサーバのIPアドレス) にアクセスすると、Apacheのデフォルトページが表示されます。

エラーが発生した場合は、エラーメッセージを確認して問題をトラブルシューティングします。

### dpkg -lの内容をインストールしようとしても失敗する。依存関係があるからかも？

dpkg コマンドを使用してパッケージをインストールするとき、そのパッケージが依存している他のパッケージがすべてインストールされていないと、エラーが発生することがあります。apt-get コマンドは依存関係を自動的に解決しますが、dpkg コマンドはそのような機能はありません。

依存関係の問題を解決するには、次の手順を試してみてください：

dpkg コマンドを使用してパッケージをインストールします。依存関係の問題が発生した場合、エラーメッセージが表示されます。

エラーが発生したら、sudo apt-get -f install コマンドを実行します。このコマンドは、依存関係の問題を自動的に解決しようとします。

これらの手順が問題を解決しない場合、エラーメッセージをもとに具体的なトラブルシューティングを行う必要があります。

### apatch2-utils単体だとapt-get installできない？

通常、apache2-utilsパッケージは単独で apt-get install コマンドを使用してインストールできます。以下のコマンドを実行します：

```bash
sudo apt-get install apache2-utils
```

ただし、以下のいくつかのシナリオではエラーが発生する可能性があります：

パッケージリストが更新されていない場合。これを解決するには sudo apt-get update を実行します。

apache2-utils パッケージがリポジトリにない場合。この場合、適切なリポジトリを追加するか、パッケージの公式ウェブサイトから.debファイルをダウンロードする必要があります。

パッケージが依存している他のパッケージが存在しない、または適切なバージョンがない場合。この場合、sudo apt-get -f install を実行して依存関係の問題を解決します。

これらの解決策が機能しない場合、エラーメッセージを確認して具体的な問題を特定します。

### tar.gzになってるモジュールをインストールする方法ってある？

はい、tar.gz形式のファイルからモジュールをインストールする方法は存在します。通常、この形式のファイルはソースコードが含まれていて、それをビルドしてインストールすることが求められます。

基本的な手順は以下の通りです：

ファイルの展開: 最初に、tarコマンドを使ってファイルを展開します。コマンドは tar -xvzf filename.tar.gz です。ここで "filename.tar.gz" は実際のファイル名に置き換えてください。

ディレクトリへの移動: 展開すると、通常は新たにディレクトリが作られます。cdコマンドでそのディレクトリに移動します。

インストールの準備: そのディレクトリ内には通常、インストールの手順が書かれたREADMEファイルやINSTALLファイルが含まれています。それらのファイルを読んで、必要な依存関係を解決し、特別なインストール手順が必要な場合はそれに従います。

ビルドとインストール: 通常、以下のコマンドを順に実行することでビルドとインストールが行えます：

```bash
./configure
make
sudo make install
```

この手順は一般的なもので、特定のソフトウェアやモジュールによっては異なる手順が必要な場合もあります。そのため、必ず公式のドキュメンテーションや含まれているREADMEファイルを参照してください。

### whereis でフルパスって出せる？

whereisコマンドはプログラムのバイナリ、ソース、マニュアルの位置を表示します。通常、このコマンドは結果としてファイルのフルパスを表示します。

例えば、lsコマンドの場所を調べるには以下のようにします：

```bash
whereis ls
```

このコマンドを実行すると、以下のような出力が得られます（システムによります）：

```bash
ls: /bin/ls /usr/share/man/man1/ls.1.gz
```

この結果は、lsコマンドのバイナリが /bin/lsにあり、マニュアルが /usr/share/man/man1/ls.1.gzにあることを示しています。

したがって、whereisコマンドはフルパスを表示します。ただし、whereisコマンドはシステムの標準パスにあるファイルしか見つけられないため、その他の場所にあるファイルを探すにはfindやlocateコマンドを使用することを検討してみてください。

### tarで解凍したhttpd-2.2.29をどこに置くかわからなくて。現開発環境ではどこにあるのか調べたくなった

tarで解凍したhttpd-2.2.29（Apache HTTP Server）のソースコードの配置場所は、基本的にはあなたが選択することができます。一般的には、ユーザのホームディレクトリや /usr/local/src のような場所に置かれます。これはビルド作業を行うための一時的な場所で、完成したバイナリは通常 /usr/local/apache2 にインストールされます（デフォルトの設定に従った場合）。

ただし、すでにApacheがインストールされていて、その位置を調べたい場合は、以下のコマンドを使用することができます：

```bash
whereis httpd
```

または

```bash
whereis apache2
```

これらのコマンドはApacheのバイナリ、マニュアル、設定ファイルなどがどこにあるかを教えてくれます。しかし、これらのコマンドはシステムの標準的なパスに基づいています。

Apache HTTP Serverは通常、設定ファイルを /etc/httpd や /etc/apache2 に、バイナリを /usr/sbin に、ウェブコンテンツを /var/www に配置します。ただし、これはディストリビューションや具体的な設定により異なる場合があります。したがって、特定のシステムでApacheがどのように配置されているかを把握するためには、具体的な設定ファイルを確認する必要があります。

### vsftpdってなに

vsftpd は "Very Secure FTP Daemon" の略で、Linux でよく使われる FTP（File Transfer Protocol）サーバの一つです。FTPはインターネットを介してコンピュータ間でファイルを転送するためのプロトコルです。

vsftpd の特徴はそのセキュリティとパフォーマンスにあります。デフォルトの設定では、一部の危険なFTPコマンドは無効化されていて、強固なセキュリティが確保されています。また、軽量で効率的な設計により、高速なファイル転送が可能であり、大規模なFTPサーバにも対応できます。

FTPは比較的古いプロトコルで、暗号化されていない状態ではデータが盗まれるリスクがあるため、セキュアなファイル転送が必要な場合はSFTP（SSH File Transfer Protocol）やFTP over SSL/TLSなど、暗号化をサポートしたプロトコルを利用することが推奨されています。vsftpd もこれらのセキュアなプロトコルに対応しています。

```bash
./configure --prefix=PREFIX
make
sudo make install
PREFIX/bin/apachectl start
```

### PREFIX/bin/apachectl startってINSTALLにある。なんだろう

この手順はソースコードからApache HTTP Serverをビルドしてインストールするための一般的な手順です。それぞれのコマンドの役割は以下の通りです：

./configure --prefix=PREFIX : configureスクリプトは、ソフトウェアをビルドする前にシステムをチェックし、適切な設定を生成します。--prefix=PREFIX オプションはインストール先のディレクトリを指定します。ここで、PREFIXは具体的なパスに置き換えます。たとえば、/usr/local/apache2 を指定する場合は、./configure --prefix=/usr/local/apache2となります。

make : makeコマンドは、configureスクリプトが生成した設定に基づいてソフトウェアをビルド（コンパイル）します。

sudo make install : このコマンドはビルドしたソフトウェアをシステムにインストールします。sudoを使用しているのは、通常はインストール先のディレクトリへの書き込みには管理者権限が必要だからです。

PREFIX/bin/apachectl start : ここで、PREFIXは先程の./configure --prefix=PREFIXで指定したパスに置き換えます。このコマンドは、Apacheサーバを起動します。たとえば、/usr/local/apache2にインストールした場合は、/usr/local/apache2/bin/apachectl startとなります。

この手順を通じてApache HTTP Serverをソースコードからビルドし、システムにインストールすることができます。

### makeできない。apt-getもデータベースに存在するが利用できないという

makeコマンドが利用できない、またはapt-getでパッケージがデータベースに存在するが利用できないというエラーはいくつかの原因で発生する可能性があります。

以下は、エラーの解決に向けた一般的な手順です：

必要なパッケージのインストール：makeコマンドを実行するためには、build-essentialパッケージが必要です。次のコマンドを実行してインストールしてみてください：sudo apt-get install build-essential

パッケージリストの更新：apt-getがデータベースにパッケージが存在すると報告しているが、インストールできない場合、古いパッケージリストが原因かもしれません。次のコマンドを実行してパッケージリストを更新してみてください：sudo apt-get update

依存関係の解決：ソースコードのビルドに必要な依存関係が足りない可能性もあります。ソースコードのドキュメンテーションやREADMEファイルで必要な依存関係を確認し、それらがすべてインストールされていることを確認してください。

これらの手順を試した上で、まだ問題が解決しない場合は、エラーメッセージの具体的な内容をもとに追加のトラブルシューティングを行う必要があります。エラーメッセージの詳細を提供していただければ、更に具体的なアドバイスを提供することが可能です。

### build essentialはパッケージが見つかりませんときた

build-essentialが見つからないとのエラーは、パッケージリストが最新でないか、リポジトリ設定が正しくない可能性があります。

まず、パッケージリストを更新してみてください。以下のコマンドを実行します：

```bash
sudo apt-get update
```

このコマンドが完了したら、再度build-essentialパッケージのインストールを試みてみてください：

```bash
sudo apt-get install build-essential
```

もしまだbuild-essentialが見つからない場合、システムのリポジトリ設定が正しくないかもしれません。UbuntuなどのDebianベースのシステムでは、/etc/apt/sources.listと/etc/apt/sources.list.d/ディレクトリ内のファイルがリポジトリ設定を保持しています。これらのファイルを確認し、公式のリポジトリが正しくリストされていることを確認してみてください。

なお、これらの操作によって問題が解決しない場合、システムの詳細やエラーメッセージの全文など、より多くの情報が必要になるかもしれません。

### sudo apt-get updateって安全なの？railsのbundle updateでハマったことがあるから不安

sudo apt-get update コマンドは、UbuntuやDebianといったLinuxディストリビューションで使われるパッケージ管理システムAPTの一部で、このコマンドは通常、非常に安全です。これはシステム上のパッケージのリストを更新するだけで、既存のソフトウェアやシステム設定を変更したりはしません。

このコマンドは、システムがインターネット上のリポジトリから利用可能なパッケージとそのバージョンの最新リストを取得します。このため、新しいパッケージをインストールしたり、既存のパッケージを更新したりする前には、このコマンドを実行してパッケージリストを最新の状態にしておくことが一般的です。

なお、sudo apt-get update コマンドと混同されやすい sudo apt-get upgrade コマンドは、システム上の全てのパッケージを最新バージョンにアップグレードします。この upgrade コマンドは、新しいバージョンのパッケージによって互換性の問題が発生する可能性があるため、注意が必要です。

Railsの bundle update コマンドは、Rubyの依存関係管理ツールであるBundlerの一部で、Gemfileにリストされたすべてのgemを最新バージョンに更新します。これもまた、新しいバージョンのgemによって互換性の問題が発生する可能性があるため、注意が必要です。

### sudo apt-get updateは無視とエラーと取得に失敗しましたばかりでる

sudo apt-get update コマンドを実行した際に "無視" や "エラー"、 "取得に失敗しました" というメッセージが表示される場合、いくつかの一般的な原因があります：

リポジトリのURLが間違っている： /etc/apt/sources.list ファイルや /etc/apt/sources.list.d/ ディレクトリ内のファイルを確認して、リポジトリのURLが正しいことを確認してください。

ネットワーク接続の問題： ネットワークが正常に動作していることを確認してください。一時的な接続問題が原因である場合もあります。

リポジトリが一時的に利用できない： 特定のリポジトリが一時的にダウンしている可能性があります。しばらく待ってから再度 sudo apt-get update コマンドを試すと解決することがあります。

プロキシ設定の問題： システムがプロキシ経由でインターネットに接続している場合、その設定が正しいか確認してください。

これらの手段で問題が解決しない場合、エラーメッセージの詳細な内容が必要になるかもしれません。具体的なエラーメッセージを教えていただければ、より具体的なアドバイスを提供できます。

### 他のサーバからbuild-essentialだけをコピーしちゃダメなの？

Linuxのパッケージ管理システムであるAPTでは、パッケージ（この場合は build-essential）をインストールする際に、そのパッケージの依存関係も自動的に管理されます。これにより、必要なすべてのパッケージが適切にインストールされ、システム全体の整合性が保たれます。

一方、パッケージを他のサーバから直接コピーすると、この依存関係の管理が適切に行われず、システムが不安定になる可能性があります。また、パッケージのバイナリファイルは特定のシステムアーキテクチャやOSバージョンに対してコンパイルされているため、異なる環境へのコピーは予期せぬ問題を引き起こす可能性があります。

したがって、パッケージを他のサーバから直接コピーすることは通常は推奨されません。パッケージのインストールに問題がある場合は、まずはその原因を解決することをお勧めします。

なお、非常に特殊な状況下では、パッケージの手動コピーとインストールが必要になることもありますが、そのようなケースは一般的には限られています。その場合でも、必要な依存関係を正しく満たすように注意する必要があります。

### dpkgでbuildessential入れた方がいいかな

UbuntuやDebianベースのシステムでは、dpkgは直接パッケージをインストールするためのツールです。しかし、dpkgはapt-getとは異なり、パッケージの依存関係を自動的に解決しません。つまり、build-essentialパッケージが依存する他のパッケージがシステムにすでに存在しなければ、dpkgで直接インストールしようとしてもうまく行かない可能性があります。

そのため、通常はapt-getを使用してパッケージをインストールすることが推奨されます。しかし、あなたのシステムが何らかの理由でapt-getを使用できない場合、dpkgを使って手動でインストールすることも一つの選択肢となります。

build-essentialパッケージをdpkgを使ってインストールするには、まず手元にその.debパッケージファイルが必要です。それをダウンロードした上で、以下のようなコマンドを実行します：

```bash
sudo dpkg -i /path/to/package.deb
```

ただし、この方法では依存関係が解決できない場合があります。その場合、apt-getを使って依存関係を解決することが可能です：

```bash
sudo apt-get install -f
```

これにより、dpkgでインストールしようとしたパッケージの依存関係が解決され、インストールが完了するはずです。

### sudo apt-get install build-essentialでパッケージが見つかりませんって出る

"パッケージが見つからない"というエラーは、通常は以下の理由により発生します：

パッケージ名が間違っている
パッケージがレポジトリに存在しない
aptのパッケージリストが最新ではない
正しいレポジトリがシステムに設定されていない
build-essentialは、UbuntuやDebianなどの多くのLinuxディストリビューションにおいて標準のパッケージであり、通常はこの名前で問題なくインストールできるはずです。そのため、エラーの原因はおそらく3番目か4番目の可能性が高いです。

まず、aptのパッケージリストを更新してみてください：

``` bash
sudo apt-get update
```

もしまだ問題が解決しない場合は、システムのレポジトリ設定を確認すると良いでしょう。UbuntuなどのDebianベースのシステムでは、/etc/apt/sources.listと/etc/apt/sources.list.d/ディレクトリ内のファイルがレポジトリ設定を保持しています。

なお、これらの対応により問題が解決しない場合は、システムの詳細（例えば、OSのバージョンなど）やエラーメッセージの詳細な内容など、より多くの情報が必要となる可能性があります。

### やっぱダメっぽい。ネットワークかなあ

あなたがネットワーク接続の問題を疑っているなら、それが原因である可能性が高いです。パッケージをインストールするためには、システムがパッケージリポジトリに接続できる必要があります。ネットワーク接続に問題がある場合、apt-getはパッケージを検索し、ダウンロードすることができません。

もし可能なら、別のネットワーク環境で同じコマンドを試してみてください。もしくは、ネットワークの設定（プロキシ設定、DNS設定など）が適切かどうかを確認してみてください。

また、サーバが企業ネットワーク内にある場合や、特定のネットワークポリシー下で運用されている場合は、ネットワーク管理者に確認すると良いでしょう。

### /usrディレクトリってバイナリの展開先だからscpでコピーするようなものじゃないと思うけど、どう思う？

Linuxのファイルシステム階層構造では、/usrディレクトリは通常、ユーザーレベルのアプリケーションソフトウェアとその関連データを格納するために使用されます。たとえば、/usr/binは実行可能バイナリを、/usr/libはライブラリを、そして/usr/shareはアーキテクチャに依存しない（共有可能な）データを格納するためのディレクトリとなります。

それぞれのディストリビューションやパッケージは独自の規則を持ち、一部のソフトウェアは/optや/usr/localなど、他の場所にインストールされることもあります。

したがって、バイナリを/usrディレクトリに直接コピーするのは、一般的には推奨されません。これは、パッケージ管理システム（apt, yum, dnf, pacmanなど）が提供する依存関係の管理、バージョン管理、設定ファイルの管理など、多くの機能を失うためです。

しかし、特定の状況下（例えば、特定のバイナリがパッケージ管理システムで利用できない場合）では、バイナリを直接コピーすることが必要になることもあります。その場合でも、システムの整合性と安全性を確保するためには、慎重に作業することが重要です。

### makeをするのに何をaptすればいい？

Linuxのソフトウェアをソースからビルドするためには、makeツールとgcc（GNUコンパイラコレクション）が必要です。これらは一般的にbuild-essentialパッケージに含まれています。

build-essentialパッケージはmakeやgccなどの基本的な開発ツールをインストールします。UbuntuやDebianベースのシステムでは以下のコマンドでインストールできます：

```bash
sudo apt-get install build-essential
```

ただし、あなたのシステムがネットワークに接続されていないか、なんらかの理由でapt-getコマンドがうまく機能しない場合、別の方法を考える必要があります。それは別のマシンから必要なパッケージをダウンロードし、それをターゲットのマシンに転送するなどです。ただし、その場合でもパッケージの依存関係を満たす必要があります。

### Ubuntuのリポジトリが切り替わった問題ってある？持ってる知識まででいいから

Ubuntuのリポジトリが切り替わるという問題は、主にUbuntuのバージョンが非サポート（End of Life, EOL）になったときに発生します。

Ubuntuは新しいバージョンがリリースされると、古いバージョンのサポートを一定期間経過後に終了します。これは通常、リリース日から5年後（LTSリリースの場合）とされています。

サポート期間が終了した後、そのUbuntuバージョンの公式リポジトリは通常、archive.ubuntu.comやold-releases.ubuntu.comといった場所に移動されます。これにより、サポート終了後のバージョンでもパッケージをダウンロードできるようになっています。

しかし、これはあくまで過去のパッケージへのアクセスを可能にするためのもので、これらのパッケージへのセキュリティアップデートは提供されません。したがって、可能な限り最新かつサポートされているUbuntuバージョンを使用することが推奨されます。

なお、このリポジトリ切り替えの問題が発生した場合、/etc/apt/sources.list ファイルを更新して、新しいリポジトリのURLを指すように変更することで対応可能です。ただし、そのUbuntuバージョンが非サポート状態であることを理解した上で行うべきです。

### 3.13.0-32-genericなんだよね、今のUbuntu

3.13.0-32-genericはカーネルのバージョンを示しています。これはUbuntu 14.04 LTS (Trusty Tahr)がリリースされた時期のカーネルで、このUbuntuバージョンは2019年にサポートが終了しています。

サポートが終了したUbuntuバージョンを使用している場合、セキュリティアップデートが提供されないため、システムは脆弱性に対して保護されていない可能性があります。したがって、可能であれば最新のサポートされているバージョンにアップグレードすることを強く推奨します。

なお、サポートが終了したUbuntuバージョンに対するパッケージのインストールが必要な場合は、/etc/apt/sources.listを編集して、パッケージリポジトリのURLをold-releases.ubuntu.comに変更することで対応できます。ただし、この操作はセキュリティリスクを伴うため、十分に注意が必要です。

### MySQLのtarを解凍したけど、どうすれはいいかわからない

MySQLのtarファイルを解凍した後、次に進むためにはMySQLをビルドしてインストールする必要があります。ただし、MySQLのソースコードから直接ビルドする作業は複雑で時間がかかる場合があります。以下に、一般的な手順を示します：

依存関係のインストール: MySQLをビルドするためにはいくつかのライブラリやツールが必要です。これには通常、cmake, make, gcc, libncurses5-dev などが含まれます。

ビルドの準備: 解凍したディレクトリ内で cmake . を実行します。これによりビルドのためのMakefileが作成されます。

ビルド: make を実行します。これによりソースコードがコンパイルされ、実行可能バイナリが生成されます。

インストール: sudo make install を実行します。これによりビルドしたMySQLがシステムにインストールされます。

注意点として、MySQLの公式サイトには多くのプラットフォームとバージョンに対応したバイナリパッケージが提供されています。ソースからビルドするよりも、これらのバイナリパッケージを使用する方が簡単で安全かつ効率的です。

なお、具体的なビルド手順や依存関係は、ダウンロードしたMySQLのバージョンや、使用しているシステムのバージョンによって異なる場合があります。そのため、具体的な手順については、ダウンロードしたソースコードに付属するドキュメンテーション（READMEやINSTALLなど）を参照してください。