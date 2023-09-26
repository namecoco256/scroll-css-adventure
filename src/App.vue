<script setup>
import { onMounted } from 'vue';
import Header from './components/header.vue'

onMounted(() => {
  window.onload = () => {
    const target = document.getElementsByClassName('target')
    console.log(target)
  }
})
function fontBigger() {
  const p = document.querySelectorAll('#text-dummy p');
  for (let i = 0; i < p.length; i++) {
    p[i].style.fontSize = '1em'
    // text[i].removeAttribute('id')
  }
}
function makeLineHeight(){
  const text = document.querySelectorAll('#text-dummy');
  for (let i = 0; i < text.length; i++) {
    text[i].style.lineHeight = "1.5";
    // text[i].removeAttribute('id')
  }
}
function removeTextDummy(){
  const text = document.querySelectorAll('#text-dummy');
  for (let i = 0; i < text.length; i++) {
    text[i].removeAttribute('id')
  }
}

</script>

<template>
  <section class="hero-dummy is-large">
    <div class="hero-body-dummy">
      <div class="">
        <img id="top-image" src="./assets/img/DSC05986.JPG">
        <h1 class="title is-1">
          CSS
        </h1>
        <h2 class="subtitle is-4">
          CSS
        </h2>
      </div>
    </div>
  </section>
  
  <section id="text-dummy" class="transition">
    <p>
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
      <br>
    </p>
  </section>
  <section id="text-dummy" class="font-bigger transition">
    <button @click="fontBigger">文字を大きくする</button>
  </section>
  <section id="text-dummy" class="make-line-height transition">
    <button @click="makeLineHeight">行間を開ける</button>
    <p>
      <br>
      いかがでしょうか。<br>
      行間を開けるだけでもそれなりに読みやすさは向上したと思います。<br>
    </p>
  </section>
  <section id="text-dummy" class="remove-text-dummy">
    <button @click="removeTextDummy">コントラストを下げる</button>
  </section>


</template>

<style lang="scss">
@import "bulma/bulma.sass";

</style>