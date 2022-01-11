<template>
  <div class="container">
    <manufacturer v-slot="data">
      <devices :manufacturerID="data.factId"></devices>
    </manufacturer>
  </div>
</template>
<script>
import Manufacturer from '../components/Manufacturer.vue';
import Devices from '../components/Devices.vue';
export default {
  name: 'main',
  components: {
    Manufacturer: Manufacturer,
    Devices: Devices,
  },
};
</script>
