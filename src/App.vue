<template>
  <div id="app container">
    <h1 class="text-6xl text-center">Chistes</h1>
    <div class="mx-auto max-w-sm text-right p-1 mt-6">
    <button class="btn-success p-2" @click="addChiste">Añadir chiste</button>
    </div>
    <div class="container p-2">
      <chiste v-for="chiste in chistes" :key=chiste.id :id="chiste.id" :texto="chiste.texto"></chiste>
    </div>
    <chiste-modal />
  </div>
</template>

<script>
import Chiste from './components/Chiste.vue';
import ChisteModal from './components/ChisteModal.vue';
import axios from 'axios';
import { EventBus } from './event-bus.js';

export default {
  name: 'App',
  components: {
    Chiste,
    ChisteModal
  },
  data() {
    return {
      chistes: []
    }
  },
  mounted() {
    axios.get(`${process.env.VUE_APP_API_HOST}api/v1/chistes`).then((response)=>{
      this.chistes = response.data;
    });
  },
  methods: {
    addChiste() {
      EventBus.$emit('openModal', null);
    }
  }
}
</script>

<style>
</style>
