<template>
  <div>
    <h1>Hello Twitch!</h1>
    <ul>
      <li v-for="post in posts" :key="post._id">
        {{ post.title }}
        <p>{{ post.body }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
import { groq } from '@nuxtjs/sanity'

const query = groq`{ "posts": *[_type == "post"] }`

export default {
  asyncData({ $sanity }) {
    return $sanity.fetch(query)
  },
}
</script>
