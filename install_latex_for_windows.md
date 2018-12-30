# LaTeXの環境構築 for Windows
## 目次
* [Setup LaTeX](#sec1)
* [Setup Sublime Text 3](#sec2)
* [Setup SumatraPDF](#sec3)
* [See also](#sec4)

<a id="sec1"></a>
<h2> Setup LaTeX </h2>

### TeXインストーラ 3
TeXインストーラ 3は東京大学の阿部紀行さんにより作成されたWindows用の日本語TeXインストーラである．これを実行するだけでlatexを使う上で必要な関連ソフトをひと通りそろえることができる．

### 手順
1. [TeXインストーラ 3](https://www.ms.u-tokyo.ac.jp/~abenori/soft/abtexinst.html)をダウンロードする
2. ファイルを解凍し，実行ファイルを起動する
3. インストーラが起動したら，デフォルトのまま`次へ`を押し続けるだけでOK
4. `latexmk`を使えるようにするためにPerlを入れる→[Strawberry Perl](http://strawberryperl.com/)

#### Perlを入れないと...
`latexmk`を実行するときに`Script interpreter is not found in PATH.`というエラーが出る

<a id="sec2"></a>
<h2> Setup Sublime Text 3 </h2>

### 手順
1. [Sublime Text 3](https://www.sublimetext.com/3)をインストール
2. [Package Control](https://packagecontrol.io/installation)を入れる
3. [LaTeXTools](https://latextools.readthedocs.io/en/latest/)をPackage Controlでインストールする
4. Sublimeのメニュー **Preferences→Package Settings→LaTeXTools→Settings User**で以下を`LaTeXTools.sublime-settings`に追加する

		```
		"builder_settings" : {

		        // General settings:
		        // See README or third-party documentation

		        "command" : ["latexmk", "-cd",
		                "-e", "$latex = 'platex %O -no-guess-input-enc -kanji=utf8 -interaction=nonstopmode -synctex=1 %S'",
		                "-e", "$biber = 'biber %O --bblencoding=utf8 -u -U --output_safechars %B'",
		                "-e", "$bibtex = 'pbibtex %O %B -kanji=utf8'",
		                "-e", "$makeindex = 'upmendex %O -o %D %S'",
		                "-e", "$dvipdf = 'dvipdfmx %O -o %D %S'",
		                "-f", "-%E", "-norc", "-gg", "-pdfdvi"],

		                									.
		                									.
		                									.
		},
		```

5. 日本語入力用に[ConvertToUTF8](https://github.com/seanliang/ConvertToUTF8)と[IMESupport](https://github.com/chikatoike/IMESupport)をPackage Controlでインストールする
6. 補完機能を追加するために[LaTeX-cwl](https://github.com/LaTeXing/LaTeX-cwl)をPackage Controlでインストールする

<a id="sec3"></a>
<h2> Setup SumatraPDF </h2>

### 手順
1. [SumatraPDF](https://www.sumatrapdfreader.org/free-pdf-reader.html)をインストール
2. 逆順検索を有効にするため，SumatraPDFのメニューから「設定→オプション」を選択．ウィンドウの「逆順検索コマンドラインの設定」に，以下のように入力．Sublimeのパスを変更している場合はそのパスに変更する必要がある．`"C:\Program Files\Sublime Text 3\sublime_text.exe" "%f:%l"`

<a id="sec4"></a>
<h2> See also </h2>

* [TeX Wiki](https://texwiki.texjp.org/?Microsoft%20Windows)