<template>
    <div class="card">
      <div class="card-body">
        <h5 class="card-title text-center">Új gyakorlat rögzítése</h5>
        <div class="mb-3">
          <label for="gyakorlat" class="form-label">Elvégzett gyakorlat</label>
          <input
            id="gyakorlat"
            type="text"
            class="form-control"
            v-model="bejegyzes.gyakorlat"
          />
        </div>
        <div class="mb-3">
          <label for="ismetles" class="form-label">Sorozatszám</label>
          <input
            id="ismetles"
            type="number"
            class="form-control"
            v-model="bejegyzes.ismetlesszam"
            min="1"
            max="8"
          />
        </div>
        <button class="btn btn-primary w-100" @click="rogzit">Rögzít</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        bejegyzes: { gyakorlat: "", ismetlesszam: 6 }
      };
    },
    methods: {
      rogzit() {
        this.$emit('ujGyakorlat', this.bejegyzes);
      }
    }
  };
  </script>

<style scoped>
    .card{
        backdrop-filter: blur(10px);
        padding: 20px;
        border: 2px solid;
        border-radius: 10px;
    }
</style>
  