---
title: "Hugo + Netlify でブログサイトを作る [1/2]"
date: 2018-10-01T23:12:47+09:00
draft: false
toc: true
thumbnail: "/images/PC_theme_photo_0008.jpg"
categories:
 - "web"
 - "hugo"
 - "netlify"
---

これから、ブログサイトをつくろう思います。
---	

とかなんとか言ってますが、  
私はwebエンジニアではなく  
ただの専業主婦

主にGoogle先生の助けと  
エンジニアであるダンナの協力で  
作っていこうと思います。  
  
  
  

Hugo と Netlifyという組み合わせ
---

上記の構成でブログを作ろうとした理由は  
ダンナのアドバイス  

早速、いろいろと手取り足取り教えてくれるのかと思いきや  


ダンナ「とりあえず誰の助けも借りずにがんばってごらん（はぁと」  

と、相変わらずのデレツンっぷり、、  

まぁ、そうやって冷たくされるのは嫌いでは無いので  
（相変わらずドMなわたし。）  
早速ググってみる  

早速よさげなサイトが見つかった  
さすがGoogle先生  

---
HugoとNetlifyで、簡単に自分のブログを公開してみよう！  
https://www.esz.co.jp/blog/181.html  
（株式会社しずおかオンラインブログより）  

---

コチラのブログによると  
Hogo というのが、静的サイトジェネレータで  
Netlify というのが、静的サイトを公開するホスティングサービス  
らしいです  
  
Hugoってのがアプリケーションで、  
Netlifyってのがサーバってことですかね  
・・・まぁ、なんでもいいんです、無料でブログサイトがつくれるなら。  
  
  
手順は以下の通り  
１．Hugoでブログを作る  
２．Netlifyで公開する  
  
お、たったの２ステップなんですね。  
なんだかすぐにできそうな予感。  


早速、１．Hugoでブログを作る、の工程に行きましょう。
---
  
しずおかオンラインさんのブログにしたがって、サクサク進めていきましょう！  

> では、早速、terminalを開いて、ブログサイトを作ってみましょう！  
> 今回は、事前に以下の環境を準備してあります。  
> (以下に記したツールのインストール方法などの説明は割愛させていただきます)  
>   
> ・macOS High Sierra  
> ・Homebrew(パッケージマネージャー)  
> ・Github  
> まずは、Homebrewを使ってHugoをインストールします。  

  
お、おおぅ、、、  

> 説明は割愛させていただきます  

の部分がよくわかりせん。。。  

・macOS High Sierra  
・Homebrew(パッケージマネージャー)  
・Github  
  
が、それぞれ、いちいちよくわかりません。。。  
  
基本に忠実に、まずはググります。  

---
macOS High Sierra にアップグレードする  
https://support.apple.com/ja-jp/macos/high-sierra  
（Appleサポートサイトより）  

---
  
フーム、どうやらmacOSのバージョンのようですね。  
わたしのPCはバリバリのWindowsなので、  
いきなり詰みましたね。。。  
  
こうなればダンナの macbook を無断で拝借しようかともおもったが  
勝手に触るとあとで、ギャーギャーギーギーうるさいので  
他の手段を考えてみます。  

Windows でもHogo 使えるんでしたっけ？
---

Hugo っていうのが macOS だけじゃなくて、Windows でも使えれば  
OKってことだと思うので、いくつかググってみると、  
どうやら、Hogo の Windows版というのは存在しているらしい。  
ということで、とりあえず良かった。  
このブログが続けられるｗ  

Hogo のインストール方法を求めてさらにググってみると  
Chocolatey なるものがちらほらでてきました。  
  
さて、なんでしょうね、Chocolatey さん  
名前の甘ーい感じと同様に、取り扱いもイージーな感じでお願いしたいところですよね。  

---
Chocolateyがとても便利だったので紹介する  
https://donsyoku.com/pc/introduction-for-chocolatey.html  
（鈍色スイッチより）  

---
    
下記、インストールコマンドを叩いてみると、  
  

```言語:windowsコマンド
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```  


![gazo01](/images/gazo_001_20180914.png)

なんか、警告っぽい感じ、、、  
ログの感じから、管理者権限が無いぞ的な？  
  
  
ということで、管理者権限でコマンドプロンプトを起動し、  
再度実行。  

![gazo02](/images/gazo_002_20180914.png)
  
なんかちょろちょろワーニングが出てますが、  
まぁ、結果オーライというか、とりあえずインストールは成功したようです。  
  
  
  
続けて、choco ちゃんを使って、Hugoをインストールしてみましょう。  

インストール方法はっと、、、早速ググりましょう  

---
静的ジェネレーターHugoを使う  
https://raym-d.jp/blog/install-hugo/  
（RAYM DESIGNより）  

---


なんと、

```言語:windowsコマンド
choco install hugo
```  

  
っていうコマンド叩くだけでいいんですって！  

あの面倒な、「次へ(N)」「次へ(N)」地獄がないなんて  
ほんと、ステキですね！  
  
  
![gazo03](/images/gazo_003_20180914.png)  
  
  
ということで、インストールできたので、早速 Hugo でサイトを作ってみましょう
  
```言語:windowsコマンド
hugo new site my_blog
```  
  
お、なんか成功したっぽい。  
  
my_blog っていうディレクトリができてますね。  
  

Gitとの連携、の前にGitを理解する
---

次、Git に連携。。。  
そう、Git、ぎっと、gitto  
Git ってなんですかね。  

ググりましょう。

---
【絶対理解できる】Gitとは？特徴やできることまとめ！  
https://www.sejuku.net/blog/5756  
（侍エンジニア塾ブログより）  

---
  
  
こちら、絶対理解出来る、という頼もしい文言がついていたので早速記事を拝見。  
  
・  
・  
・  
・  
・  
  
フーム。ソースコードを管理出来る便利なツールっていうことですね。  
そんな便利なツールなら、早速、インストールしましょう。  
  
またまたググって、、、  

とと、まてよ。  

choco ちゃんで Git をインストールできんじゃね？  

ということで

```言語:windowsコマンド
choco install git
```  
  
  
おお－、動いてる動いてる  
ということで、無事インストールができました！  

gitにパスが通って無かったので、フルパスで指定して、、  

```言語:windowsコマンド
C:\Program Files\Git\bin\git init
```  
  
無事、Git 管理にできました。  

それからテーマを選んだり  
config.toml にテーマ名を設定したり  
と、順調に作業は進み。  

新規記事を作成。  
  
  
とりあえず、Git との連携が設定できたので、  
続きは次回。  


