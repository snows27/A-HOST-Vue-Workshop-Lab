<template>
  <div class="container text-center">
    <h1>Device ID : {{ id }}</h1>
    <p>----------------------</p>
    <p>{{ device.Title }}</p>
    <p>{{ device.Processor }}</p>
    <p>Price : ${{ device.Price }}</p>
    <img class="block mx-auto" :src="device.Photo" />
  </div>
</template>

<script>
import { computed } from 'vue';
import { useRoute } from 'vue-router/dist/vue-router.esm-bundler';
import axios from 'axios';
export default {
  name: 'Detail',
  setup() {
    const route = useRoute();
    const id = computed(() => route.params.id);
    return {
      id,
    };
  },
  data: () => ({
    device: [
      {
        Title: '',
        Processor: '',
        Photo: '',
        Price: '',
      },
    ],
  }),
  created() {
    axios.get(`https://demo.yume-dev.me/devices?id=${this.id}`).then((res) => {
      [this.device] = res.data;
      console.log(this.device);
    });
  },
};
</script>
