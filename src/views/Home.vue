<template>
  <div>
    <button @click="setupBluetooth">setup</button>
  </div>
</template>

<script>
export default {
  name: "Home",
  methods: {
    async setupBluetooth() {
      if (!("bluetooth" in navigator)) return;
      const { bluetooth } = navigator;
      console.log(bluetooth);
      const availability = await bluetooth.getAvailability();
      if (availability === false) return;

      const device = await bluetooth.requestDevice({
        acceptAllDevices: true
      });
      console.log(device.name);

      const devices = await bluetooth.getDevices();
      console.log(devices);
    }
  }
};
</script>
