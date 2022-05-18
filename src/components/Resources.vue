<template>
  <section class="resource-cards-container">
    <section class="resource-card" v-for="resource in resources" :key="resource.id">
      <section class="card-header">
        <h2>{{ resource.title }}</h2>
        <button @click="deleteResource(resource.id)">Delete</button>
      </section>
      <br>
      <p>{{ resource.description }}</p>
      <a :href="resource.link">View Resource</a>
    </section>
  </section>
</template>

<script>
export default {
  inject: ['resources', 'deleteResource']
}
</script>

<style scoped>
.resource-cards-container {
  margin-top: 5vh;
  width: 41%;
}

.resource-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin: 0;
  min-height: 12vh;
  padding: 15px;
  margin-bottom: 3vh;
  border-radius: 10px;
  box-shadow: 0.5px 1px 5px 1px grey;
}

.card-header {
  display: flex;
  justify-content: space-between;
}

button {
  background: none;
  border: none;
  color: #3a0061;
}

a {
  text-decoration: none;
  color: #ce5c00;
  margin-top: 1vh;
}

a:hover {
  color: #eda36a
}
</style>