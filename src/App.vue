<template>
  <section class="main-app">
    <Header />
    <ResourcesMenu @toggle-component="toggleComponent" />
    <component :is="selectedComponent"></component>
  </section>
</template>

<script>
import Header from './components/Header'
import ResourcesMenu from './components/ResourcesMenu.vue'
import Resources from './components/Resources.vue'
import Form from './components/Form.vue'

export default {
  components: {
    Header,
    ResourcesMenu,
    Resources,
    Form
  },
  data() {
    return {
      resources: [
        {
          id: 1,
          title: 'Official Vue Guide',
          description: 'The official Vue.js documentation',
          link: 'https://vuejs.org/'
        },
        {
          id: 2,
          title: 'Google',
          description: 'Learn to google...',
          link: 'https://google.org/'
        }
      ],
      selectedComponent: 'Resources'
    }
  },
  methods: {
    toggleComponent(component) {
      this.selectedComponent = component
    }
  },
  provide() {
    return {
      resources: this.resources
    }
  }
}
</script>

<style>
* {
  margin: 0;
}

#app {
  font-family: 'Roboto', sans-serif;
}

.main-app {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
  width: 100vw;
}
</style>