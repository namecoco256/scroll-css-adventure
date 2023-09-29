<script setup>
import { onMounted, watch, ref } from 'vue';
import Header from './components/header.vue'
import navigatorText from './components/navigatorText.vue';
import hljs from 'highlight.js'
import hero from './components/hero.vue'

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

function addCardClass(){
  const text = document.querySelectorAll('.card-content-dummy');
  for (let i = 0; i < text.length; i++) {
    text[i].classList.add('card-content')
    text[i].classList.remove('card-content-dummy')
  }
  textDummyFlags.value[2] = true
}

const isOverlapped = ref(false)
function titleOverlap(){
  const topImageDummy = document.querySelectorAll('#top-image-dummy')
  for (let i = 0; i<topImageDummy.length; i++){
    topImageDummy[i].remove()
  }
  const heroBody = document.querySelectorAll('.hero-body-dummy')
  for (let i = 0; i<heroBody.length; i++){
    heroBody[i].classList.remove('hero-body-dummy')
    heroBody[i].classList.add('hero-body')
  }
  const hero = document.querySelectorAll('.hero-dummy')
  for (let i = 0; i < hero.length; i++) {
    hero[i].classList.remove('hero-dummy')
    hero[i].classList.add('hero')
  }
  isOverlapped.value = true
}

const isTitleDarked = ref(false)
function titleDarker(){
  const title = document.getElementsByClassName('title is-2 transition')
  for (let i = 0; i < title.length; i++){
    title[i].classList.add('has-text-white')
  }
  const subtitle = document.getElementsByClassName('subtitle is-3 transition')
  for (let i = 0; i < subtitle.length; i++){
    subtitle[i].classList.add('has-text-light')
  }
  const heroBodyBefore = document.querySelectorAll('.hero-body:before')
  console.log(heroBodyBefore)
  for (let i = 0; i < heroBodyBefore.length; i++) {
    heroBodyBefore[i].style.backgroundColor = 'rgba(0,0,0,0.4)'
  }
  const jumpTo = document.getElementsByClassName('hero-body')[1]
  jumpTo.scrollIntoView({ behavior: 'smooth' })

  isTitleDarked.value = true
}

const isChangeButton = ref(false)
function changeButton(){
  const button = document.querySelectorAll('button')
  console.log(button)
  for (let i = 0; i < button.length; i++) {
    button[i].classList.add('button')
  }
  const jumpTo = document.getElementsByClassName('changing-color')[0]
  jumpTo.scrollIntoView({ behavior: 'smooth' })
  isChangeButton.value = true
}

const isChangedButtonColor = ref(false)
const selectedColor = ref('白黒')
let currentColor = ref('')
watch(selectedColor, ()=>{
  console.log(selectedColor)
  const button = document.querySelectorAll('button')

  for (let i = 0; i < button.length; i++) {
    button[i].classList.remove('is-' + currentColor.value)
  }
  switch(selectedColor.value){
    case '白黒':
      currentColor.value = ''
      break
    case '青緑':
      currentColor.value = 'primary'
      for (let i = 0; i < button.length; i++) {
        button[i].classList.add('is-' + currentColor.value)
      }
      break
    case '青':
      currentColor.value = 'link'
      for (let i = 0; i < button.length; i++) {
        button[i].classList.add('is-' + currentColor.value)
      }
      break
    case '水色':
      currentColor.value = 'info'
      for (let i = 0; i < button.length; i++) {
        button[i].classList.add('is-' + currentColor.value)
      }
      break
    case '緑':
      currentColor.value = 'success'
      for (let i = 0; i < button.length; i++) {
        button[i].classList.add('is-' + currentColor.value)
      }
      break
    case '黄色':
      currentColor.value = 'warning'
      for (let i = 0; i < button.length; i++) {
        button[i].classList.add('is-' + currentColor.value)
      }
      break
    case '赤':
      currentColor.value = 'danger'
      for (let i = 0; i < button.length; i++) {
        button[i].classList.add('is-' + currentColor.value)
      }
      break
  }
  isChangedButtonColor.value = true
})

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

