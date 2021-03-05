<template>

<div>{{toonList.title_english}}<br>
  <b-img :src="toonList.image_url" fluid alt="Responsive image"></b-img><br>
  <div class="container">
  {{toonList.synopsis}}
  </div>
</div>


</template>

<script>
import axios from 'axios'
export default {
data() {
    return {
      toonList: "",
      url: `https://api.jikan.moe/v3/manga/${this.$route.params.id}`,
    };
  },
  
  mounted() {
    axios
      .get(this.url)
      .then((response) => {
        this.toonList = response.data;
      })
      .catch((err) => {
        console.log(err);
        alert(err);
      });
  },
}
</script>

<style>

</style>