<template>
  <main class="main movie">
    <h1 class="title02">
      阿部 寛の映画出演
    </h1>
    <ul class="list">
      <li v-for="(post,i) in movieAward" :key="i">
        {{ post.fields.list }}
      </li>
    </ul>
    <table class="table">
      <tbody>
        <tr v-for="(post,i) in movie" :key="i">
          <td>{{ post.fields.date }}</td>
          <td><a :href="post.fields.link">{{ post.fields.title }}</a></td>
          <td>{{ post.fields.comment }}</td>
        </tr>
      </tbody>
    </table>
    <hr />
  </main>
</template>

<script>
import { createClient } from '~/plugins/contentful.js'

const client = createClient()

export default {
  data() {
    return {
      movie: '',
      movieAward: ''
    }
  },
  async asyncData({ env, params }) {
    const movie = await client
    .getEntries({
      content_type: "movie"
    })
    const movieAward = await client
    .getEntries({
      content_type: "movieAward"
    })
    return{
      movie:movie.items,
      movieAward:movieAward.items
    }
  }
}
</script>

<style></style>
