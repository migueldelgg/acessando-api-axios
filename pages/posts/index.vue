<template>
  <div class="posts">
    <ul>
      <li v-for="post in posts" :key="post.id">
        <NuxtLink :to="`/posts/${post.id}`">
          <h2 class="post-title">{{ post.date }} - {{ post.woodSpecies }}</h2>
          <h3 class="post-measure">Medida: {{ post.measure }}</h3>
          <p class="post-production">Produção Diária: {{ post.dailyProduction }}</p>
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    try {
      const posts = await $axios.$get("/production/findAll")
      return { posts }
    } catch (error) {
      console.error("Error fetching posts:", error)
      return { posts: [] }
    }
  },
  data() {
    return {
      posts: []
    }
  }
}
</script>

<style scoped>
.posts ul {
  list-style-type: none;
  padding: 0;
}

.posts li {
  margin: 15px 0;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
  background-color: #f9f9f9;
}

.post-title {
  margin: 0 0 5px 0;
  font-size: 1.5em;
  color: #333;
}

.post-measure {
  margin: 5px 0;
  font-size: 1.2em;
  color: #666;
}

.post-production {
  margin: 5px 0;
  font-size: 1em;
  color: #999;
}

a {
  text-decoration: none;
  color: inherit;
}

a:hover {
  color: #007BFF;
}
</style>
