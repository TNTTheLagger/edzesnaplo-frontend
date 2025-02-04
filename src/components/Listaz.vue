<template>
    <div class="card">
      <div class="card-body">
        <h5 class="card-title text-center">Elvégzett gyakorlatok</h5>
        <ul class="list-group">
          <li
            v-for="gyakorlat in gyakorlatok"
            :key="gyakorlat.id"
            class="list-group-item"
            :class="{ 'text-danger': gyakorlat.ismetlesszam > 6 }"
          >
            {{ gyakorlat.created_at }} - {{ gyakorlat.gyakorlat }} ({{ gyakorlat.ismetlesszam }} ismétlés)
          </li>
        </ul>
        <p class="mt-3 text-center" v-if="!gyakorlatok.length">
          Nincs rögzített gyakorlat
        </p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ['gyakorlatok']
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