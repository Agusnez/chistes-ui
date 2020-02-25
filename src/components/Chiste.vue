<template>
  <div>
    <div
      class="border m-6 rounded-lg bg-white mx-auto max-w-sm shadow-lg rounded-lg overflow-hidden"
    >
      <div class="sm:flex sm:items-center px-6 py-4">
        <div class="sm:text-left sm:flex-grow">
          <div class="mb-4">
            <p class="text-md leading-tight text-grey-dark">{{this.texto}}</p>
          </div>
          <div class="text-right">
            <button
              class="pl-2 pr-2 mr-2"
            >Editar</button>
            <button
              class="btn-danger pr-2 pl-2"
              @click="removeChiste"
            >Borrar</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: "Chiste",
  props: {
    id: Number,
    texto: String
  },
  methods: {
    removeChiste() {
      axios.delete(`${process.env.VUE_APP_API_HOST}api/v1/chistes/${this.id}`).then(()=>{
        location.reload();
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
