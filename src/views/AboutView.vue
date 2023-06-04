<template>
  <div class="about">
    <ul class="">
      <li v-for="item in myData" :key="item.id.value"> 
        <img :src="item.picture.medium" alt="">
        <p> {{ item.name.last }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      myData:{}
    }
  },
  async mounted() {
    console.log(import.meta.env.VITE_TEXT);
    await this.$http.get(import.meta.env.VITE_PATH).then((res) => {
     
      this.myData = res.data.results;
      console.log(this.myData);
    })
  }
}
</script>

<style>
ul {
  list-style:none
}
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
