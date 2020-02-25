<template>
  <div v-if="this.opened" class="modal-component container absolute top-0 z-50 items-center">
    <div class="flex bg-gray-200 text-center">
      <h1>Modal</h1>
    </div>
  </div>
</template>

<script>
import { EventBus } from "../event-bus.js";

export default {
  data() {
    return {
      opened: false
    };
  },
  created() {
    EventBus.$on("openModal", () => {
      this.opened = !this.opened;
      document.body.className = "opened-modal";
    });
  }
};
</script>

<style>
.opened-modal {
  overflow: hidden;
}

.modal-component {
  width: 100vw;
  height: 100vh;
  background-color: azure;
}
</style>