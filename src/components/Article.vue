<script setup>
import { computed } from 'vue'

const props = defineProps({
  title: String,
  body: String,
  author: String,
  isPublished: Boolean,
})

// 1. Вычисляемое свойство: имя автора заглавными буквами
const authorUpperCase = computed(() => {
  return props.author ? props.author.toUpperCase() : ''
})

// 2. Вычисляемое свойство: начертание шрифта в зависимости от публикации
const authorFontStyle = computed(() => {
  return props.isPublished ? 'normal' : 'italic'
})

// 3. Вычисляемое свойство: класс для покраски неопубликованных статей
const articleClass = computed(() => {
  return props.isPublished ? 'published' : 'unpublished'
})
</script>

<template>
  <div class="article" :class="articleClass">
    <h2 v-if="title">{{ title }}</h2>
    <p v-if="author" :style="{ fontStyle: authorFontStyle, fontWeight: 'bold' }">
      Автор: {{ authorUpperCase }}
    </p>
    <p v-if="body">{{ body }}</p>
    <p v-else class="no-body">Текст статьи отсутствует</p>
    <hr />
  </div>
</template>

<style scoped>
/* Красим неопубликованные статьи в красный */
.unpublished {
  color: red;
}
.published {
  color: green;
}
.no-body {
  font-style: italic;
  color: gray;
}
</style>