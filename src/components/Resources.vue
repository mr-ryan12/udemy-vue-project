<template>
  <section class="resource-cards-container">
    <section class="resource-card" v-for="resource in resources" :key="resource.id">
      <!-- <h2>{{ resource.title }}</h2>
      <br>
      <p>{{ resource.description }}</p>
      <a :href="resource.link">View Resource</a> -->
      <h1>{{resource.title}}</h1>
    </section>
  </section>
</template>

<script>
export default {}
</script>

<style>
.resource-cards-container {
  margin-top: 5vh;
  height: 7vh;
  width: 40%;
  background-color: red;
}

.resource-card {
  height: 4vh;
  width: 30%;

}
</style>