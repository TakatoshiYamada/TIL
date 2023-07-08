# 8th June 2023

- [8th June 2023](#8th-june-2023)
  - [reboot](#reboot)
    - [VMwareの仮想環境だと再起動しても他のサーバに影響は与えないよね](#vmwareの仮想環境だと再起動しても他のサーバに影響は与えないよね)
    - [Ubuntuだとbootでいいんだっけ](#ubuntuだとbootでいいんだっけ)
    - [rebootしたら繋がらなくなった](#rebootしたら繋がらなくなった)
    - [readlineのアプデでOSの起動がコケるようになってしまった](#readlineのアプデでosの起動がコケるようになってしまった)
  - [Library install](#library-install)
    - [Ubuntuのpcreって何をするの？](#ubuntuのpcreって何をするの)
    - [error zlib-headers and/or libs where not foundエラーが出た](#error-zlib-headers-andor-libs-where-not-foundエラーが出た)
  - [fastcgi](#fastcgi)
    - [fastcgiってなに](#fastcgiってなに)
    - [fcgi, libfcgi , mod\_fastcgiってtarがあるんだけど、何から手をつけるべき？](#fcgi-libfcgi--mod_fastcgiってtarがあるんだけど何から手をつけるべき)
    - [lighttpd使ってるならmodはいらないかな](#lighttpd使ってるならmodはいらないかな)
    - [fast CGIってアプリケーションサーバなの？](#fast-cgiってアプリケーションサーバなの)
    - [fcgiのバージョンってどう確認すればいいの？](#fcgiのバージョンってどう確認すればいいの)
  - [make uninstall](#make-uninstall)
    - [configureやmakeしたものってどうやってアンインストールするの？](#configureやmakeしたものってどうやってアンインストールするの)
  - [gem install](#gem-install)
    - [railsを入れてと言われ、大量のgemが入ったディレクトリを渡されたのだけど、どこから手をつければいいのかわからない。rails1.1.2ってどうすれば](#railsを入れてと言われ大量のgemが入ったディレクトリを渡されたのだけどどこから手をつければいいのかわからないrails112ってどうすれば)
    - [gemからインストールするかbundleでインストールするべきか](#gemからインストールするかbundleでインストールするべきか)
    - [gem単体からインストールってどうなの](#gem単体からインストールってどうなの)
    - [現開発環境でrailsがどのように動いているか知りたい。bundler探したりrailsの起動みたり](#現開発環境でrailsがどのように動いているか知りたいbundler探したりrailsの起動みたり)
    - [rails serverじゃなくてshで起動されてるのかも。ps auxでrailsのプロセスが見当たらない](#rails-serverじゃなくてshで起動されてるのかもps-auxでrailsのプロセスが見当たらない)
  - [local gem install](#local-gem-install)
    - [gemのファイルからrailsをインストールをしないと古い環境を構築できないみたい](#gemのファイルからrailsをインストールをしないと古い環境を構築できないみたい)
  - [find etc](#find-etc)
  - [現開発環境にgemfileがないか検索したい](#現開発環境にgemfileがないか検索したい)
    - [拡張子tgzってどうやって解凍すればいいの？](#拡張子tgzってどうやって解凍すればいいの)
    - [make installしたrubyを再インストールするためにmake uninstallしようとしたらno rule to make target uninstallって出た](#make-installしたrubyを再インストールするためにmake-uninstallしようとしたらno-rule-to-make-target-uninstallって出た)
    - [zlib入れてるのにzlibのエラーが発生する。gem入れたいんだけど](#zlib入れてるのにzlibのエラーが発生するgem入れたいんだけど)
    - [zlibをインストールしたのにダメっぽい](#zlibをインストールしたのにダメっぽい)
    - [ruby 1.8.6をapt-getで入れてみる](#ruby-186をapt-getで入れてみる)
    - [バージョン1.8.7が入ってしまった。1.8.6を指定したい](#バージョン187が入ってしまった186を指定したい)

## reboot

### VMwareの仮想環境だと再起動しても他のサーバに影響は与えないよね

はい、その通りです。VMwareを使って各サーバーは独立した仮想マシンとして動作しますので、一つの仮想マシンを再起動しても、同じ物理ホスト上の他の仮想マシンには直接的な影響はありません。ただし、その仮想マシンが提供するサービスやアプリケーションに依存している他のサーバーがある場合、それらのサーバーは間接的に影響を受ける可能性があります。

### Ubuntuだとbootでいいんだっけ

Ubuntuを再起動するためには通常、以下のコマンドをターミナルで入力します。

```bash
sudo reboot
```

あるいは、

```bash
sudo shutdown -r now
```

どちらのコマンドもシステムを即座に再起動します。"sudo"は「スーパーユーザーとしてこのコマンドを実行する」という意味で、再起動のようなシステムレベルの操作を行うためには通常、スーパーユーザーの権限が必要となります。

### rebootしたら繋がらなくなった

再起動後に接続できない理由はいくつか考えられます。以下にいくつか可能性を挙げてみます：

Ubuntuが正しく再起動しなかった：何らかの理由でUbuntuが起動しきれず、ネットワークに接続できない状態になっているかもしれません。

ネットワーク設定の問題：再起動後にネットワーク設定が変わってしまい、ネットワーク接続ができなくなった可能性があります。

ファイアウォールやセキュリティ設定：ファイアウォールや他のセキュリティ設定が再起動後の接続をブロックしている可能性があります。

これらの問題を診断・解決するためには、直接Ubuntuのコンソールにアクセスしたり、ホストマシンの設定を確認するなど、更なる調査が必要です。それが難しい場合は、ITの専門家に相談することをおすすめします。

### readlineのアプデでOSの起動がコケるようになってしまった

それは大変ですね。readlineライブラリのアップデートが原因でUbuntuが起動しなくなった場合、一般的な解決策は次のステップで試してみることです：
レスキューモード（またはシングルユーザーモード）でUbuntuを起動します。これは最小限のサービスだけでOSを起動するモードで、問題のあるシステムを修復するために使われます。
レスキューモードで起動したら、コマンドラインからreadlineをダウングレードするか、あるいはアップデート前の状態に戻します。次のコマンドを試してみてください：

```bash
sudo apt-get install --reinstall readline=[version]
```

上記コマンドで"[version]"の部分にダウングレードしたいreadlineのバージョンを指定します。適切なバージョンを指定するためには、apt-cache policy readlineコマンドで利用可能なバージョンを確認してみてください。
readlineのバージョンをダウングレードまたはアップデート前の状態に戻したら、システムを再起動します。
この手順が問題を解決することを願っています。しかし、それでも問題が解決しない場合は、詳しいエラーメッセージや、起動中に発生する問題の詳細な情報を持って、ITの専門家に相談することをおすすめします。

## Library install

### Ubuntuのpcreって何をするの？

PCREは "Perl Compatible Regular Expressions" の略で、これはPerl言語の正規表現を再現するライブラリです。

正規表現は特定の文字列を検索、置換、抽出するためのパターンです。PCREライブラリはPerlの強力な正規表現エンジンを他のプログラムで利用可能にします。
Ubuntuや他のLinuxシステムにおいては、PCREは多くのソフトウェアパッケージに必要な依存関係となっています。これにはWebサーバーやデータベース、システム管理ツールなどが含まれます。これらのツールは、ファイルの検索、ログファイルの分析、データの抽出といった作業を行う際にPCREを使用します。

### error zlib-headers and/or libs where not foundエラーが出た

このエラーメッセージは、通常、あなたがコンパイルまたはインストールしようとしているソフトウェアが、zlibというライブラリのヘッダーファイルやライブラリを必要としているが、それがシステム上に見つからないときに表示されます。
zlibはデータの圧縮と展開を行うためのソフトウェアライブラリで、多くのソフトウェアパッケージで使用されています。
この問題を解決するには、zlibの開発パッケージをインストールする必要があります。Ubuntuでは、以下のコマンドを実行してzlibの開発パッケージをインストールできます：

```bash
sudo apt-get install zlib1g-dev
```

このコマンドはスーパーユーザー権限（sudo）で実行する必要があります。インストールが完了したら、再度コンパイルまたはインストールを試みてください。これで問題が解決するはずです。

## fastcgi

### fastcgiってなに

FastCGI (Fast Common Gateway Interface)は、ウェブサーバとウェブアプリケーション間で通信するためのインターフェースの一つです。CGI (Common Gateway Interface)の改良版で、ウェブサーバのパフォーマンスを向上させる目的で開発されました。
通常のCGIはリクエストごとに新しいプロセスを作成しますが、このアプローチはリソースを大量に消費し、パフォーマンスに影響を及ぼします。それに対し、FastCGIは長期間稼働するプロセスを使用し、そのプロセス内で複数のリクエストを処理します。この結果、FastCGIはCGIよりもリソース効率が良く、応答時間も短縮されます。
FastCGIはPHP, Python, Ruby, Perlなどの多くのプログラミング言語でサポートされており、Apache, Nginx, Lighttpdなどの多くのウェブサーバでも利用することができます。

### fcgi, libfcgi , mod_fastcgiってtarがあるんだけど、何から手をつけるべき？

fcgi, libfcgi, および mod_fastcgi は、FastCGIインターフェースを実装するための異なるコンポーネントです。

fcgi: これはFastCGIの開発キットで、FastCGIアプリケーションを書くためのライブラリやツールが含まれています。

libfcgi: これはFastCGIアプリケーションの開発に使用されるCライブラリです。これは、FastCGIインターフェースを通じてウェブサーバと通信するアプリケーションを開発するために使います。

mod_fastcgi: これはApacheウェブサーバ用のFastCGIモジュールで、ApacheがFastCGIアプリケーションと通信できるようにするためのものです。

インストールする順番としては、通常は libfcgi を最初にインストールします。これはFastCGIアプリケーションを開発するための基本的なライブラリを提供するからです。次に fcgi 開発キットをインストールし、最後にApacheの mod_fastcgi モジュールをインストールします。
ただし、具体的な順序はあなたが何を達成しようとしているか、またはどのような依存関係があるかによるため、具体的な状況によります。また、これらのパッケージのインストールはそれぞれが提供するドキュメンテーションに従うことが重要です。

### lighttpd使ってるならmodはいらないかな

Lighttpdは自身がFastCGIをネイティブにサポートしているので、Apache用のmod_fastcgiは不要です。
Lighttpdを使用している場合、FastCGIアプリケーションを開発するためには、libfcgiまたはfcgi（もしくはその他の言語向けのFastCGIライブラリ）が必要になります。アプリケーションが開発されたら、Lighttpdの設定を行いFastCGIアプリケーションと通信できるようにします。
したがって、あなたがFastCGIを使用してウェブアプリケーションを開発し、それをLighttpd上で稼働させる予定なら、mod_fastcgiは不要となります。

そもそもインストールする必要あるのかな。railsとlighttpdとMySQLのサービスなんだけど。
あなたがRuby on Railsを使用してウェブアプリケーションを開発し、それをLighttpdウェブサーバーとMySQLデータベースと共に運用する予定であれば、FastCGIとして動作する設定が必要となります。
Railsアプリケーションは、通常Passengerなどのアプリケーションサーバを介して動作しますが、FastCGIを介しても動作させることができます。
具体的には、RailsアプリケーションをFastCGIとして動作させるためには、fcgi gemが必要となります。その後、Lighttpdの設定ファイルにRailsアプリケーションのFastCGI設定を追加します。
ただし、近年ではPassengerやPumaなどのアプリケーションサーバーを使用してRailsアプリケーションを運用することが一般的となっています。これらのサーバーはマルチスレッドの処理能力やより高度な機能を提供しており、FastCGIを介した運用よりも効率的なケースが多いです。
したがって、特にFastCGIで運用する理由がなければ、PassengerやPumaを使用することを検討してみてください。

### fast CGIってアプリケーションサーバなの？

FastCGI自体はアプリケーションサーバではなく、ウェブサーバとウェブアプリケーション間で通信を行うためのプロトコルです。

しかし、FastCGIはウェブアプリケーションサーバの役割を果たすことができます。それは、ウェブサーバ（ApacheやNginxなど）がクライアントからのリクエストを受け取り、それをFastCGIを介してウェブアプリケーション（PHP、Python、Rubyなど）に転送するという方法で動作します。ウェブアプリケーションはそのリクエストを処理し、結果をFastCGIを介してウェブサーバに返します。その後、ウェブサーバがその結果をクライアントに送信します。

しかし、言葉の使い方には注意が必要です。FastCGI自体がアプリケーションサーバーを「置き換える」わけではありません。むしろ、FastCGIはウェブサーバとウェブアプリケーション間の「橋渡し」を行い、二つが効率的に通信できるようにする役割を果たします。

### fcgiのバージョンってどう確認すればいいの？

FastCGI（fcgi）のバージョンを確認する方法は、インストールされたFastCGIの形式（ソースコードからのビルド、またはパッケージマネージャを使用したインストール）と、どのプログラミング言語や環境で使用しているかによります。
一部のシステムでは、以下のコマンドを使ってFastCGI（fcgi）のバージョンを確認することができます：

```bash
cgi-fcgi -version
```

または

```bash
/usr/bin/cgi-fcgi -version
```

しかし、これは FastCGI がシステム全体で利用可能なバイナリとしてインストールされている場合に限ります。

もしこのコマンドが利用できない場合、または特定のプログラミング言語やフレームワーク用のFastCGIライブラリのバージョンを知りたい場合は、その言語やフレームワーク特有の方法を使ってバージョンを確認する必要があります。

例えば、PHPでFastCGIを使用している場合は、phpinfo(); 関数を使ってFastCGIのバージョンを確認することができます。

もし特定の環境でのFastCGIのバージョンの確認方法がわからない場合は、その環境の詳細を教えていただければと思います。

## make uninstall

### configureやmakeしたものってどうやってアンインストールするの？

ソースコードからビルドしてインストールしたソフトウェアをアンインストールする方法は、そのソフトウェアが提供している機能によります。いくつかのソフトウェアでは make uninstall コマンドを提供しており、これを使うとインストールしたファイルを削除することができます。以下の手順で試してみてください：

ソフトウェアのソースコードがあるディレクトリに移動します。

sudo make uninstall コマンドを実行します。

ただし、全てのソフトウェアが make uninstall オプションをサポートしているわけではありません。その場合、インストールしたファイルを手動で削除する必要があります。これを行う一つの方法は、make install コマンドを再度実行し（今回は sudo を使わないでください）、コマンドがどのファイルをどこにコピーしようとしているかを確認することです。その情報を元に、それらのファイルを手動で削除します。

ただし、手動でファイルを削除する場合は注意が必要です。間違ったファイルを削除するとシステムが不安定になる可能性があります。また、この作業は管理者権限（sudo）が必要です。

なお、パッケージマネージャー（例えば apt、yum、dnf など）を使ってインストールしたソフトウェアのアンインストールは、パッケージマネージャーのコマンドを使って行います。これは make uninstall や手動での削除よりも簡単で安全な方法です。

## gem install

### railsを入れてと言われ、大量のgemが入ったディレクトリを渡されたのだけど、どこから手をつければいいのかわからない。rails1.1.2ってどうすれば

Ruby on Rails 1.1.2は非常に古いバージョンで、現在は非推奨となっています。そのため、最初に行うべきはRailsのバージョンアップです。古いバージョンのRailsは、新しい機能が利用できないだけでなく、セキュリティの脆弱性も存在する可能性があります。ただし、アップグレードは時間と労力が必要となります。

その一方で、Rails 1.1.2を使ってアプリケーションを動作させる必要があるなら、以下の手順を試してみてください：

必要なRubyバージョンをインストールします。Rails 1.1.2を動作させるためには、おそらく古いバージョンのRubyが必要となります。Rubyのバージョン管理ツール（rbenvやRVMなど）を使用して、適切なRubyバージョンをインストールします。

Bundlerをインストールします。これはRubyのパッケージマネージャで、gemの依存関係を管理します。

```bash
gem install bundler
```

そのRailsアプリケーションのルートディレクトリに移動し、Bundlerを使用してgemをインストールします。

```bash
bundle install
```

データベースを設定します。Railsアプリケーションの設定ファイル（config/database.yml）を見て、適切なデータベースが設定されていることを確認します。MySQLを使用している場合は、MySQLサーバが動作していて、適切なユーザとデータベースが存在することを確認します。

Railsサーバを起動します。

```bash
rails server
```

以上の手順で、Rails 1.1.2アプリケーションを動作させることができます。ただし、古いバージョンのRailsとRubyを使用することにはリスクが伴いますので、アップグレードを検討してみてください。

### gemからインストールするかbundleでインストールするべきか

Rubyのアプリケーション開発において、個々のgemを手動でgem installコマンドを使ってインストールする代わりに、Bundlerを使用して依存関係を管理することが推奨されています。

BundlerはRubyの依存関係管理ツールで、Gemfileという特殊なファイルを読み込んで、その中にリストアップされたすべてのgem（及びそれらのバージョン）を自動的にインストールします。これにより、アプリケーションの依存関係を一元管理し、他の開発者や環境との整合性を保つことができます。

つまり、Railsアプリケーションなどの開発においては、通常、以下のような手順でgemをインストールします：

アプリケーションのルートディレクトリにGemfileを作成（または編集）します。その中に、アプリケーションが必要とするすべてのgemとそのバージョンをリストアップします。

ターミナルでbundle installコマンドを実行します。これにより、Gemfileにリストアップされたgemがすべてインストールされます。

この方法であれば、アプリケーションがどのgemに依存しているのか、それらのバージョンは何なのかを明確に管理できます。また、bundle installコマンドを実行するだけで、必要なすべてのgemをインストールできるため、開発効率が向上します。

なお、手動で特定のgemをシステム全体にインストールしたい場合（例えば、bundler自体やrailsコマンドなど）は、gem installコマンドを使用します。

### gem単体からインストールってどうなの

Rubyのgemパッケージを手動でインストールする場合、gem install コマンドを使用します。このコマンドはRubyのパッケージ管理システムであるRubyGemsが提供しています。

例えば、rails gemをインストールするには以下のコマンドを実行します：

```bash
gem install rails
```

この方法でgemをインストールすると、そのgemがシステム全体で利用可能になります。

ただし、これは一つのgemをインストールするだけであり、そのgemが依存している他のgemについては手動で追加する必要があります。また、同じgemの異なるバージョンを同時に管理するのが難しくなります。

そのため、アプリケーションの依存関係を管理するには Bundler を使用する方がより効率的です。Bundler は Gemfile を読み込み、リストアップされた全てのgemとそのバージョンを自動でインストールします。この方法であれば、複数のgemの依存関係を一元的に管理し、他の開発者や環境との整合性を保つことができます。

したがって、システム全体で利用するgemをインストールする場合や、特定のgemを試す場合には gem install を使用します。一方、アプリケーションの開発や運用においては、Bundler を使用して依存関係を管理することをお勧めします。

### 現開発環境でrailsがどのように動いているか知りたい。bundler探したりrailsの起動みたり

Ruby on Railsのアプリケーションがどのように動作しているかを理解するには、以下の観点から確認を進めてみてください：

依存関係の確認： GemfileとGemfile.lockをチェックします。Gemfileにはアプリケーションが依存しているgemがリストアップされています。Gemfile.lockはbundle installを実行したときにBundlerによって自動生成され、具体的なgemのバージョンとそれらの依存関係が記述されています。

データベースの設定： config/database.ymlファイルを確認します。ここにはどのデータベースを使用し、その接続情報が何かが定義されています。

Railsの起動： bin/rails server（またはbundle exec rails server）コマンドを使ってRailsサーバーが起動します。開発環境では通常、このコマンドを使ってサーバーを起動し、ブラウザからアクセスします。

ルーティングの確認： config/routes.rbファイルを見ます。このファイルには、特定のURLパスにアクセスしたときにどのコントローラのどのアクションが呼び出されるかが定義されています。

コントローラとビュー： 各コントローラはapp/controllersディレクトリに、対応するビューはapp/viewsディレクトリに格納されています。これらのファイルを確認することで、アプリケーションのロジックや表示を理解することができます。

モデルとデータベーススキーマ： app/modelsディレクトリにはモデルのファイルが、db/schema.rbファイルにはデータベースのスキーマが定義されています。

これらを確認することで、アプリケーションの動作を理解することができます。また、Railsのドキュメンテーションやガイドも参照すると、より詳しい情報を得られます。

### rails serverじゃなくてshで起動されてるのかも。ps auxでrailsのプロセスが見当たらない

それなら、おそらくRailsアプリケーションは別の方法で実行されている可能性があります。シェルスクリプト（.shファイル）で起動されている場合、そのスクリプト内には実際の起動コマンドが記載されているはずです。

以下のコマンドを実行して現在動作しているプロセスを調べてみてください：

```bash
ps aux | grep ruby
```

もしくは、

```bash
ps aux | grep rails
```

これらのコマンドは、rubyまたはrailsを含むプロセスを探します。rails serverコマンドは、実際にはRubyのインタープリタであるrubyを使ってRailsアプリケーションを起動します。そのため、ps aux | grep rubyコマンドでRailsアプリケーションのプロセスを見つけることができる可能性があります。

シェルスクリプトが見つかった場合は、その内容を確認してみてください。おそらくその中には、Railsアプリケーションを起動するためのコマンド（たとえば、bundle exec rails serverやunicorn_railsなど）が含まれているはずです。

## local gem install

### gemのファイルからrailsをインストールをしないと古い環境を構築できないみたい

古いバージョンのRailsをインストールする場合、特定のバージョンのgemファイルからインストールすることが必要な場合があります。これは、そのバージョンのRailsがもはやRubyGemsの公式リポジトリから削除されていたり、古い依存関係を満たすために必要な場合があります。

この場合、以下の手順で古いバージョンのRailsをインストールできます：

ダウンロードしたgemファイル（例：rails-1.1.2.gem）が存在するディレクトリに移動します。

次のコマンドを実行してgemをインストールします：

```bash
gem install --local rails-1.1.2.gem
```

このコマンドは、指定したgemファイルをローカル環境にインストールします。--localオプションは、ローカルのgemファイルをインストールすることを指定します。
なお、古いバージョンのRailsを使用する場合は、そのバージョンのRailsが依存する古いバージョンのgemも必要になることがあります。その場合は、それらのgemも同様にインストールする必要があります。

## find etc

## 現開発環境にgemfileがないか検索したい

開発環境のディレクトリ内でGemfileを探すためには、findコマンドを使用すると便利です。以下のコマンドは、現在のディレクトリから始めて全てのサブディレクトリを検索し、Gemfileという名前のファイルを見つけるものです：

```bash
find . -name Gemfile
```

ここで、.は現在のディレクトリを表し、-nameオプションは探すファイルの名前を指定します。
このコマンドを実行すると、全てのGemfileのパスがリスト表示されます。これにより、開発環境内にGemfileが存在する場所を把握することができます。

見つからなかったからやっぱり--localオプションで入れないとダメかも。現在インストールされてるgemのリストとか出せる？
現在インストールされているgemのリストを表示するには、gem list コマンドを使用します。このコマンドは、インストールされている全てのgemとそのバージョンをリスト表示します：

```bash
gem list
```

また、特定のgemだけを探すには、gem list コマンドに検索パターンを渡します：

```bash
gem list ^rails
```

この例では、名前が "rails" で始まる全てのgemを探します。

これらのコマンドは、システム全体のgemリストを表示します。特定のアプリケーションにバンドルされているgemのリストを表示するには、アプリケーションのルートディレクトリで bundle list コマンドを実行します。ただし、Gemfileが見つからないとのことなので、このケースでは gem list を使用するのが適切でしょう。

### 拡張子tgzってどうやって解凍すればいいの？

.tgzファイルは、TarとGzipを使用してアーカイブと圧縮が行われたファイルです。これはUNIXおよびLinuxシステムで広く使用されています。

.tgzファイルを解凍するには、以下のコマンドを使用します：

```bash
tar -xvzf file.tgz
```

ここで：
-xは「解凍」を意味します。
-vは「詳細モード」を意味し、解凍の進行状況を表示します。
-zはGzipで圧縮されたアーカイブを解凍することを指定します。
-fは解凍するファイル名を指定します。
file.tgzの部分には、解凍するファイルの正確な名前を入力します。これにより、.tgzファイルが解凍され、中に含まれるファイルやディレクトリが現在のディレクトリに展開されます。

### make installしたrubyを再インストールするためにmake uninstallしようとしたらno rule to make target uninstallって出た

make uninstallコマンドは、ソフトウェアをソースからビルドした際にそのソフトウェアをシステムからアンインストールするためのものです。しかし、すべてのソフトウェアがmake uninstallターゲットをサポートしているわけではありません。エラーメッセージ "no rule to make target uninstall"は、そのソフトウェア（この場合はRuby）がmake uninstallターゲットをサポートしていないことを示しています。

ソフトウェアがmake uninstallをサポートしていない場合、アンインストールするには手動でファイルを削除する必要があります。Rubyをソースからビルドしてインストールした場合、以下のようなファイルとディレクトリを削除することでアンインストールできます：

/usr/local/lib/ruby
/usr/local/bin/ruby
/usr/local/bin/irb
/usr/local/bin/gem

その他/usr/local/bin/下のRubyに関連するファイル
ただし、これらのファイルとディレクトリはシステムにより異なる場所にインストールされる場合があるため、具体的なパスはmake installを実行した際のログを確認してください。

なお、Rubyの再インストールにはRuby Version Manager (RVM) やrbenvのようなバージョン管理ツールを使用することを推奨します。これらのツールを使用すると、異なるバージョンのRubyを簡単に切り替えたり、システム全体に影響を与えることなく特定のプロジェクトに対して異なるバージョンのRubyを使用したりすることができます。

### zlib入れてるのにzlibのエラーが発生する。gem入れたいんだけど

Rubyやgemをインストールする際にzlibに関連するエラーが発生する場合、Rubyがzlibライブラリを正しく認識できていない可能性があります。これは、Rubyのインストール時にzlibのヘッダーファイルが見つからないため、Rubyがzlibのサポートを組み込むことができない場合によく起こります。
まず、zlibの開発版がインストールされていることを確認しましょう。Ubuntuの場合は以下のコマンドで確認できます：

```bash
sudo apt-get install zlib1g-dev
```

次に、Rubyのビルドを行う前に、./configureコマンドを使って、Rubyがzlibを正しく認識するように設定します：

```bash
./configure --with-zlib-dir=/usr/include
make
sudo make install
```

--with-zlib-dirオプションにはzlibのヘッダーファイルが格納されているディレクトリを指定します。大抵のLinuxディストリビューションでは、/usr/includeディレクトリにヘッダーファイルが格納されていますが、システムによっては異なる場所に存在することもあります。ヘッダーファイルの場所はzlib.hを検索して特定できます：

```bash
find / -name zlib.h
```

これらの手順を踏むことで、Rubyがzlibを認識し、gemのインストールが可能となるはずです。

unrecognized optionって出るね

すみません、私の説明が不足していました。./configure --with-zlib-dir=/usr/includeコマンドは一部のソフトウェアで使用可能ですが、Rubyのconfigureスクリプトでは使用できません。

Rubyがzlibを見つけられない場合、その原因となる可能性がいくつかあります。

zlibがインストールされていない。

zlibがインストールされているが、そのパスが検索パスに含まれていない。

まず、以下のコマンドを使ってzlibがインストールされているか確認しましょう。

```bash
sudo apt-get install zlib1g zlib1g-dev
```

これにより、zlibライブラリとその開発用パッケージがインストールされます。

次に、Rubyを再インストールします。通常、./configureスクリプトはシステムにインストールされているライブラリを自動的に検出するはずです。もし問題が解決しない場合は、./configureのオプションに問題がある可能性があります。

./configureのオプションを確認するには、以下のコマンドを実行します。

```bash
./configure --help
```

これにより、有効なオプションとその説明が表示されます。ここで、zlibに関連するオプションがあるか確認してみてください。

### zlibをインストールしたのにダメっぽい

それは困った状況ですね。Rubyがzlibを認識できないと、gemのインストールが困難になります。次の手順で問題を解決できるか試してみてください：

Rubyのソースコードを再ダウンロードします。
ソースコードがあるディレクトリに移動します。
ext/zlibディレクトリに移動します。これはRubyのソースコードに含まれるzlibの拡張です。

以下のコマンドを順に実行します：

```bash
ruby extconf.rb
make
sudo make install
```

これにより、Rubyがzlibを認識するための拡張がビルドされ、インストールされます。これを行った後で、Ruby全体のビルドとインストールを再度行ってみてください。

なお、この手順を行うためにはRubyが一部動作する状態である必要があります。もしRuby自体が全く動作しない状態であれば、Rubyのビルドを成功させるために他の方法を探す必要があります。

### ruby 1.8.6をapt-getで入れてみる

Ubuntuのパッケージマネージャーであるapt-getを使用して特定のバージョンのRubyをインストールするには、以下のようなコマンドを使用します：

```bash
sudo apt-get install ruby1.8
```

ただし、apt-getでインストールできるRubyのバージョンはUbuntuのバージョンやリポジトリの状態によります。もしリポジトリにRuby 1.8.6がない場合、それはUbuntuのバージョンが新しすぎて古いRubyのバージョンをサポートしていない可能性があります。

そういった場合、Rubyをソースからビルドしてインストールするか、rbenvやRVMのようなバージョン管理ツールを使用することを検討してみてください。これらのツールを使用すれば、さまざまなバージョンのRubyを簡単にインストールし、管理することができます。

### バージョン1.8.7が入ってしまった。1.8.6を指定したい

Ubuntuのパッケージマネージャであるapt-getは、具体的なマイナーバージョン（例：1.8.6）までの指定はできません。パッケージ名としてruby1.8を指定すると、利用可能な最新の1.8.xバージョンがインストールされます。つまり、1.8.7がインストールされたということは、Ubuntuのリポジトリでは1.8.7が最新の1.8.xバージョンであり、1.8.6を直接インストールすることはできないということです。

このような場合、以下の方法を検討してみてください：

ソースコードからビルドする：Rubyの公式ウェブサイトから1.8.6のソースコードをダウンロードし、手動でビルド・インストールします。ただし、この方法は技術的な知識を必要とし、また依存関係を手動で管理する必要があります。

Rubyのバージョン管理ツールを使用する：rbenvやRVMのようなツールを使用すると、複数のRubyのバージョンを同時に管理し、それぞれに対して異なるgemセットを持つことができます。これらのツールは、指定したバージョンのRubyを自動でダウンロードし、ビルド・インストールします。以下はrbenvを使用してRuby 1.8.6をインストールする例です：

```bash
rbenv install 1.8.6
rbenv global 1.8.6
```

ただし、これらのツールをインストール・使用するには初めての場合はある程度の設定が必要です。また、非常に古いRubyのバージョンを使用すると、現在のシステムやライブラリとの互換性に問題が生じる可能性もありますので、注意が必要です。