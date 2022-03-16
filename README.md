# 南臺科技大學碩博士 LaTeX 論文模板

## 前言

鑑於各系或是實驗室產出的論文排版品質不一，導致後續的學弟妹們參考時很是迷惘。

為此，本模板將以學校釋出的[論文模板](./texmf/doc/THESIS_example.pdf)作為準則，並使用 LaTeX 排版，不必再煩惱論文排版的設定。

若想進一步了解各檔案的用途可參考[此說明檔](./purpose.md)。

## 行前準備

請依本身的作業系統安裝以下套件：

- texlive
- make

```bash
# Debian
apt-get install texlive \
	texlive-xetex \
	texlive-lang-chinese \
	texlive-bibtex-extra \
	texlive-science \
	texlive-publishers \
	latex-cjk-all \
	ttf-mscorefonts-installer	# For 'Times New Roman'
```

### 字型

本模板總共使用兩種字型，請依自身的作業系統分別安裝:
- 英文: Times New Roman
- 中文: 國發會提供的[全字庫正楷體](https://data.gov.tw/dataset/5961)，位於本資料夾中的 `texmf/fonts/truetype`，此字體渲染效果最好。

```bash
# Methods below supports GNU/Linux
$ make font.check				# 檢查全字庫正楷體是否已安裝
$ sudo make font.install			# 以root權限安裝全字庫正楷體
```

## 使用方法

- 手動編譯，順序為 ``xelatex → bibtex → xelatex``

- 自動編譯，請於本資料夾中使用 `make` 工具編譯 `main.tex` ， 即可產出論文 `main.pdf` 。

以下為自動編譯的使用範例：

```bash
$ make tex.build 				# 編譯主檔案 (xelatex)
$ make tex.all					# 編譯主檔案及參考文獻 (xelatex → bibtex → xelatex)
```

若需清除緩存檔案(caches)，可使用以下命令：

```bash
$ make tex.clean				# 清除緩存檔案
$ make tex.distclean				# 清除所有緩存檔案及**output資料夾中所有檔案**
```

## 開始撰寫

> 若是第一次接觸 LaTeX 可參考 [大家來學LATEX](https://jupiter.math.nctu.edu.tw/~smchang/latex/latex123.pdf) ， 非常推薦大家拜讀由李果正先生所撰寫的說明文件。

### 論文相關資訊

請編輯 `information.tex` 中的：

```tex
% Usage : \info{English}{Chinese}
%% 大學
\university{Southern Taiwan University of Science and Technology}{南臺科技大學}
%% 系所
\institute{Electronic Engineering}{電子工程系}
%% 學位
\degree{master}{碩士}
%% 論文主題/題目
\title{Thesis Template in \LaTeX{} for STUST}{南臺科技大學碩博士 \LaTeX{} 論文模板}
%% 作者/學生
\author{Your name}{你的名字}
%% 學號
\stuID{MAXXXXXX}
%% 指導教授
\advisor{Advisor}{指導教授}
%% 所長/系主任
\director{Director}{系主任}
%% 西元/民國 年月日
\year{2021}{一一〇}
\month{07}{七}
\day{15}{十五}
```

只需輸入一次，相關資訊將會用至**封面頁**、**書名頁**、**書脊頁**中。

### 自定義環境

本模板已定義中英文的**摘要(abstract)**、**致謝(acknowledgements)**、**符號彙編(symbols)**環境，以摘要為例，用法如下：

```tex
% Abstract
\begin{abstract}{cht}

    這是中文摘要。

    \keywords[cht]{摘要、\LaTeX{}、模板}

\end{abstract}

\begin{abstract}

    This is abstract of english version.

    \keywords{abstract, \LaTeX{}, template}

\end{abstract}
```

- `\begin{abstract}{cht}` → 多加 `{cht}` 代表該環境的章節標題已設定為繁體中文，也就是 `摘要`
- `\begin{abstract}` → 則設定為英文： `Abstract`