function back(){
  const jumpTo = document.getElementsByClassName('hero-body')[0]
  jumpTo.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
  <hero />
  <section id="text-dummy" class="transition introduction main-text ">
    <div class="card-content-dummy transition main-text">
      <p>
        <br>
        みなさん、こんにちは。初めまして。<br>
        <br>
        突然ですが、今このページを開いてみて、みなさんはどのような感想を抱きましたか？<br>
        おそらく、「ダサい」「味気ない」「文字が読みにくい」といった、ネガティブな感想が浮かんだことでしょう。<br>
        <br>
        それもそのはず。今このページは<b>CSS</b>と呼ばれるファイルが<b>一切設定されていない</b>状態です。<br>
        <br>
        CSSは、ウェブページやホームページのデザインを整えるためのファイルで、ほぼすべてのデザイン要素を制御しています。<br>
        <br>
        ……と、いきなりこのような説明をされても理解しきれないかもしれません。<br>
        今からこのページに実際にCSSを追加しながら、CSSがデザインにどのような影響を及ぼすのか一緒に見ていきましょう！<br>
        <br>
      </p>
    </div>
  </section>
  <section id="text-dummy" class="transition introduction main-text ">
    <div class="card-content-dummy transition main-text">
      <h1 class="title is-3">実際にCSSを変更してみよう</h1>
      <p>
        <br>
        まずは文字が読みにくいのをどうにかしたいですね。<br>
        文字の可読性はすなわち<b>Webページの命です。</b><br>
        ですのでこちらを最優先で進めていきましょう！<br>
        <br>
        このページの文字の可読性を下げている大きな要因として以下の3つが挙げられます。<br>
        <br>
        <div class="content">
          <ol>
            <li>文字が小さすぎる</li>
            <li>行間が狭すぎる</li>
            <li>文字が端に寄りすぎている</li>
          </ol>
        </div>
        <br>
        ひとつずつ修正していきましょう。<br>
        <br>
        <br>
        <button class='transition' @click="fontBigger">文字を大きくする</button><br>
        <br>
        <button class='transition' @click="makeLineHeight">行間を開ける</button><br>
        <br>
        <button class='transition' @click="addCardClass">文字を少し動かす</button><br>
        <br>
        
      </p>
    </div>
    <navigatorText text="(ボタンを全てクリックすると先に進みます)" v-if="isTextDummy"></navigatorText><br>
  </section>
  
  <div class='css-explanation temp' v-if="isTextDummy"></div>
  <Transition>
    <section class="transition css-explanation  main-text" v-if="!isTextDummy">
      <div class="card-content">
        <p>
          いかがでしょうか。<br>
          すこし読みやすくなりました。<br>
          <br>
          具体的にどのような変更を加えたか解説していきます。<br>
          <br>
          まず、そのためには<b>HTML</b>どのようなものなのかを軽く知っておく必要があります。<br>
          <br>
        </p>
      </div>
    </section>
  </Transition>
  <Transition>
    <section class="transition css-explanation  main-text" v-if="!isTextDummy">
      <div class="card-content">
        <h1 class="title is-3">HTMLについて</h1>
        <p>
          HTMLは、ウェブページの構造を設定するためのファイル形式です。<br>
          CSSを家の内装や装飾にたとえるなら、HTMLはその家の骨組みに相当します。<br>
          <br>
          このページのHTMLファイルは以下のようになっています。<br>
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
          HTMLでは、テキストを<b>タグ</b>と呼ばれる目印(&lt;body&gt;のような形式)で囲むことで階層構造を表現します。通常、これらのタグに対してCSSを適用して装飾を追加します。
          <br>
          一部のタグは &lt;section class="introduction"&gt; のように、属性を持っています。(タグの中のスペースの右側についている、この例だと『class="introduction"』の部分です)<br>
          <br>
          この<b>属性</b>は、CSSで特定の装飾を適用する際の目印として使用されます。<br>
          <br>
          さて、ここで先ほど追加したCSSについて詳しく見てみましょう。<br>
          <br>
          <pre><code class="language-css">p{
  font-size: 1em;
  line-height: 1.5;
  color: #4a4a4a;
}</code></pre>
          <br>
          このCSSファイルでは、『p』 タグに適用される見た目の設定が記述されています。この設定は、『p』 タグで囲まれたテキストに適用されます。
          <br>
          具体的な設定内容は以下の通りです。<br>
          <div class="content">
            <ol>
              <li>フォントのサイズ</li>
              <li>行間の設定</li>
              <li>文字の色</li>
            </ol>
          </div>
          それぞれの設定値はコロンの後に記述されており、たとえば `font-size:` の後には文字のサイズを指定する値（単位として `em` を使用）が続きます。<br>
          (この単位についてはあまり気にしなくても構いません。)<br>
          <br>
          ……少し技術的な話をしてしまいましたが、無理に覚える必要はありません。<br>
          この次は、ウェブページをより魅力的にする方法や重要なポイントに焦点を当てて学んでいきましょう！<br>
          <br>
        </p>
      </div>
    </section>
  </Transition>
  <Transition>
    <section class="title-fix  transition main-text" v-if="!isTextDummy">
      <div class="card-content">
        <h1 class="title is-4">もっとデザインを書き換えよう！</h1>
        <p>
          次は……そうですね、このページの一番上にあるタイトルが崩れているのを修正したいと思います。<br>
          <br>
          この部分は利便性や可読性に直接関わるわけではありませんが、<br>
          ユーザーが最初に目にする部分であるため、綺麗に整えておくことが重要です。<br>
          <br>
          タイトルのクローンをここに用意しました :
        </p>
      </div>
    </section>
  </Transition>
  <hero v-if="!isTextDummy"/>

  <section class=' main-text transition' v-if="!isTextDummy">
    <div class="card-content">
    <p>
      <br>
      タイトル名と画像の配置が大幅にずれているので、これらを重ねて配置しましょう。<br>
      <br>
      <button class='transition' @click="titleOverlap">重ねる</button>
    </p>
    <navigatorText text="(ボタンをクリックすると先に進みます)" v-if="!isOverlapped && isTextDummy"></navigatorText><br>
    </div>
  </section>
  <div class='title-image-darker temp' v-if="!isOverlapped"></div>
  <Transition>
    <section class="title-image-darker  main-text transition" v-if="isOverlapped && !isTextDummy">
      <div class='card-content'>
        <p>
          ……うーん、文字の色が画像の色に似ていて、読みにくさを感じます。<br>
          <br>
          色についても考えてみましょう。<br>
          この画像は比較的暗い色が大部分なので、文字の色には明るい白色が適しています。<br>
          <br>
          <button class='transition' @click="titleDarker">色を変える</button>
        </p>
      </div>
      <navigatorText text="(ボタンをクリックすると先に進みます)" v-if="!isTitleDarked && isOverlapped && !isTextDummy"></navigatorText><br>
    </section>
  </Transition>
  
  <Transition>

    <section class=" main-text transition" v-if="isTitleDarked && isOverlapped && !isTextDummy">
      <div class="card-content">
        <p>
          いいですね！<br>
          これにより文字と背景のコントラストが上がり、よりオシャレかつ視認性の高いデザインになりました。<br>
        </p>
      </div>
    </section>
  </Transition>
  <Transition>
    <section class="main-text transition" v-if="isTitleDarked && isOverlapped && !isTextDummy">
      <div class="card-content">
        <p>
          最後に、ボタンのデザインを変えましょう。<br>
          現在はブラウザに初期から入っているデザインがそのまま使用しています。<br>
          これを別なデザインに変更してみましょう。<br>
          <br>
          試しに枠線だけのシンプルなデザインのものにしてみます。<br>
          <br>
        </p>
        <button class='transition' @click="changeButton">ボタンを変える</button>
      </div>
      <navigatorText text="(ボタンをクリックすると先に進みます)" v-if="!isChangeButton && isTitleDarked && isOverlapped && !isTextDummy"></navigatorText><br>
    </section>
  </Transition>
  <div class="changing-color temp" v-if="!isChangeButton && isTitleDarked && isOverlapped && !isTextDummy"></div>
  <Transition>
    <section class="main-text transition changing-color" v-if="isChangeButton && isTitleDarked && isOverlapped && !isTextDummy">
      <div class="card-content">
        <p>
          どうでしょうか。<br>
          この辺りは個人の好みによるかもしれません。<br>
          <br>
          いくつか選択肢を用意しておきましたので、お好きな色に変えてみてください。<br>
          <br>
          <div class="select">
            <select v-model="selectedColor">
              <option>白黒</option>
              <option>青緑</option>
              <option>青</option>
              <option>水色</option>
              <option>緑</option>
              <option>黄色</option>
              <option>赤</option>
            </select>
          </div>
        </p>
      </div>
      <navigatorText text="(色を変更すると先に進みます)" v-if="!isChangedButtonColor && isChangeButton && isTitleDarked && isOverlapped && !isTextDummy"></navigatorText><br>
    </section>
  </Transition>
  <Transition>
    <section class="main-text transition" v-if="isChangedButtonColor && isChangeButton && isTitleDarked && isOverlapped && !isTextDummy">
      <div class="card-content">
        <p>
          好みの色は見つかりましたか？<br>
          少し色が変わるだけで、Webページの印象は大きく変わります。<br>
          <br>
          あなたの一番好きな色を探してみてください。
        </p>
      </div>
    </section>
  </Transition>
  <Transition>
    <section class="main-text transition" v-if="isChangedButtonColor && isChangeButton && isTitleDarked && isOverlapped && !isTextDummy">
      <div class="card-content">
        <h1 class='title is-3'>終わりに</h1>
        <p>
          お疲れさまでした！<br>
          ここまでの閲覧、本当にありがとうございます。<br>
          <br>
          一度このページの一番上まで戻っていただくと、最初と比べはるかに読みやすくなっていることを実感できると思います。<br>
          <br>
          このページを通じてWebコーディング、プログラミングに興味を持っていただけたならとても幸いです。<br>
          <br>
          <button @click="back" :class="`transition button is-${currentColor}`">一番上に戻る</button>
          <br>
        </p>
      </div>
    </section>
  </Transition>

  <Template>

  </Template>
</template>

<style lang="scss">
@import "bulma/bulma.sass";

.v-enter-active,
.v-leave-active {
  transition: opacity 2s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>