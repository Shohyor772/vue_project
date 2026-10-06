<script setup>
import Article from './Article.vue'

defineProps({
  articles: Array,
  msg: String,
})
</script>

<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <div v-if="articles.length">
      <Article
        v-for="article in articles"
        :key="article.id"
        :author="article.author"
        :title="article.title"
        :body="article.body"
        :isPublished="article.isPublished"
      />
    </div>
    <p v-else>Нет статей в списке.</p>
  </div>
</template>