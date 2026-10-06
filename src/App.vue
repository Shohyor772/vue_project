<script setup>
import { ref } from 'vue'
import ArticleList from './components/ArticleList.vue'

const articles = ref([
  { id: 1, title: 'Введение в Vue 3', author: 'Иван Петров', body: 'Текст статьи...', isPublished: true },
  { id: 2, title: 'Работа с компонентами', author: 'Мария Сидорова', body: 'Текст статьи...', isPublished: false },
  { id: 3, title: 'Реактивность в деталях', author: 'Алексей Смирнов', body: '', isPublished: true },
])
</script>

<template>
  <main>
    <ArticleList :articles="articles" msg="Список статей" />
  </main>
</template>