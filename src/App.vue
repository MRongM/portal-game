<template>
  <div class="search-box">
    <input
      v-model="keyword"
      type="text"
      placeholder="Search game…"
      class="search-input"
      autofocus
    />
  </div>
  <main class="container">
    <div class="grid">
      <PageCard
        v-for="page in filteredPages"
        :key="page.url"
        :title="page.title"
        :description="page.description"
        :url="page.url"
        :iconUir="page.iconUir"
      />
    </div>
  </main>
</template>

<script>
import PageCard from './components/PageCard.vue'
import pages from './PageData'

export default {
  components: { PageCard },
  data() {
    return {
      keyword: '',
      pages
    }
  },
  computed: {
    filteredPages() {
      const key = this.keyword.trim().toLowerCase()
      if (!key) return this.pages
      return this.pages.filter(p =>
        p.title.toLowerCase().includes(key) ||
        p.description.toLowerCase().includes(key)
      )
    }
  }
}
</script>

<style scoped>
.search-box {
  text-align: center;
  margin-bottom: 32px;
}

.search-input {
  margin-top: 100px;
  width: 60%;
  max-width: 500px;
  padding: 12px 16px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 8px;
  outline: none;
  transition: 0.3s;
}
.search-input:focus {
  border-color: #007bff;
  box-shadow: 0 0 0 2px rgba(0,123,255,0.2);
}
.container {
  max-width: 80%;
  margin: 0 auto;
  padding: 40px 20px;
}
.header {
  font-size: 32px;
  text-align: center;
  margin-bottom: 40px;
}
.grid {
  display: grid;
  gap: 24px;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}
</style>
