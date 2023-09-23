<script setup>
import { onMounted } from 'vue';
import Header from './components/header.vue'

onMounted(() => {
  // const p = document.getElementsByTagName('p')[1];
  // p.setAttribute('class', 'test')
})
</script>

<template>
  <section class="hero-dummy is-large">
    <div class="hero-body-dummy">
      <div class="">
        <img width="70%" src="./assets/img/DSC05986.JPG">
        <p class="title is-primary">
          CSS
        </p>
        <p class="subtitle">
          CSS
        </p>
      </div>
    </div>
  </section>
  
  <section class="text-dummy">
    <p>みなさん、こんにちは。初めまして。</p>
    <p>突然ですが、今このページを開いてみて、みなさんはどんな感想を抱きましたか？</p>
    <p>おそらく、「ダサい」「味気ない」と思ったのではないでしょうか。</p>
    <p>それもそのはず。今このページはデザインや装飾を決定する<b>CSS</b>と呼ばれるファイルが<b>一切設定されていない</b>状態です。</p>
    <p>と、言うわけで今回は、このまっさらな状態のページを私と一緒に装飾していきましょう！</p>
  </section>

</template>

<style lang="scss">
@import "bulma/bulma.sass";

</style>