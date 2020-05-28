<template>
  <div>
    <img
      v-bind:src="event.better_featured_image.source_url"
      alt="image"
      width="400px"
      height="400px"
    />
    <h1>{{event.title.rendered}}</h1>
    <hr />
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
    const response = await $axios.get(
      "http://distritotec.itesm.mx/wp-json/wp/v2/eventos?slug=" + params.event
    );
    console.log(response);
    const event = response.data[0];
    return {
      event
    };
  }
};
</script>
