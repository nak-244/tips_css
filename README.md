### background:fixedはiOSでうまく機能しないときにやる方法

[https://www.olp.co.jp/medical/](https://www.olp.co.jp/medical/)

## background-attachment:fixed;以外の方法で背景画像を固定する

background-attachment:fixed;を使わずにどうやって背景を固定するのかというと、パララックスにしたい要素そのものに背景を固定しようとしてもできないので、考え方としては、全画面を覆う背景を適用したブロック要素を作って、その要素自体をfixedで固定する。  

つまり、背景画像を固定するのではなくて、位置を固定した要素をコンテンツの後ろに配置するという方法をとります。  

要素という言葉だとわかりにくいかもしれないので、例えばdiv要素などと思えばいいでしょう。  

「背景画像を固定する」と「要素自体を固定する」というこの違いわかりますかね。  

この固定するための要素（例えばdivなど）を別で用意しないといけないんですけど、HTMLコードを触るのも面倒なのでCSSだけでやってしまいましょう。


今回は疑似要素というものを使います。  

:beforeというものを使って、背景を指定しようとしていた要素の先頭にCSSによって要素を挿入します。  

疑似要素についてはここでは説明しませんので、わからない人はそのままソースコードを覚えてください。  

背景画像を設定しようとしていた要素に対して、先頭に疑似要素としてのブロック要素を挿入して。  

つまり、簡単に言うとdivのようなものをCSSを使って挿入している感じです。  

で、その挿入した疑似要素を、その背景ではなくそのものを固定します。  

なので、ここではposition:fixedを使うんです。  

widthはもちろん100%で、高さについては表示領域全体の高さということでvhという単位を使って100vhを指定。  

vhっていう単位、かなり便利なんですがたぶん使ってる人少ないよね。


    body:before{
    content:"";
    display:block;
    position:fixed;
    top:0;
    left:0;
    z-index:-1;
    width:100%;
    height:100vh;
    background:url(https://y-com.info/contents/wp-content/uploads/2017/05/IMG_1894.jpg) center no-repeat;
    background-size:cover;
    }

    
