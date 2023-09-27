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
          CSSのはたらき
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
        具体的にどんなふうに変更がくわえられたかを解説していきます。<br>
        <br>
        まず、そのためには<b>HTML</b>の知識が必要ですね。<br>
        <br>
        HTMLとは、Webページの構成を設定するためのファイルです。<br>
        先に挙げたCSSを家の内装や装飾だとすれば、HTMLは家の骨組みに当たります。<br>
        <br>
        このページのHTMLファイルはこのようになっています。<br>

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