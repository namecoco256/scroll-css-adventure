<script setup>
import { onMounted, watch, ref } from 'vue';
import Header from './components/header.vue'
import navigatorText from './components/navigatorText.vue';
import hljs from 'highlight.js'

onMounted(() => {
  window.onload = () => {
    const target = document.getElementsByClassName('target')
    console.log(target)
  }
})
const textDummyFlags = ref([false,false,false])
const isTextDummy = ref(true)

function fontBigger() {
  const p = document.querySelectorAll('#text-dummy p');
  for (let i = 0; i < p.length; i++) {
    p[i].style.fontSize = '1em'
    // text[i].removeAttribute('id')
  }
  textDummyFlags.value[0] = true
}
function makeLineHeight(){
  const text = document.querySelectorAll('#text-dummy');
  for (let i = 0; i < text.length; i++) {
    text[i].style.lineHeight = "1.5";
  }
  textDummyFlags.value[1] = true
}
function changeColor(){
  const text = document.querySelectorAll('#text-dummy');
  for (let i = 0; i < text.length; i++) {
    text[i].style.color = '#4a4a4a'
  }
  textDummyFlags.value[2] = true
}
watch(textDummyFlags, () => {
  console.log(textDummyFlags)
  
  if(textDummyFlags.value.every((val)=>{return val})){
    const text = document.querySelectorAll('#text-dummy');
    console.log(text)
    for (let i = 0; i < text.length; i++) {
      text[i].removeAttribute('id')
    }
    isTextDummy.value = false

    const jumpTo = document.getElementsByClassName('css-explanation')[0]
    jumpTo.scrollIntoView({behavior: 'smooth'})
  }
},{deep:true})
</script>

<template>
  <section class="hero-dummy is-large">
    <div class="hero-body-dummy">
      <div class="">
        <img id="top-image" src="./assets/img/DSC05986.JPG">
        <h1 class="title is-2">
          見て学ぶWebデザイン超入門
        </h1>
        <h2 class="subtitle is-3">
          CSS編
        </h2>
      </div>
    </div>
  </section>
  
  <section id="text-dummy" class="transition introduction">
    <p>
      <br>
      みなさん、こんにちは。初めまして。<br>
      <br>
      突然ですが、今このページを開いてみて、みなさんはどんな感想を抱きましたか？<br>
      おそらく、「ダサい」「味気ない」「文字が読みにくい」……など、いろいろとネガティブな感想が浮かんだかもしれません。<br>
      <br>
      それもそのはず。今このページは<b>CSS</b>と呼ばれるファイルが<b>一切設定されていない</b>状態です。<br>
      <br>
      CSSは、ホームページなどのWeb上で見ることができるほぼすべてのデザインを設定するためのファイルのことです。<br>
      <br>
      ……と、そんなことを言われてもあまりピンと来ませんね。<br>
      なので、今からこのページに実際にCSSを追加していき、CSSがどのようなはたらきをしているのか一緒に見てみましょう！<br>
      <br>
    </p>
    <h1 class="title is-4">実際にCSSを変更してみよう</h1>
    <p>
      <br>
      まずは文字が読みにくいのをどうにかしたいですね。<br>
      文字の可読性はすなわち<b>Webページの命！</b><br>
      ですのでひとまずこちらを最優先で進めていきましょう！<br>
      <br>
      このページの文字の可読性を下げている大きな要因として以下の3つが挙げられます。<br>
      <br>
      <div class="content">
        <ol>
          <li>文字が小さすぎる</li>
          <li>行間が狭すぎる</li>
          <li>背景と文字の色のコントラストが高すぎて目に負担がかかる</li>
        </ol>
      </div>
      <br>
      上から順番に修正していきましょう。<br>
      <br>
      <br>
      <button @click="fontBigger">文字を大きくする</button><br>
      <br>
      <button @click="makeLineHeight">行間を開ける</button><br>
      <br>
      <button @click="changeColor">コントラストを下げる</button><br>
      <br>
      
    </p>
  </section>
  <navigatorText text="(ボタンを全てクリックすると先に進みます)"></navigatorText><br>
  <Transition>
    <section class="transition css-explanation" v-if="!isTextDummy">
      <p>
        いかがでしょうか。<br>
        まだまだ気になる点は沢山ありますが、いくらか読みやすくはなりました。<br>
        <br>
        具体的にどのような変更を加えたか解説していきます。<br>
        <br>
        まず、そのためには<b>HTML</b>どのようなものなのかを軽く知っている必要があります。<br>
        <h1 class="title is-4">HTMLについて</h1>
        HTMLとは、Webページの構成を設定するためのファイルです。<br>
        先に挙げたCSSを家の内装や装飾だとすれば、HTMLは家の骨組みに当たります。<br>
        <br>
        このページのHTMLファイルはこのようになっています。<br>
        <br>
        <pre><code class="language-html">&lt;body&gt;
  &lt;section class="hero is-large"&gt;
    &lt;div class="hero-body"&gt;
      &lt;div class=""&gt;
        &lt;h1 class="title is-2"&gt;
          見て学ぶWebデザイン超入門
        &lt;/h1&gt;
        &lt;h2 class="subtitle is-3"&gt;
          CSSのはたらき
        &lt;/h2&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/section&gt;
  &lt;section class="introduction"&gt;
    &lt;p&gt;
      &lt;br&gt;
      みなさん、こんにちは。初めまして。&lt;br&gt;
      &lt;br&gt;
      突然ですが、今このページを開いてみて、みなさんはどんな感想を抱きましたか？&lt;br&gt;
      ……中略……
    &lt;/p&gt;
  &lt;/section&gt;
