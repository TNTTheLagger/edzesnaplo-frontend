<template>
  <div class="app-container">
    <div class="container py-5">
      <div class="row">
        <div class="col-md-6">
          <UjGyakorlat @ujGyakorlat="rogzitGyakorlat" />
        </div>
        <div class="col-md-6">
          <Listaz :gyakorlatok="gyakorlatok" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import UjGyakorlat from './components/UjGyakorlat.vue';
import Listaz from './components/Listaz.vue';
import { API_HOST } from './config';

export default {
  components: { UjGyakorlat, Listaz },
  data() {
    return {
      gyakorlatok: []
    };
  },
  methods: {
    async rogzitGyakorlat(gyakorlat) {
      try {
        const response = await fetch(API_HOST, {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify(gyakorlat),
        });

        const data = await response.json();
        alert(data.message);
        this.fetchData();
      } catch (error) {
        console.error('Hiba történt:', error);
      }
    },
    async fetchData() {
      try {
        const response = await fetch(API_HOST);
        this.gyakorlatok = await response.json();
      } catch (error) {
        console.error('Hiba történt az adatok lekérésekor:', error);
      }
    }
  },
  created() {
    this.fetchData();
  }
};
</script>

<style scoped>
.app-container {
  background: url('@/assets/background.png');
  background-size: auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
