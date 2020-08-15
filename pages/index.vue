<template>
  <main class="main top">
    <h1 class="title01">
      阿部 寛のホームページ
    </h1>
    <div class="conts">
      <div class="leftBlock">
        <picture>
          <source srcset="~assets/images/abe-top-20190328-2.webp" type="image/webp">
          <img src="~assets/images/abe-top-20190328-2.jpg" alt="">
        </picture>
        <dl class="dlList01">
          <div class="dlList01__item">
            <dt>阿部 寛</dt>
            <dd>（あべ ひろし）</dd>
          </div>
          <div class="dlList01__item">
            <dt>生年月日</dt>
            <dd>1964年6月22日</dd>
          </div>
          <div class="dlList01__item">
            <dt>血液型</dt>
            <dd>A型</dd>
          </div>
          <div class="dlList01__item">
            <dt><a href="#">プロフィール</a></dt>
          </div>
        </dl>
        <p>If you have any enquiries regarding my TV drama or film, or would like to make an enquiry concerning future projects, please do not hesitate to contact me through the following email address.</p>
        <p class="mailTxt">mail:<a href="">shigeta@navy.plala.or.jp</a></p>
        <dl class="dlList02">
          <div class="dlList02__item">
            <dt>所属:</dt>
            <dd>茂田オフィス<br>
            107-0052<br>
            東京都港区赤坂9-5-29<br>
            赤坂ロイヤルマンション303</dd>
          </div>
          <div class="dlList02__item">
            <dt>TEL :</dt>
            <dd>+81-3-5410-8585</dd>
          </div>
          <div class="dlList02__item">
            <dt>FAX :</dt>
            <dd>+81-3-5410-0588</dd>
          </div>
        </dl>
      </div>
      <div class="rightBlock">
        <p class="infoTitle">★★★　最新情報　★★★</p>
        <hr>
        <dl>
          <dt>ドラマ</dt>
          <dd v-for="(post,i) in infoDrama" :key="i">
            <a :href="post.fields.link">{{ post.fields.title }}</a>
            <br>{{ post.fields.comment }}
          </dd>
        </dl>
        <hr>
        <dl>
          <dt>映画</dt>
          <dd v-for="(post,i) in infoMovie" :key="i">
            <a :href="post.fields.link">{{ post.fields.title }}</a>
            <br>{{ post.fields.comment }}
          </dd>
        </dl>
        <hr>
      </div>
    </div>
  </main>
</template>

<script>
import { createClient } from '~/plugins/contentful.js'

const client = createClient()

export default {
  head: {
    title: 'テスト'
  },
  data() {
    return {
      infoMovie: '',
      infoDrama: ''
    }
  },
  async asyncData({ env, params }) {
    const infoMovie = await client
    .getEntries({
      content_type: "infoMovie"
    })
    const infoDrama = await client
    .getEntries({
      content_type: "infoDrama"
    })
    return{
      infoMovie:infoMovie.items,
      infoDrama:infoDrama.items
    }
  }
}
</script>

<style></style>
