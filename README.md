 <br>
 
 # Outline

コーディングの際、迷うと品質とスピードの両方が失われます。  
本ガイドラインは、迷っている時間を少なくし、品質とスピードを一定に保つためのものです。   

あくまで心得の様なもので、この型に合わせる必要はなく、臨機応変にカスタマイズして良いです。  
その為、常にガイドラインは変化（バージョンアップ）します。 

<br>
マークダウン方式についてはこちらを確認してください。
<br>
https://gist.github.com/mignonstyle/083c9e1651d7734f84c99b8cf49d57fa


 
 <br>
 <br>
 
# コーディングの定義
### 基本
+ 予測しやすい
+ 再利用しやすい
+ 保守しやすい
+ 拡張しやすい

 以上4つが CSS Architecture で提唱された「良いcss」 の定義です。  
 これらが保たれているかを念頭においてコーディングしてください。



 <br>
 
# Directory
```
root/
	├ include/
	
	│	├ functions.php
	│	├ meta.php
	│	├ js.php
	│	├ loading.php
	│	├ preload-svg.php
	│	├ header.php
	│	├ footer.php
	│	├ aside.php
	│	└ header.php
	├ assets/
	│	├ img/
	│	│	├ common/
	│	│	├ meta/
	│	│	└ ページ名/
	│	├ svg/
	│	├ css/
	│	│	├ common.min.css
	│	│	├ theme-ページ名.min.css
	│	│	├ wp-admin.min.css
	│	│	├ wp-editor.min.css
	│	│	└ wp-login.min.css
	│	├ js/
	│	│	├ library.js
	│	│	├ module.min.js
	│	│	├ common.min.js
	│	│	├ theme-ページ名.min.js
	│	│	├ component-コンポーネント名.min.js
	│	│	└ wp-admin.min.js 
	│	├ font/
	│	└ pdf/
	├ wp/
	├ ページ名/
	└ index.php
```

## assets
-img -- imgタグで出力する画像を格納。common,meta以外は、ページ名でディレクトリを作る。
-svg -- インラインで仕様するsvgを格納
-font -- フォントをディレクトリ単位で格納
-pdf -- PDFを格納


## css
- common.min.css -- ページ共通のcssファイル
- theme-ページ名.min.css --  ページ固有のcssファイル
- wp-admin.min.css --  WordPressの全ユーザの管理画面用cssファイル
- wp-editor.min.css --  WordPressの編集者の管理画面用cssファイル
- wp-login.min.css --  WordPressのログイン画面用cssファイル
※themeが少ない場合は、commonと合わせても問題ない


## JavaScript
- library.js -- 外部ライブラリを集めたJavaScriptファイル（圧縮なし）
- module.min.js -- 自作プラグインを集めたJavaScriptファイル
- common.min.js -- ページ共通のJavaScriptファイル
- theme-ページ名.min.js -- ページ固有のJavaScriptファイル
- component-コンポーネント名.min.js -- フォームなど部品のJavaScriptファイル
- wp-admin.min.js  -- WordPressの全ユーザの管理画面用JavaScriptファイル
※themeが少ない場合は、commonと合わせても問題ない


 <br>
 
# Common
 
## 命名規則

### 基本
+ 半角英数字のみを使用
+ 記号は「-」（ハイフン）を使用し、ハイフンが使えない場合は「_」（アンダースコア）を使用する
+ 全角スペース、半角スペースは使用しない
 <br>
 
### 画像名
画像のファイル名は、単語間は「_」（アンダースコア）、状態を表す時は「-」（ハイフン）を使用してください。    
例えば、色が違う場合などがこれに当たります。
また、ページや種類ごとでディレクトリ名を変えているので、画像の先頭に top などの ページ名は不要としています。
```
// 例
logo_horizontal-black.svg
logo_horizontal-white.svg
logo_vertical-black.svg

[大内容]_[小内容]_..._[連番]-[状態].[拡張子]
```

### ディレクトリ名
単語間はハイフンを使用してください。  
```
// 例
/about-us/
/portfolio-item/
```

### jsファイル名
キャメルケースを使用してください。  
```
// 例
objectFit.js
isCurrent.js
smoothScroll.js
``` 
 
### 変数名 [JavaScript,php]
スネークケースを使用してください。  
文字の単語間にアンダーバーを使用し、ひと単語が長いなど 単語を読み易くするため 大文字の使用も有りとしています。  
```
// 例
const snake_road = 'hoge';
const snakeBlack_road = 'hoge';
```
 
### 関数名 [JavaScript,php]
キャメルケースを使用してください。  
最初の単語以外の文字の先頭を大文字を使用してください。  
```
// 例
const getWindowHeight = function (){
    // function ...
}
```

また、関数の最初は、なにをしている関数なのかを明確にするため、以下のような文字を使用してください。
| name | description |
----|---- 
| init | 初期化 |
| set | 値を代入する場合に用いる |
| get | データの取得 |
| add | 追加 |
| remove | 削除 |



 <br>
 
<br> 

# Sass
flocssを採用しています。  
https://github.com/hiloki/flocss


## Directory
```
└ sass/
	├ foundation/
	│	├ animation/
	│	├ genetal/
	│	│	├ function/
	│	│	├ mixin/
	│	│	└ variable/
	│	├ base/
	│	│	├ _reset.scss
	│	│	└ _base.scss
	│	├ font/
	│	└ library/
	├ layout/
	├ object/
	│	├ component/
	│	├ project/
	│	├ utility/
	│	├ js/
	│	└ wp/
	├ theme/
	│	└ _pagename.scss
	├ ua/
	├ wp-admin.scss
	├ wp-editor.scss
	├ wp-login.scss
	└ common.scss
```
- foundation -- プロジェクトにおける基本的なスタイルを定義します
	- animation -- アニメーションを定義します
	- general -- mixinや変数など、プロジェクト全体で使用するスタイルを定義します
		- function -- 関数をファイル別で定義します。
		- mixin -- mixinをファイル別で定義します。
		- variable -- 変数をファイル別で定義します。
	- font -- アニメーションを定義します
	- base -- フォントの読み込みがある場合、定義します。
	- library -- jsの外部プラグインでcssがある場合は、拡張子をscssに変えて定義します。
- layout -- ページを構成するスタイルを定義します。
- object -- 繰り返し使用できるスタイルを定義します
	- component -- 再利用できるパターンとして、小さな単位のモジュールを定義します。
	- project -- 複数のcomponentからなる、もしくはsection単位などの大きな単位のモジュールを定義します。
	- utility -- わずかなスタイルの調整のための便利クラスなどを定義します。
- theme -- objectには属さない、ページ固有のスタイルを定義します。
- ua -- UserAgentを使用し、ブラウザや端末などでスタイルを時に定義します。



## themeについて
objectは、繰り返し使用できるスタイルで、ページ固有のスタイルを定義する場所がないです。  
そのため、sassディレクトリ直下にthemeディレクトリを追加し、そこをページ固有のスタイルを定義するディレクトリにします。  
pageという名前が良かったのですが、projectのpとかぶっているためthemeにしています。



## クラス名
クラスは、flocssをbaseに使っています。
ただ、状態を表すものについては、クラスが長くなってしまうのを防ぐ為、ハイフンから始めて良いものとしています。

```
<p class="c-btn c-btn-black">
 <!-- 通常はこれですが -->
</p>

<p class="c-btn -black">
 <!-- これも有りです -->
</p>
```
```
.c-btn{
 &.-black{
  /* style */
 }
}
```



<br> 

# JavaScript


