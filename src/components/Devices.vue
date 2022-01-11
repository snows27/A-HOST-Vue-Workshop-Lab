<template>
  <span class="font-black mb-3">Devices
  <div class="grid grid-cols-3 gap-4 border border-black ml-0 mr-5 p-3">
    <ul v-for="device in devices" :key="device.id">
      <li>
      <router-link :to="{name: 'detail', params: {id: device.id}}">
        <img :src="device.Photo" />
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'Devices',
  props: {
    manufacturerID: Number,
  },
  data: () => ({
    devices: [
      { id: 1, DeviceName: 'Asus ROG' },
      { id: 2, DeviceName: 'Dell XP13' },
    ],
  }),
  watch: {
    manufacturerID: function (newId, oldId) {
      console.log('new Id: ', newId, ' | was: ', oldId);
      this.validateId(newId);
    },
  },
  created() {
    this.validateId(0);
  },
  methods: {
    async getDevices(uri) {
      const res = await axios.get(uri);
      this.devices = res.data;
    },
    validateId(id) {
      let URI = 'https://demo.yume-dev.me/devices';
      if (this.manufacturerID != 0 || this.manufacturerID) {
        URI = `${URI}?ManufacturerID=${this.manufacturerID}`;
        console.log('URI ::: ', URI);
        this.getDevices(URI);
      } else {
        this.getDevices(URI);
      }
      this.getDevices(URI);
    },
  },
};
</script>