&lt;/body&gt;</code></pre>
        <br>
        &lt;body&gt;…&lt;/body&gt; のような<b>タグ</b>と呼ばれる目印を使って文字を囲い、階層構造を表現しています。<br>
        基本的にはこのタグに対してCSSを指定し、装飾を付け加えます。<br>
        <br>
        中には &lt;section class="introduction"&gt; のように、スペースを開けてclass=""が続いているタグがあります。<br>
        これは、CSSで装飾をつけるための目印になり、このclassを指定して「この要素一つだけに装飾をつけたい」なんて時に使用します。<br>
        <br>
        さて、次に先ほど追加したCSSがどんなものだったか見てみましょう。<br>
        <br>
        <pre><code class="language-html">p{
  font-size: 1em;
  line-height: 1.5;
  color: #4a4a4a;
}</code></pre>
        <br>
        先頭に p、その次に波括弧、波括弧の中に見た目についての設定が書かれています。<br>
        ここで、HTMLファイルをもう一度見てみましょう。<br>
        &lt;p&gt; というタグで囲われた部分が見つかるはずです。<br>
        <br>
        つまり、このCSSは、「pの中のものを波括弧の中で指示しているように装飾しなさい」という意味になります。<br>
        波括弧の中身の内容は一番上から、
        <div class="content">
          <ol>
            <li>フォントのサイズ</li>
            <li>行と行の間隔</li>
            <li>文字の色</li>
          </ol>
        </div>
        の設定となっています。<br>
        :(コロン)の後ろの数字が、その設定のパラメーターに当たります。<br>
        <br>
        例えば、font-size:に続く <b>1em</b>が、文字のサイズをどれくらいにするか。という数字です。<br>
        あまり聞きなじみのない単位かもしれませんが、ここではそこまで気にする必要はありません。<br>
        <br>
        ……さて、ここまで難しい話が続きましたが、無理に覚える必要はありません。<br>
        ここからは、気になるポイントや、もっとおしゃれにできるポイントをどんどんと書き換えていきましょう！<br>
      </p>
    </section>
  </Transition>
  <Transition>
    <section class="title-fix" v-if="!isTextDummy">
      <h1 class="title is-4">もっとデザインを書き換えよう！</h1>
      <p>
        次は……そうですね、このページの一番上のタイトルが崩れてるのを直したいです。<br>
        直接読みやすさに関与する部分ではありませんが、ページにアクセスしたユーザーが一番最初に見る部分ですので、<br>
        ここが崩れているのは極力避けたいです。<br>
        <br>
        上のタイトルと全く同じものをここに用意しました↓
        <section class="hero-dummy is-large">
          <div class="hero-body-dummy">
            <div class="">
              <img id="top-image" src="./assets/img/DSC05986.JPG">
              <h1 class="title is-2">
                見て学ぶWebデザイン超入門
              </h1>
              <h2 class="subtitle is-3">
                CSS編
              </h2>
            </div>
          </div>
        </section>
      </p>
    </section>
  </Transition>
  <div class='css-explanation' v-if="isTextDummy"></div>
</template>

<style lang="scss">
@import "bulma/bulma.sass";

.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>