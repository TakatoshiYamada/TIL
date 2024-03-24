# Open3

Rubyの標準ライブラリに含まれる Open3 モジュールは、外部コマンドを実行するためのメソッドを提供しており、その実行に関する標準出力、標準エラー出力、ステータスコードなどを取得することができます。

このモジュールは、プログラムからシェルコマンドを安全に実行するために使用され、Kernel#system や %x{...} よりも詳細な制御が可能です。
例えば、標準出力と標準エラー出力を別々にキャプチャしたり、プロセスの終了を待つことなく非同期に実行したりすることができます。

Open3 モジュールは次のようなメソッドを含みます:

- popen3: 標準入力、標準出力、標準エラー出力のためのパイプとプロセスIDを提供します。
- capture3: コマンドの標準出力と標準エラー出力をキャプチャし、プロセスの終了ステータスを返します。
- capture2: 標準出力のみをキャプチャします。
- pipeline_start, pipeline_rw, pipeline: 複数のコマンドをパイプラインで実行するためのメソッドです。

例:

```ruby
require 'open3'

stdout, stderr, status = Open3.capture3("ls -l")

puts stdout  # ls コマンドの結果が出力される
puts stderr  # エラーメッセージがあれば出力される
puts status  # プロセスの終了ステータスオブジェクトが出力される
```

このモジュールは、外部プロセスの実行が必要な場合、特にセキュリティや詳細な制御が必要なスクリプトやアプリケーションで非常に有用です。

## 具体的に使われるイメージが湧かない

Open3 モジュールを使用する典型的なシナリオを考えてみましょう。
例えば、Ruby スクリプトから画像を処理する外部プログラム（convert コマンドなど）を呼び出して、その結果を扱いたいとします。

以下のコードは convert コマンドを使用して画像のサイズを変更し、その出力をキャプチャしてエラーがあるかどうかをチェックする例です。

```ruby
require 'open3'

# convertコマンドでimage.pngをサイズ変更する。
stdout, stderr, status = Open3.capture3("convert", "image.png", "-resize", "100x100", "image_resized.png")

if status.success?
  puts "画像が正常にリサイズされました。"
else
  puts "エラーが発生しました: #{stderr}"
end
```

このコードでは、convert コマンドに必要な引数を capture3 メソッドに渡しています。
プログラムが正常に終了したかどうかを status オブジェクトでチェックし、エラーメッセージがあればそれを出力します。

Open3 は、特にシステムの環境やデータにアクセスする際に、セキュリティやエラーハンドリングの観点から、シェルを経由せずに直接コマンドを実行したい場合に非常に便利です。
また、プログラムの出力をリアルタイムで処理する必要があるときや、出力を他のRubyメソッドでさらに処理したい場合にも役立ちます。

## 話変わるけどconvertコマンドって何

convert コマンドは、ImageMagickというプログラムの一部です。
ImageMagickは、画像を作成、編集、または変換するためのソフトウェアスイートで、多くのファイル形式に対応しています。

convert コマンドを使うと、コマンドラインから直接画像のリサイズ、形式変換、色変換、複雑なエフェクトの適用など、様々な画像処理操作を実行できます。
例えば、JPEG形式の画像をPNG形式に変換する、画像のサイズを変更する、画像を回転させるといったことが可能です。

以下は、convert コマンドの基本的な使用例です。

画像の形式を変更する場合:

```sh
convert picture.jpg picture.png
```

画像のサイズを変更する場合:

```sh
convert picture.jpg -resize 100x100 picture_small.jpg
```

ImageMagickは非常に強力で、コマンドラインツールとしてだけでなく、APIを介して多くのプログラミング言語から利用することもできます。
そのため、ウェブサーバーで自動的に画像を処理するスクリプトを書くときなど、開発者にとって重宝されるツールの一つです。