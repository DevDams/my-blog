<template>
  <div class="container">
    <div>
      <h1 class="title">
        blog
      </h1>
    </div>
    <div v-for="obj in getObjects.objects" :key="obj.title">
      <img :src="obj.metadata.image.imgix_url" alt="" class="image">
      <nuxt-link :to="'/blog/' + obj.slug">
        <h1>{{ obj.title }}</h1>
      </nuxt-link>
      <p>{{ obj.metadata.description }}</p>
    </div>
  </div>
</template>

<script>
import getObjects from '../queries/getObjects'
export default {
  apollo: {
    getObjects: {
      prefetch: true,
      query: getObjects
    }
  }
}
</script>

<style scoped>
.container {
  margin: 0 auto;
  min-height: 100vh;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.image {
  width: 300px;
  height: 350px;
}
</style>
