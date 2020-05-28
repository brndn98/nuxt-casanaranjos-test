<template>
  <div>
    <div v-for="event in events" :key="event.id">
      <img
        v-bind:src="event.better_featured_image.source_url"
        alt="image"
        width="400px"
        height="400px"
      />
      <nuxt-link :to="'/' + event.slug">{{event.title.rendered}}</nuxt-link>
      <hr />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    const response = await $axios.get(
      "http://distritotec.itesm.mx/wp-json/wp/v2/eventos?per_page=5"
    );
    const events = response.data;
    return {
      events
    };
  }
};
</script>
