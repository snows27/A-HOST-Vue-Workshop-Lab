<template>
  <div class="grid grid-cols-2 gap-4 border-black">
    <div class="ml-10 mr-0">
      <h1>Manufacturer</h1>
      <ul
        v-for="manufacture in manufacturer"
        :key="manufacture.id"
        class="border border-black"
      >
        <li>
          <button @click="changeManufacturerId(manufacture.id)">
            <img :src="manufacture.Logo" width="100" />
          </button>
        </li>
      </ul>
    </div>
    <slot :factId="currentManuFactID"></slot>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'Manufacturer',
  data: () => ({
    currentManuFactID: 0,
    manufacturer: [
      { id: 1, Title: 'Asus' },
      { id: 2, Title: 'Dell' },
    ],
  }),
  created() {
    this.getManufacturer();
  },
  methods: {
    async getManufacturer() {
      const res = await axios.get('https://demo.yume-dev.me/manufacturers');
      this.manufacturer = res.data;
    },
    changeManufacturerId(mid) {
      this.currentManuFactID = mid;
    },
  },
};
</script>
