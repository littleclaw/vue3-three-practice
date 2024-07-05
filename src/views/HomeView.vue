<template>
  <main>
    <ol>
      <li v-for="(content, index) in contents" :key="content" @click="routeChapter(index)">{{ content }}</li>
    </ol>
  </main>
</template>

<script setup lang="ts">
import { useRouter } from 'vue-router'
const router = useRouter()
const contents = [
  'Basic Concept'
]
function routeChapter(index: Number) {
  router.push({ path: `/chapter${index + 1}` })
}
</script>

<style lang="scss" scoped>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

ol {
  padding: 0;

  li {
    font-size: 20px;
    list-style: none;
    cursor: pointer;
    margin-bottom: 10px;
    color: blue;

    &:hover {
      text-decoration: underline;
    }
  }
}
</style>