# README
ブログ用に用意したタスクランナーのリポジトリです。
## 主要な機能
- 画像自動圧縮
- メタ言語を利用した効率的な開発
- Sassコンパイル
- ベンダープレフィックス自動付与
- CSSプロパティ自動並び替え
- メディアクエリを１つにまとめる
- メタ言語保存時に、コンパイル後のHTMLとCSSを解析する
- あらかじめエラーを通知しておくことで、意図しないスタイル崩れを防止


##### 対象ブラウザについて
[browserslist: A page to display compatible browsers from a browserslist string.](https://browserl.ist/)
ベンダープレフィックス自動付与する各ブラウザのバージョン。
```
//package.json
"browserslist": [
  "Last 5 Safari versions",
  "Last 5 iOS versions",
  "Last 5 Chrome versions",
  "Last 5 ChromeAndroid versions",
  "IE 11",
  "Last 5 Edge versions",
  "Last 5 Firefox versions",
  "Last 5 FirefoxAndroid versions"
],
```


##### stylelintについて
```
"_comments":{
  "plugin/declaration-block-no-ignored-properties":"inlineにmarginをつけるなど、不要な記述を検出するプラグイン",
  "plugin/no-unsupported-browser-features":"サポートが不十分なプロパティがある場合、対象とブラウザを検出するプラグイン。通知を減らすためにignoreしてあるルールがあるのでチェックしておく",
  "length-zero-no-unit":"0pxや0%は0と記述",
  "declaration-block-no-duplicate-properties":"同ルールセット内に重複したプロパティを許可しない",
  "font-family-no-missing-generic-family-keyword": "font-familyの最後にsans-serifかserifかが必要",
  "declaration-block-no-shorthand-property-overrides":"ショートハンドの後に値を上書きするのを許可しない",
  "no-duplicate-selectors":"重複したセレクターを許可しない",
  "value-no-vendor-prefix":"ベンダープレフィックスを許可しない。後でAutoPrefixerでまとめてつけるから",
  "selector-list-comma-newline-after":"グループセレクタを改行しない"
},
```

## インストール
### ダウンロード
1. 本ディレクトリをDL
2. コマンドラインで保存フォルダへcd
3. パッケージをインストールする
```
npm i
```

## フォルダ階層
<pre>
dist
┠ 案件A
┗ 案件B
src
┠ 案件A
┗ 案件B
</pre>

### src : 作業フォルダ
<pre>
src
┗ 案件A
   ┗ ejs
      ┠ under  
      　　┗　index.ejs : 下層CSSコーディング用。BS案件でのparts.htmlと用途は同じ。
      ┠ widgets
         ┠　_copyright.ejs : コピーライトウィジェット
         ┠　_footer.ejs : フッターウィジェット
         ┠　_header.ejs : ヘッダーウィジェット
         ┠　_javascript.ejs : HOME固定ページカスタムフィールド
         ┠　_main.ejs : HOME固定ページ
         ┠　_mainimage.ejs : HOME固定ページカスタムフィールド
         ┠　_nav.ejs : ナビウィジェット
         ┗　_side.ejs : サイドウィジェット
      ┗ index.ejs : 各ウィジェット読み込み
      
   ┗ img : スライスをここに入れる
   
   ┗ css : slick.cssなどライブラリ用のcssファイル
   
   ┗ js : 案件によってjsファイルが違うときは入れ替える
   
   ┗ scss
      ┠ abstract ※1
         ┠ _color.scss
         ┠ _mixin.scss
         ┗ _setting.scss : 各種設定
      ┠ base
         ┗ _base.scss : 要素セレクタへのスタイル
      ┠ component 
         ┗ 略 ※2
      ┠ layout ※3
      ┠ utility ：利便性のために定義した具体的なルールセット
      
      ┗ _custom.scss : TOPコーディング用
      ┗ common.scss
      ┗ style.scss
      ┗ index.scss
   ┗ gulprun.bat : gulp実行
</pre>

## 備考
### stylelintルールに合わせて、エディタ側でscssをオートフォーマットする。
prettier-stylelintプラグインを入れてあります。
VS Codeでしか調べていませんが、以下のURLに詳しい説明があります。
[VS Code で Prettier と Stylelint を連携して CSS/SCSS ファイル保存時にオートフォーマットをかける - Qiita](https://qiita.com/tkiryu/items/016aa9ef8a25b631e7e6)
