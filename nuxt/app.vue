<template>
  <h1 class="nuxt__title">Title</h1>
  <div class="container">
    <h2 class="container__title">Container Title</h2>
    <hr />
    <p class="container__text">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Beatae, quo.
      Saepe ab qui accusamus mollitia libero laudantium itaque velit, recusandae
      consectetur est. Velit voluptatem omnis, vero nostrum libero laudantium
      excepturi?
    </p>
  </div>
  <div class="api__container">
    <h2 v-for="item in data" :key="item.id">{{ item.title }}></h2>
    <p class="api__text">api テキスト</p>
  </div>
</template>

<script>
export default {
  async asyncData({ params }) {
    const response = await axios.get("http://localhost:1337/api/test/cat/");
    return {
      data: response.data,
    };
  },
};
</script>
<style>
body {
  height: 200px;
  width: 90%;
  background-image: linear-gradient(
    90deg,
    rgba(40, 0, 255, 1),
    rgba(255, 160, 71, 1)
  );
}

.nuxt__title {
  color: #fff;
  font-size: 32px;
  font-weight: 400;
  text-align: center;
}

.container {
  width: min(100%, 1120px - 80px);
  margin: 0 auto 60px;

  .container__title {
    color: aliceblue;
    border-left: 2px solid aliceblue;
    padding-left: 1em;
    margin-bottom: 60px;
  }

  .container__text {
    color: bisque;
  }
}

.api__text {
  text-align: center;
  color: bisque;
}
</style>
