<template>
  <div class="card" @click="openPage">
    <img class="icon-image" :src="iconUir" alt="Icon" />
    <div class="info"> 
      <h2 class="title">{{ title }}</h2>
      <p class="description">{{ description }}</p>
    </div>
  </div>
</template>
  
<script>
export default {
  props: {
    title: String,
    description: String,
    iconUir: String,
    url: String,
  },
  methods: {
    openPage() {
      window.open(this.url, '_blank')
    }
  }
}
</script>
  
<style scoped>
  .info {
   margin-left: 20px; 
   /* padding-left: 20px;  */
  }
  .icon-image {
    width: 50px;
    height: 50px;
  }
  .card {
    background: #fff;
    border-radius: 16px;
    box-shadow: 0 2px 12px rgba(0, 0, 0, 0.1);
    padding: 20px;
    transition: 0.3s;
    cursor: pointer;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    min-width: 240px;
  }
  .card:hover {
    transform: translateY(-4px);
  }
  .title {
    font-size: 18px;
    font-weight: bold;
    margin-bottom: 8px;
  }
  .description {
    color: #666;
    font-size: 14px;
    margin-bottom: 12px;
  }
</style>
  