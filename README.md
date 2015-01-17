# Yatex commands

## タイプセット（ビルド，コンパイル）

``` bash
Ctrl-c Ctrl-t j
```
## section型補完（sectionとか）

```bash
// [Ctrl]押しながら[c]押して[s]を押す
Ctrl-c Ctrl-s
```

その後，下の方に

```bash
(C-v for view-section) \???{}(default documentclass):
```

と出てくるので入れたいものを入力する．
最初の数文字を入れると[Tab]で補完できる．

### section型補完で入力できる主なもの
| 部 | part | |
| 章 | chapter | |
| 節 | section | 使うのはここから|
| 小節 | subsection | |
| 少々節 | subsection | |

## begin型補完（数式や画像、表、リストなど）

```bash
// [Ctrl]押しながら[c]押して[b]を押す
Ctrl-c Ctrl-b [Space]
```

その後，下の方に

```bash
Begin environment(default xxx):
```

と出てくるので入れたいものを入力する．
最初の数文字を入れると[Tab]キーで補完できる．

### begin型補完で入力できる主なもの
| 画像 | figure |
| 数式 | eqnarray |
| 箇条書き | itemize |

画像の挿入に関しては以下のコードをコピペするのが速い．

```tex
\begin{figure}[htbp]
	\begin{center}
		\includegraphics[scale=1]{gazou.pdf}
	\end{center}
	\caption{画像の説明}
\end{figure}
```

## 参照について
例えば図説明文に図番号を振りたいとき．まず以下のように図番号だけ書かずに文章を書き，画像を挿入するコードをコピペしておく．

```tex
図に示すように提案手法は従来手法に比べて処理時間，精度の点において優れている．
\begin{figure}[htbp]
	\begin{center}
		\includegraphics[scale=1]{gazou.pdf}
	\end{center}
	\caption{画像の説明}
\end{figure}
```

図番号を入れたいところにカーソルを合わせてsection型補完を起動して，`ref`と入力する．

```bash
Ctrl-c Ctrl-s
```

```bash
(C-v for view-section) \???{}(default documentclass): ref[Enter]
```

もし`(default documentclass)`が`(default ref)`になっていればそのまま`[Enter]`を押せばおっけい．

下の様にキャプション一覧が出てくるので図番号を参照したいキャプション名の上で[Enter]を押す．

![参照の様子01](./reference_01.png)

すると下の方に

```bash
Give a label for this line: hogehoge
```

と出てくるので[Enter]を押す．これはTeX上で画像を識別するタグのようなもので1つの画像などにユニークに与えられる必要がある．一度設定すれば二回目に同じ画像を参照しても出てこない．
これで無事に参照番号が振られたと思う．これは画像だけでなく，節や数式にも同じように適用できる．おそらくこの機能が`Yatex`を使う上で一番強いので是非使ってほしい．
なお，上手く参照できれば以下のようになるはずだ．
![参照の様子02](./reference_02.png)
