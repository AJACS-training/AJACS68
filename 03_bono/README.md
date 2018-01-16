# 遺伝子発現DBをはじめとした公共オミックスDBの使い方 at AJACS浜松

情報・システム研究機構 データサイエンス共同利用基盤施設 ライフサイエンス統合データベースセンター  
[坊農 秀雅](http://dbcls.jp/~bono/) bono@dbcls.rois.ac.jp  
2018年1月16日


----

これは統合データベース講習会AJACS浜松「遺伝子発現DBをはじめとした公共オミックスDBの使い方」の資料です。

----

## 概要

本講習は、だれでも自由に使うことができる公共DBやウェブツールを活用して、研究のさまざまな場面で調べることの多い個々のオミックスDBを簡単に調べるための方法と基礎知識について学びます。
とくに、需要の増している公共DBから遺伝子発現データを検索し取得してくる方法について詳しく説明、実習します。
また、自ら行なった大規模発現解析の(あるいは公共DBから取得・解析した)結果として得られた数百〜数千におよぶ遺伝子セットについて、生物学的な解釈をする方法とその結果の考察を実践します。

----

## 講習の流れ
今回の講習では、以下の内容について順番に説明します。【実習】の部分はみんなでやる実習、【応用】は早くできてしまった人用の応用課題です。

- 研究現場で頻繁に使われるDBやツールを知る: 統合TV
- 公共オミックスDBとは
- 公共オミックスDBの使い方
     - EBI ArrayExpress
	     - 【実習1】ArrayExpressを使って、興味ある実験データセットを検索する
     - NCBI Gene Expression Omnibus（GEO）
     - AOE (All of gene expression)
		 - 【実習2】AOEを使って、興味ある実験データセットを絞り込む
-  個々の遺伝子の発現プロファイルなどを調べる
    - 【実習3】RefExを使って、組織特異的遺伝子を検索する
    - 【応用1】ChIP-Atlasを使って注目の遺伝子がコードされたゲノム領域にあるChIP-seqピークを検索する
- 数十～数千の遺伝子群の生物学的解釈
    - 【実習4】metascapeを用いて、発現データの結果を生物学的に解釈する
    - 【応用2】複数のエンリッチメント解析ツールを用いて、発現データの結果を生物学的に解釈する
----

### 講習に際しての注意とお願い

- みんなで同時にアクセスするとサイトにつながりにくくなることが予想されます。
    - 資料を見ながら自力で進められそうな方はどんどん先に、そうでない方は講師と一緒にすすめていきましょう。
    - サイトの反応が悪い時はタイミングをずらして実行してみてください。
    - 反応が無いからと言って何度もクリックするとますます繋がらなくなってしまいます。おおらかな気持ちで臨みましょう。
- わからないことがあったら挙手にてスタッフにお知らせください。
    - 遠慮は無用です(そのための講習会です!)。おいてけぼりは楽しくありません。
- 実験的な試みとしてWeb上で匿名で質問・コメントできるフォームを用意してみました。
  - [講師用](https://docs.google.com/presentation/d/19CsrlyrT1hdrmPVnS4R7uUveOgHfN5IqPK-kt8WLCHw/edit?usp=sharing)
  - [受講者質問用フォーム](https://goo.gl/slides/jnrta2)(右クリックから「新しいタブで開く」推奨)

----

## 研究現場で頻繁に使われるデータベースやツールを知る
### [統合TV](http://togotv.dbcls.jp/)
- 生命科学分野の有用なデータベースやツールの使い方を動画で紹介するウェブサイト
    - http://togotv.dbcls.jp/ [![https://gyazo.com/acd9a661ebb043e62cc50176d6ad69ca](https://i.gyazo.com/acd9a661ebb043e62cc50176d6ad69ca.png)](http://togotv.dbcls.jp/)
    - YouTube版もあります　http://youtube.com/togotv/
    - ウェブサイトへのアクセスから結果の見方まで、操作の一挙手一投足がわかります。
        - 講義・講習などの参考資料や後輩指導の教材として利用できます。
        - 本講習中、本家サイトが繋がらない時は、統合TVのYouTube版を見ればおおよその内容がわかるようになっています。
        - 今回の講習に関連する内容の多くは、「発現解析」タグのついた動画にあります。
        - 過去の講習会の内容はそのほとんどが統合TVに収録されており、いつでもどこでも繰り返し復習できるようになっています。
    - お探しの動画が見つからない or 統合TV未掲載の場合は、[統合TV番組リクエストフォーム](http://togotv.dbcls.jp/ja/contact.html)へどうぞ!
    - [統合TVを作ってくれる方、募集中!!](https://twitter.com/bonohu/status/747954940157399040)

----

## 公共オミックスDBとは
### mind the gap
遺伝子発現解析などのオミックス解析→DB(というか、公共アーカイブ)に登録

- 日本では論文投稿前が現在一般的
- 欧米では研究費の条件で多くの場合データを出したらわりとすぐ

### その歴史
- マイクロアレイの発明→網羅的遺伝子発現定量が可能に→遺伝子発現DB
	- アレイのイメージデータ(CELファイルなど)
	- 定量データ(Series Matrix File)
- マイクロアレイのデータベース
  - [DDBJ CIBEX](http://cibex.nig.ac.jp/) (更新停止) → 2018年、DDBJ Omics Archive(DOR)として仕切り直し
  - [NCBI Gene Expression Omnibus（GEO)](http://www.ncbi.nlm.nih.gov/geo/)
  - [EBI ArrayExpress](http://www.ebi.ac.uk/arrayexpress/)
    - ArrayExpressはGEOのデータを定期的に取り込み続けていた→こちらの使用を推奨していた→2017年に取り込み停止。
- 次世代シークエンサー(NGS: Next Generation Sequencer)の発明→個々のサンプルでのtranscript sequencing (RNA-seq)が現実的に
	- データはNGS配列DB(SRA: Sequence Read Archive) and/or 遺伝子発現DBへ?
	- NCBI,EBIでは遺伝子発現DB(それぞれGEO,ArrayExpress)に登録すれば、配列データ(FASTQファイル)がSRAにも登録される状況
		- DDBJ(日本)もその仕組みを現在構築中（上述のDOR）
	- 現状、どこかの公共DBに登録されていればOK

### 発現定量のステップ
#### マイクロアレイ
[![https://gyazo.com/a5ea2e97d8fb84e7f21ecc1bb4b878cb](https://i.gyazo.com/a5ea2e97d8fb84e7f21ecc1bb4b878cb.png)](https://gyazo.com/a5ea2e97d8fb84e7f21ecc1bb4b878cb)

#### NGS(RNA-seq)
[![https://gyazo.com/fe4394bafcd3900a9d568292a0a19b8f](https://i.gyazo.com/fe4394bafcd3900a9d568292a0a19b8f.png)](https://gyazo.com/fe4394bafcd3900a9d568292a0a19b8f)

 - データ解析の流れは、[Dr.Bonoの生命科学データ解析](https://www.medsi.co.jp/books/products/detail.php?product_id=3588) p174-p181を参照
 [![drbonobon](https://www.medsi.co.jp/books/upload/save_image/09271003_59caf8cb2985a.jpg)](https://www.medsi.co.jp/books/products/detail.php?product_id=3588)

 - 詳しい手順は、[次世代シークエンサーDRY解析教本「Level2② 発現解析」](https://github.com/AJACS-training/AJACSa2)p97-141などを参考に

  [![http://gakken-mesh.jp/book/detail/9784780909203.html](http://gakken-mesh.jp/images/goods_img/14158092001.jpg)](http://gakken-mesh.jp/book/detail/9784780909203.html)

----

## 公共オミックスDBの使い方

### EBI ArrayExpress

- EBIが提供・維持管理している遺伝子発現情報のデータベース
	- http://www.ebi.ac.uk/arrayexpress/
	- NCBI GEOのデータも取り込んでいて、こちらのほうがデータ数が多い
  	- が、2017年10月にそれを止めるとアナウンス
	- インターフェースが使いやすい

#### 【実習1】ArrayExpressを使って、興味あるマイクロアレイの実験データセットを検索する
1. [ArrayExpressのサイト](http://www.ebi.ac.uk/arrayexpress/)にアクセス、検索窓に'cancer'と入力
[![https://gyazo.com/c0cf9c24aff417fa51d24fc645f76f31](https://i.gyazo.com/c0cf9c24aff417fa51d24fc645f76f31.png)](https://gyazo.com/c0cf9c24aff417fa51d24fc645f76f31)

2. 候補となるキーワードがいろいろ出てきました。cancerの左にある'＋'をクリックして解いてみましょう
[![https://gyazo.com/2e716af19911031e5ba8eba07d1dad37](https://i.gyazo.com/2e716af19911031e5ba8eba07d1dad37.png)](https://gyazo.com/2e716af19911031e5ba8eba07d1dad37)

3. 今回はそのまま'Search'ボタンを押して、cancerで検索してみます
4. 黄色でハイライトされた'cancer'以外に、オレンジ色でcancer関係のキーワードもハイライトされているのを確認しましょう
[![https://gyazo.com/ae8fe04aad31e08c299ede4e25d131de](https://i.gyazo.com/ae8fe04aad31e08c299ede4e25d131de.png)](https://gyazo.com/ae8fe04aad31e08c299ede4e25d131de)

5. 単にcancerではヒット数が多いので、'oral cancer'で検索してみましょう
[![https://gyazo.com/8192a0e6a879f679e79203bff1f65a15](https://i.gyazo.com/8192a0e6a879f679e79203bff1f65a15.png)](https://gyazo.com/8192a0e6a879f679e79203bff1f65a15)

6. デフォルトでは'Released'(データの公開日)が新しいものから古いもの順にならんでいます。'Views'(閲覧数)をクリックして並べ替えてみましょう
[![https://gyazo.com/42740cf9772175e373ac4c81dafcfc31](https://i.gyazo.com/42740cf9772175e373ac4c81dafcfc31.png)](https://gyazo.com/42740cf9772175e373ac4c81dafcfc31)

7. 詳細を見るには'Accession'のリンクをクリックします。[番号の意味はこちらを参照](http://www.ebi.ac.uk/arrayexpress/help/accession_codes.html)
[![https://gyazo.com/2151dac0cce22ae9db7eb8814f72ea45](https://i.gyazo.com/2151dac0cce22ae9db7eb8814f72ea45.png)](https://gyazo.com/2151dac0cce22ae9db7eb8814f72ea45)


8. ブラウザのバックボタンで戻ります。'Title'には研究内容のタイトル、'Type'には実験の種類、'Organism'には生物種が書かれています
[![https://gyazo.com/42740cf9772175e373ac4c81dafcfc31](https://i.gyazo.com/42740cf9772175e373ac4c81dafcfc31.png)](https://gyazo.com/42740cf9772175e373ac4c81dafcfc31)

9. 'Processed'にアイコンがあるものは解析済みデータがあることを、'Raw'にアイコンがあるものは生データがダウンロード可能であることを示しています
10. アイコンが下向き矢印のものは直接ダウンロードが始まり、クリップのものはダウンロードのできるサイトにジャンプします
[![https://gyazo.com/1ba9b3841322ccfb0836ae4baf01ee40](https://i.gyazo.com/1ba9b3841322ccfb0836ae4baf01ee40.png)](https://gyazo.com/1ba9b3841322ccfb0836ae4baf01ee40)

11. ブラウザのバックボタンで戻ります。'Atlas'にアイコンがあるものは[Expression Atlas](https://www.ebi.ac.uk/gxa/)にデータが収録されていることを示しています。
[![https://gyazo.com/29b979ffee1e1605a6a8cd023af0639a](https://i.gyazo.com/29b979ffee1e1605a6a8cd023af0639a.png)](https://gyazo.com/29b979ffee1e1605a6a8cd023af0639a)

12. 自分の研究テーマに近い、また興味のあるマイクロアレイデータが利用可能か検索してみましょう。

----

### NCBI Gene Expression Omnibus（GEO)
- NCBIが提供・維持管理している遺伝子発現情報（主にマイクロアレイ）のデータベース
  - [https://www.ncbi.nlm.nih.gov/geo/](https://www.ncbi.nlm.nih.gov/geo/)
- 自分の興味のある発現データセットや遺伝子プロファイルを検索することができるだけでなく、それらの生データを自由にダウンロードすることが可能です。
  - GEOのエントリについて（GEO ID番号の最初の3文字の意味）
    - GPL: Platform ー マイクロアレイチップの種類
    - GSM: Sample ー 1枚のマイクロアレイチップから得られたサンプルデータ
    - GSE: Series ー 1つの実験で得られたGSMのセット
    - GDS: DataSet ー NCBIのスタッフが解析可能なデータを集めて再編成したGSMのセット

- [【参考】NCBI GEOの使い方1〜マイクロアレイデータの検索・取得〜 2017](http://doi.org/10.7875/togotv.2017.002)

----

### [AOE(All of gene Expression)](http://aoe.dbcls.jp/)
- 遺伝子発現用のデータ目次
	- 年ごと、生物種ごとにヒストグラム表示
- http://AOE.dbcls.jp/
- マイクロアレイ(Affymetrix,Agilent,それ以外) ＋ RNA-seq(Illumina,それ以外)でデータが分類
- キーワード検索結果もヒストグラム表示されてわかりやすい

----

#### 【実習2】AOEを使って、低酸素関連遺伝子発現データを検索する



 1. http://AOE.dbcls.jp/ にアクセスします
  [![https://gyazo.com/e8c76144beb593e1e0d4333011e1360f](https://i.gyazo.com/e8c76144beb593e1e0d4333011e1360f.png)](https://gyazo.com/e8c76144beb593e1e0d4333011e1360f)
 2. 「生物種別登録データランキング」で生物種のところ(8. Escherichia coli)をクリックすると、その生物種だけのデータ登録数に絞りこめます
  [![https://gyazo.com/9aed0048ff42a0fbb525a071aa107f92](https://i.gyazo.com/9aed0048ff42a0fbb525a071aa107f92.png)](https://gyazo.com/9aed0048ff42a0fbb525a071aa107f92)
 3. 「手法別登録データランキング」で赤系の色(4. illuminaと5. Other_NGS)だけクリックして残すと、NGSによる遺伝子発現測定のデータのみに絞りこめます
  [![https://gyazo.com/91e5d31d15c299032965d34292c8d794](https://i.gyazo.com/91e5d31d15c299032965d34292c8d794.png)](https://gyazo.com/91e5d31d15c299032965d34292c8d794)
 4. 上部の検索窓でキーワード(例えば、``hypoxia``)を入れて検索ボタンを押すと、そのキーワードを実験タイトルに含むエントリだけに絞りこめます
 [![https://gyazo.com/fe9cbd7e6990d239d25960fbe89c767f](https://i.gyazo.com/fe9cbd7e6990d239d25960fbe89c767f.png)](https://gyazo.com/fe9cbd7e6990d239d25960fbe89c767f)

[【参考】AOEを使って遺伝子発現データベースの統計を見ながら検索する](http://doi.org/10.7875/togotv.2014.096)

----

## 個々の遺伝子の発現プロファイルを調べる
### [RefEx (Reference Expression dataset)](http://refex.dbcls.jp/)
- ヒト、マウス、ラットの遺伝子発現情報リファレンスデータセット
  - [http://refex.dbcls.jp/](http://refex.dbcls.jp/)
- 4つの異なる実験手法（EST、GeneChip、CAGE、RNA-seq）によって得られた正常組織、初代培養細胞、細胞株における遺伝子発現データを検索、閲覧可能
    - 最近新たに、FANTOM5 CAGEデータが追加(ヒト556種、マウス286種)
    - 掲載しているデータやオリジナルデータなどの詳細については、[RefExについて](http://refex.dbcls.jp/about.php?lang=ja)
- RefExで掲載されているデータはすべて再利用可能
    - 下部の「ダウンロード」からリンク
    - [figshare【統合TV】](http://doi.org/10.7875/togotv.2016.034)というレポジトリにも [doi:10.6084/m9.figshare.c.3812815](https://doi.org/10.6084/m9.figshare.c.3812815)
    - 「RefEx analysis」として論文に引用していただいたケースも
         -  [Aberrant IDH3α expression promotes malignant tumor growth by inducing HIF-1-mediated metabolic reprogramming and angiogenesis, Oncogene, (22 December 2014) | doi:10.1038/onc.2014.411](http://www.nature.com/onc/journal/vaop/ncurrent/full/onc2014411a.html)
- 2017年に論文出ました [doi:10.1038/sdata.2017.105](https://doi.org/10.1038/sdata.2017.105)
- このツールでできること
    - 正常組織における遺伝子発現データを調べる
    - 測定手法による遺伝子発現量の差異を比較する
    - 組織特異的遺伝子をワンタッチで検索可能
    - 遺伝子発現解析などで見出された不詳な遺伝子群の機能および関係性を調べる

----
#### 【実習3】RefExを使って、組織特異的遺伝子を検索する
- [【復習用 統合TV】RefExの使い方](http://doi.org/10.7875/togotv.2014.009)  

 1. http://refex.dbcls.jp/ を開きます。
 2. 画面中央の「組織特異的に発現する遺伝子を見る」の臓器アイコンにカーソルを合わせると、更に詳細な部位のアイコンが出るので、調べたい臓器（例として肝臓）をクリックします。  
 [![Gyazo](http://i.gyazo.com/fab7f0ba81afbce32061692c344bf03f.png)](http://gyazo.com/fab7f0ba81afbce32061692c344bf03f)

 3. 検索結果一覧が表示されます。検索結果一覧では、「ソート項目の切り替え」や「絞り込み検索」、「リストへの追加」ができます。(手順11以降で解説します。)
 4. 各遺伝子の青字の部分（例 [fibrinogen alpha chain](http://refex.dbcls.jp/gene_info.php?lang=ja&db=human&geneID=2243&refseq=NM_000508&unigene=Hs.351593&probe=205649_s_at))をクリックすると詳細情報を閲覧できます。
 [![Gyazo](http://i.gyazo.com/2a250c033aac172fae84b89033e1b225.png)](http://gyazo.com/2a250c033aac172fae84b89033e1b225)

 5. 「ヒートマップ on Bodyparts3D」では、表示する部位の切り替え（全身・体幹部・頭部）ができます。「皮膚・骨格筋を表示」もしくは「アニメーション表示」にチェックを入れるとどのように表示されるでしょうか。
 6. 「組織40分類別データ」では、バーの上にマウスオーバーすると測定部位と発現値が表示されます。
 [![Gyazo](http://i.gyazo.com/b60518629c6dd0fe8163776cc7824a3c.png)](http://gyazo.com/b60518629c6dd0fe8163776cc7824a3c)

 7. 「Download」をクリックすると、表示中の遺伝子の組織40分類別の発現データがタブ区切り形式でダウンロードできます。
 8. 「Probe set ID」のリンク先をクリックすると、どういう情報が参照できるでしょうか。
 [![Gyazo](http://i.gyazo.com/78a17e8253cb9ed64f6becf96b5a1e03.png)](http://gyazo.com/78a17e8253cb9ed64f6becf96b5a1e03)

 9. 遺伝子オントロジー(GO ID)をクリックすると、そのGO termを持つ他の遺伝子を一括で検索できます。
   - 例として、[GO:0007596](http://refex.dbcls.jp/genelist.php?lang=ja&db=human&idkind=1&ids=GO:0007596)   blood coagulation をクリックしてみましょう。
 10. 右側のFANTOM5 CAGEのタブをクリックすると、FANTOM5 CAGEデータのビューアに切り替わります。
   - ビューアは上部が拡大図で、下部が全体表示になっています。
   - 検索窓にキーワードを入れるとサンプル名を検索できます。ヒットしたサンプルはオレンジ色で強調されます。
   - 右側に、サンプル名と発現値、サンプル分類が表示されます。
   - [RefEx用に整理したサンプル情報一覧](http://bit.ly/fantom5cagehuman)も閲覧可能です。
 11. 検索結果一覧に戻ります。ソート項目を切り替えて、どのように結果が変わるでしょうか。
 12. 様々な条件で検索結果を絞り込むことができます。絞り込み検索は左のバーから行えます。
   - 遺伝子名に「liver」を含むデータは何件あるでしょうか。
   - 「遺伝子名」の下の「条件なし」をクリックして表示されるウインドウに「liver」と入力し、「Include」をクリックし、「この条件で絞り込み」を押します。
   - 「遺伝子名」の項目で「Exclude」に「solute」を加えると、検索結果はどう変わるでしょうか。
   - 「組織」の項目で、データ元をRNA-seqに変更したり、臓器の指定を追加すると検索結果はどう変わるでしょうか。
   - 「必ず含むデータセット」の「ALL」にチェックを入れると、検索結果はどう変わるでしょうか。
 13.  個々の遺伝子の詳細情報は、リストに追加することで並列に比較することができます。
   - [肝臓特異的遺伝子の検索結果一覧](http://refex.dbcls.jp/genelist.php?lang=ja&db=human&roku_valid=1&rk[31]=31&order_key=score)に移動して、3つの遺伝子を「リストに追加」してみましょう。
   - 追加した件数は「リストを見る」の横に表示されます。
   - 「リストを見る」をクリックするとリストに移動します。
   - 『並べて表示する』にチェックを入れて、「遺伝子を並べて表示」をクリックします。
   - 並列に比較することで見えてくる「違い」はなんでしょうか。
 [![Gyazo](http://i.gyazo.com/f832aab525efcbd99854b8c920be0fcf.png)](http://gyazo.com/f832aab525efcbd99854b8c920be0fcf)  
 [![Gyazo](http://i.gyazo.com/0c604ddeee80bf4adf14ce52876a5744.png)](http://gyazo.com/0c604ddeee80bf4adf14ce52876a5744)

 14. 自分の研究テーマに関連する、また興味のある遺伝子について検索してみましょう。
----
#### 【応用1】ChIP Atlasを使って注目の遺伝子がコードされたゲノム領域にあるChIP-seqピークを検索する
[ChIP Atlas](http://chip-atlas.org)は公共のChIP-seqデータを再解析することで簡単に公共データを再利用できる仕組みです。

- Peak Browser
  - 例: mouseで、Antigen Classに'TFs and others'、Cell type Classに'Adipocyte'でPparg遺伝子のコードされたゲノム領域を見てみましょう
- Target genes
  - 例1: mouseで、Antigenに'Pparg'
  - 例2: humanで、Antigenに'TP53'

の機能に関して簡単に説明します。

----

## 数十～数千の遺伝子群の生物学的解釈
### [metascape](http://metascape.org/)
- マイクロアレイやRNA-seqデータの生物学的な解釈
- マイクロアレイやRNA-seq、すなわち遺伝子発現解析の一般的な目的は、実験条件によって得られた数十～数千の遺伝子群の発現が生物学的にどういう意味を持つかを考えることです。

[![Gyazo](http://i.gyazo.com/52cb4c40b1313a52f8ded6923bdd8ef0.png)](http://gyazo.com/52cb4c40b1313a52f8ded6923bdd8ef0)

- 今回は、その方法の一つとして、遺伝子リストにある遺伝子群に機能アノテーション(Gene Ontologyなど)を付与し、生物学的な解釈を行います。

#### 遺伝子リストの準備
- サンプルデータとして、公共遺伝子発現データベースからメタ解析してえた遺伝子リストを用います。この遺伝子リスト``affy10.txt``は、ある刺激前後の2群間で発現増加した実験が10回以上あった遺伝子群のリストです。  
     → [``affy10.txt``](https://raw.githubusercontent.com/AJACS-training/AJACS60/master/bono1/affy10.txt)  （右クリックして「新しいタブで開く」もしくは「名前を付けてリンク先を保存」してください。）

- このデータは、どのような実験から得られたデータなのか、どのように解釈できるのかをDAVIDを使って考察してみましょう！  

#### 【実習4】metascapeを用いて、発現データの結果を生物学的に解釈する
- [【復習用 統合TV】Metascapeを使って、遺伝子リストの生物学的解釈をする](http://doi.org/10.7875/togotv.2016.135)


1. [metascape](http://metascape.org/)のウェブサイトにアクセスします。[![https://gyazo.com/61018efe1bc790def200e40d52357d34](https://i.gyazo.com/61018efe1bc790def200e40d52357d34.png)](https://gyazo.com/61018efe1bc790def200e40d52357d34)
2. probe IDリストをコピペ or ファイルを指定し、`Submit`をクリックします。[![https://gyazo.com/f50fa9655839f96dd59c3435834257ae](https://i.gyazo.com/f50fa9655839f96dd59c3435834257ae.png)](https://gyazo.com/f50fa9655839f96dd59c3435834257ae)
3. リストのIDの種類タイプが自動的に推定されます。… 今回は、`Affymetrix ID`と推定されました。[![https://gyazo.com/2fc26c80d646f412fde27486bf8b2baa](https://i.gyazo.com/2fc26c80d646f412fde27486bf8b2baa.png)](https://gyazo.com/2fc26c80d646f412fde27486bf8b2baa)
4. `Express Analysis` をクリックするとデータ解析が実行されます。
5. しばらく待つと解析が終了し`Analysis Report Page`が現れます。それをクリックします。[![https://gyazo.com/c88f72e34f7e4ee1ec5a2e14971d379e](https://i.gyazo.com/c88f72e34f7e4ee1ec5a2e14971d379e.png)](https://gyazo.com/c88f72e34f7e4ee1ec5a2e14971d379e)
6. 解析を続けます。真ん中の「Functional Annotation Tool」をクリックします。
7. Enrichment解析の結果が表示されます。
[![https://gyazo.com/1587565858d188a52f893bb516ec17cd](https://i.gyazo.com/1587565858d188a52f893bb516ec17cd.png)](https://gyazo.com/1587565858d188a52f893bb516ec17cd)
8. 下部のPDFアイコンをクリックすると、Enrichment解析のヒストグラムがPDF形式でダウンロードできます。
9. `Gene List Report Excel Sheets`や`Gene List Report PPT file`をクリックするとそれぞれExcelとPowerPointのファイル形式で結果が得られます。
10. このページの下部には、Enrichment解析の詳細な結果などが表示されていますので見てみましょう。

#### 【応用2】複数のエンリッチメント解析ツールを用いて、発現データの結果を生物学的に解釈する
1. かつてはDAVIDというツールでこのエンリッチメント解析は行われていました。同様の結果が得られるか、試してみましょう。
 - [【統合TV】DAVIDを使ってマイクロアレイデータを解析する 2012](http://doi.org/10.7875/togotv.2012.079)
 - [【統合TV】DAVIDの使い方 実践編](http://doi.org/10.7875/togotv.2013.033)
2. また、特に医学・薬学分野に関連した情報を解析対象にすることができるのが特長の[GeneSetDB](http://genesetdb.auckland.ac.nz/haeremai.html)というツールもあります。これも試してみましょう。
 - [【統合TV】GeneSetDBで遺伝子解析とエンリッチメント解析を行う 2012](http://doi.org/10.7875/togotv.2016.002)
3. 複数のツールで得られた結果を踏まえ、「ある実験」とはどのような実験であったか考察してみましょう。
 - ``affy10.txt``は「ある刺激前後の2群間で発現が1.5倍以上上昇した実験が10回以上あった遺伝子群のリスト」  
4. 早く終わった方は、さらに20回以上発現上昇があった遺伝子群のリスト、[``affy20.txt``](https://raw.githubusercontent.com/AJACS-training/AJACS60/master/bono1/affy20.txt) （右クリックして「新しいタブで開く」もしくは「名前を付けてリンク先を保存」してください）で同じデータ解析をやってみましょう。10回以上のリストと比べてどういった違いがみられるでしょうか?
	- このようにいろいろな閾値を試して、結果を見て考察し、最終的な閾値としております(例: Table 4. Gene Set Enrichment Analysis of up/down-regulated genes after UV irradiation.[DOI: 10.1371/journal.pone.0116007.t004](http://dx.doi.org/10.1371/journal.pone.0116007.t004))
