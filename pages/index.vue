<template>
  <div class="container-fluid">
    <div class="h1 m-4">BERITA HARI INI</div>
    <div class="container">
    <div class="row">
      <div v-for="article in articles" :key="article">
        
        <div class="card m-3" style="max-width: 540px; max-height: 720px;">
          <div class="row no-gutters">
            <div class="col-md-4">
              <img :src="article.urlToImage" class="img-fluid" :alt="article.urlToImage" >
            </div>
            <div class="col-md-8">
              <div class="card-body">
                <h4 class="card-title">{{article.title}}</h4>
                <p class="card-text">{{article.description}}</p>
                <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>
              </div>
            </div>
          </div>
        </div>
        
      </div>
    </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data(){
    return {
      articles: null,
    };
  },
  mounted() {
    axios.get('https://newsapi.org/v2/top-headlines?sources=bbc-news&apiKey=92877d01cdb846a7b8cd10f71c427b3d')
      .then(response => (this.articles = response.data.articles))
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
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
</style>
